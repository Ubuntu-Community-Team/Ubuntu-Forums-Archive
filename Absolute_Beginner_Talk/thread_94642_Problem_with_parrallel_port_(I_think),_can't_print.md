---
title: "Problem with parrallel port (I think), can't print !!"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by Moloko on 2005-11-24
Hi all, when I installed Ubuntu 5.10 (my first Linux installation :lol: ) I configured the printer (HP Laserjet 1100) without problems, in fact the printer was detected for the gnome-cups-manager, after I shared the printer with other computer running Win XP and everything was working fine.

But now I can't print, looking for a solution I tried this commands:

[B]$sudo aptitude install hpoj hpijs 
$ sudo ptal-init setup[/B]

When the detection of the devices conected to the parallel port starts there's an error:

****** ptal-mlcd failed to start!  Check syslog file for error messages.***

An finally, when I look in the syslog seems to be something wrong:

[B]localhost ptal-mlcd ERROR at ExMgr.cpp:2525, dev=<mlc:usb:probe>, pid=9984, e=1, t=1132858280         Couldn't find device! 

localhost ptal-mlcd FATAL ERROR at ParPort.cpp:48, dev=<mlc:par:probe>, pid=10027, e=1, t=1132858341         [COLOR="Red"]Access denied to parallel port![/COLOR][/B] 

If I start Win instead Linux in the same pc there isn't problems with the printer, any idea is wellcome ... thanks in advance.

---

### Post by my64 on 2005-11-30
I have a similar problem with my printer on parallel port.
The printer is recognized by the parport* modules, but as soon as I lauch an impression,  it is blocked and the printer starts blinking. Doign a "lpstat" gives  a "busy" message. 

I tried to disable interrupt when loading the parport  module, but it did not work also, got an error about the IO address (should be the basic 0x378).

Sorry to not help you, but maybe someone will help us.  

Olivier

---

### Post by chrisTGc on 2005-12-20
Hullo,

My HP printer is on the parallel port also but now have it working ok.

Did the following,
$ sudo aptitude install hpoj hpijs
$ sudo modprobe parport_pc
$ sudo /etc/init.d/hpoj setup
$ sudo modprobe parport_pc

Then system>administration>printing>add printer

It may be obvious to others but just in case.In hpoj setup be carefull to select parallel port and no to USB.The stock printer memory address in BIOS is 378,maybe worth checking that first.In add printer you need to select HP and printer model number.

Now when I print i note the HP printer is in the dialogue and can be selected.The problem seems to have been around the parallel port not being found which is what modeprobe parport does,no output after that command is good.So thanks to others esp Moloko for the hpoj and hpijs bit.

Best wishes Chris.

---

### Post by sitara on 2005-12-23
I am having the same problem with HPOJ, although I am able to print OK - I just can't scan, which is why I am trying to run HPOJ. I have tried the modprobe command suggested in this thread, which returns with no output, but it doesn't make any difference - I get the same error in the syslog: '23/12/2005 12:36:52 localhost ptal-mlcd FATAL ERROR at ParPort.cpp:48, dev=<mlc:par:probe>, pid=7745, e=1, t=1135334212 Access denied to parallel port! '. I posted this problem previously but got no response. I would really appreciate some help cos I need the scanner to work. I know it is possible, because I have had it working in other Linuces previously.

---

### Post by chrisTGc on 2005-12-25
Hullo Sitara,

Ime no Linux expert but ive wondered wether you have tried the following;

click on;
Applications>Graphics>XSane Image scanning

If I do that i get 'no device' which is correct for this machine.What do you get ?.

Also you dont say here the make/model of your scanner and wether it is an all in one with the printer.If it is an all in one i would first try;

click on;
System>Administration>Printing

If i do that i can see a link to add a 'new printer' also 'Deskjet 3820 is ready'.What do you get ?.

Best Wishes and Happy Christmas all Chris.

---

### Post by www.rzr.online.fr on 2006-05-06
[QUOTE=my64]I have a similar problem with my printer on parallel port.
The printer is recognized by the parport* modules, but as soon as I lauch an impression,  it is blocked and the printer starts blinking. Doign a "lpstat" gives  a "busy" message. 

I tried to disable interrupt when loading the parport  module, but it did not work also, got an error about the IO address (should be the basic 0x378).

[/QUOTE]

How did you get the error  code ?

---

### Post by openmind on 2006-05-06
Just wondering if this would help;

[http://www.ubuntuforums.org/showthread.php?t=164137]("http://www.ubuntuforums.org/showthread.php?t=164137")

---

### Post by www.rzr.online.fr on 2006-05-08
I managed to get it  working again but I think there is a bug in the gnome frontend of cups ...

---

