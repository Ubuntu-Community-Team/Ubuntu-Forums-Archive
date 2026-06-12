---
title: "Errors with updating to ubuntustudio!!"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-05-23
Hello,

I wanted to update to ubuntu studio. So I ran these two commands:

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

after which I clicked everything which I found with ubuntustudio in synaptic. It then started downloading and installing untill I got the following error:

E: /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb: tried to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in the ardour-gtk package
(freely translated since the error was in Dutch..)

After installing I got the 'update-now' icon (orange thing with the with star in it in the top left) which after I click it gets me another error which says (again freely translated from Dutch to English):

It is not possible now to install or remove software. Use the synaptic package manager or use  "sudo apt-get install -f" in a terminal window to resolve this problem. 

When I then run "sudo apt-get install -f" it gives me another one of those errors being (again freely translated):

dpkg: error with taking care of /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb (--unpack):
 Tried to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in the package ardour-gtk
dpkg-deb: subprocess paste was killed through the signal (Broke pipe)
Mistakes found while doing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anybody know how I can resolve this or what the problem is? I would love to start using some of the programs in Ubuntu studio! Especially Rosegarden! That Already appears in the programs menu, but when I click it it doesn't do anything.. :-(

---

### Post by Jussi01 on 2007-05-23
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=445077](http://ubuntuforums.org/showthread.php?t=445077)

I think youll find the answer there :D

Cheers

Jussi

---

### Post by kramer65 on 2007-05-23
Thank you!

That works now. But one more question, as far as I understand I need to start JACK Control in order to start any of the other applications..?

When I start JACK it needs to start running automatically I think. But it does not, so I click the play button, then it gives some kind of error saying: Could not connect to JACK server as a client. with some error window saying:

11:59:04.407 Patchbay deactivated.
11:59:04.431 Statistics reset.
11:59:04.471 MIDI connection graph change.
11:59:04.644 MIDI connection change.
11:59:05.851 Startup script...
11:59:05.852 artsshell -q terminate
Error: "/home/ricam/.kde/socket-ricam-desktop" is not a link or a directory.
Error: "/home/ricam/.kde/socket-ricam-desktop" is not a link or a directory.
Error: "/home/ricam/.kde/socket-ricam-desktop" is not a link or a directory.
(The previous message was repeated 1 times.)
can't create mcop directory
11:59:06.109 Startup script terminated with exit status=256.
11:59:06.109 JACK is starting...
11:59:06.109 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
11:59:06.111 JACK was started with PID=11485 (0x2cdd).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
11:59:06.132 JACK was stopped successfully.
11:59:06.132 Post-shutdown script...
11:59:06.132 killall jackd
jackd: er is geen proces afgebroken
11:59:06.344 Post-shutdown script terminated with exit status=256.
11:59:08.268 Could not connect to JACK server as client. Please check the messages window for more info.


What does this tell me? Do I need to configure something? and if so.. What :?:  Anybody??

---

