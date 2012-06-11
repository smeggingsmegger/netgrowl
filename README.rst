netgrowl.py
===========

This is a very simple script for sending Growl messages using Python to a Growl listener.

It has no dependancies except Python.  It has been tested with Python 2.6.*, 2.7.2

The original authors are listed within the file.

Usage
-----

Usage: ./netgrowl.py [-hs] [-H hostname] [-t title] [-d description] [-p priority] [-x password]

Send Growl messages over UDP

 * -h help 
 * -H specify host 
 * -t title
 * -d description
 * -p priority [-2 to 2]
 * -s make sticky
 * -x password


This script is supplied as is.

Setup
-----
On the Mac machine that will receive the growls:

- Growl PrefPane > Network:
 - Check "Listen for incoming notifications"
 - Check "Allow remote application registration"
 - Specify Server Password (and supply it in the code snippets you choose to use)
- You may need to restart Growl

Integration Snippets
--------------------

rc_gnotif
~~~~~~~~~
Contains a small bash function to quickly send a growl notification.

Simply add its contents to your .bashrc file::

  $ cat rc_gnotif >> ~/.bashrc
  $ source ~/.bashrc

  $ gnotif "Hello World" "Incoming Notification"
  $ long_running_command; gnotif "Finished long_running_command"

- The first parameter is the growl message description.
- The second is the title of the growl notification (defaults to "Remote Task Finished")


rc_growl_long
~~~~~~~~~~~~~
In conjunction with the included .preexec.bash script, you can growl only commands that take more than n seconds::

  $ cp .preexec.bash ~
  $ cat rc_growl_long >> ~/.bashrc
  $ source ~/.bashrc

There is also a customizable list of commands to exclude. You don't usually care to know that you quit vim or less.

See this thread for more information on the preexec script:
http://hints.macworld.com/article.php?story=20071009124425468

Of Note:
~~~~~~~~
Depending on the directory you clone this into, you may need to correct the path to netgrowl.py in the snippets
