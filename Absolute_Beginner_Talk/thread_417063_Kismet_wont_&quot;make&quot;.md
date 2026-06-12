---
title: "Kismet wont &quot;make&quot;"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by stuck on 2007-04-21
Ubuntu.

ATHEROS,Atheros 5006EG wireless network adapter

Latest madwifi-ng installed (madwifi-ng-r2279-20070417)

I downloaded kismet-2007-01-R1b.tar.tar, and extracted it to my home folder.

Then I run ./configure, it seemed ok unil the end. Then this:

[INDENT]checking for initscr in -lcurses... no[/INDENT]
[INDENT]configure: error: Unable to find libncurses or libcurses[/INDENT]

Then I tried:

mark@mark-laptop:~/kismet-2007-01-R1b$ make
make: *** No targets specified and no makefile found.  Stop.

This is a fresh intall of Ubuntu, this is my first outing using it and so far it has been very difficult and un-user friendly, this is my second install after killing it trying to install my wireless card. I dont understand the command line/terminal stuff so back to very basics if you can help.

Please help a newbie.

---

### Post by madmetal on 2007-04-21
try to read this about how to install things in ubuntu 
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by Campingman on 2007-04-21
Kismet 2006.04.R1.1 is in synaptic if that is any help, system/administration/synaptin package manager.  Do not know much about wireless so apologies if this is no good.

---

### Post by stuck on 2007-04-22
Thank you very much for the link Madmonkey.

Just skimmed through it, looks like just the document I need.

---

### Post by ttakun on 2007-04-23
Maybe you have solved the problem yet, but I had the same problem a few days ago trying to install kismet from scratch. Lots of problems installing all the things it needed (libpcap, plex, ...)
In the end, I installed kismet from the repos (version 2006.04.R1) and later I installed the last version from Kismet's web:

sudo su
sudo aptitude install build-essential
wget [http://www.kismetwireless.net/code/kismet-01-R1b.tar.gz](http://www.kismetwireless.net/code/kismet-01-R1b.tar.gz)
tar xf kismet-2007-01-R1b.tar.gz
cd kismet-2007-01-R1b
./configure
make dep
make
make install

Don't forget to change your kismet.conf file. ;-)

---

### Post by stuck on 2007-04-23
When I clicked link above got the error:

[INDENT][INDENT][INDENT]error 404

page not found
[/INDENT][/INDENT][/INDENT]

I get this error alot when using links, I read through the "how to install" guide but did nothing at all to help with kismet.

---

### Post by ttakun on 2007-04-23
You don't need to click on the above link at all.
I suppose you have the previous version of kismet installed from the repos through Synaptic.
Then open a terminal window, and type all the lines I gave you before.
Before typing them, start with a "cd" command to go your /home directory, and then type them. After typing the "wget" command to download the tar file, if you get a 404 error, just try it again. I have tried it now, and the first time it gave me a 404 error (no clue why it happened), but second time I ran "wget" command, it downloaded the file succesfully.
If you have any more problems with the configure and make commands, just post the output.

---

### Post by orphzirra on 2007-04-23
Open System -> Administration -> Synaptic Package Manger

Search for libncurses and install the libncurses5-dev package.  Also, install libncurses5 if it isn't already installed (box next to it is green).

You'll find that in order to compile most things you'll need the -dev package.

---

### Post by stuck on 2007-04-25
Thanks very much for the help.

ive now managed to connect to net so no longer need Kismet.

I think ive installed it using :     Open System -> Administration -> Synaptic Package Manger

Thanks again for the assistance.

---

