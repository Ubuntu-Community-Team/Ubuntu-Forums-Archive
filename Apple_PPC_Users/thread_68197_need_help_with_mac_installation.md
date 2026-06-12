---
title: "need help with mac installation"
date: 2005-09-22
forum: Apple PPC Users
---

### Post by grimdaze on 2005-09-22
i installed ubuntu on a power pc g3 
the install seemed to work fine but when i run it
it says failed to load graphical interface
so now it's like all text 
how to i fix this

-----total noob with linux btw so please be specific

---

### Post by RHTopics on 2005-09-22
There is a file named Xorg.0.log located in /var/log subdirectory that logs your computer's attempt to start X Window.

If you can post that file back as a reply, I may be able to help you.

Also, can you provide a more specific description of your computer including the model type.

---

### Post by grimdaze on 2005-09-22
well it's actually my step fathers mac i was trying to help him install it
and i cant get the model info atm cuz i'm at work and i won't beable to post that info until tomorrow because my internet service at home is temporaly off

as far as the Xorg.0.log
i'm really noobish with linux so i don't know how to retrieve that info for you
if you could ellaborate i'd appreciate

---

### Post by grimdaze on 2005-09-22
" I cannot start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem? "


thats what pops up when i boot up tho

---

### Post by RHTopics on 2005-09-22
The Xorg.0.log file should contain the same information as what your probably seeing on the screen when you try to start the X server.

First, just to make sure the Xorg.0.log is there, do the following command from the command line:

    less /var/log/Xorg.0.log

This command allows you to browse through the file using the return key or the space bar.  Press the "q" to quit and go back to the command line.

Next, if you have a USB flash drive or some other portable storage device that could used for transferring a copy of this file on to the computer you are using for Internet access, and then post it here.

When a USB flash drive (Lexar Jump Drive) is plugged into my iMac, it shows up as device named LEXAR in the /media directory.

If you have a USB flash drive plugged in, do the following commands from the command line to list the device names and then copy the file to the USB flash drive:

    ls /media
    cp /var/log/Xorg.0.log /media/"put USB device name here"/Xorg.0.log

If doing the above is not possible, then go ahead post the Xserver output the best way you can.

---

### Post by grimdaze on 2005-09-22
can't i just copy it all to a floppy?

---

### Post by grimdaze on 2005-09-22
no i forgot there's no floppy drive on there just a cdrom and zip

---

### Post by patrickp on 2005-09-22
hi,

why don´t u tell us which graphical card u have in the mac

then u got to 
/etc/X11
there u do
nano xorg.conf

and in the section device u change the 
driver "drivername"

then u do a ctrl o
to save config

ant then ctrl x
to exit

then do 
/etc/init.d/gdm restart 

this should work

good luck

if u dont know the exact driver post your card and i will help u to find the right one

if u don`t know how simply type

lspci and give me the output

---

### Post by God of the Meeps on 2007-11-10
When I was installing 7.04 (on a live cd), when it goes to the screen where it asks you to select the operating system, select 'Safe Graphics Mode' instead of the default. Thats what worked for me (unless of course, you want a dual boot).

---

