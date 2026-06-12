---
title: "Installing Canon MP160 printer"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-09-17
I go [here,]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160") as I found when I searched these forums.  When I get to step 6 I get this.  I'm brand new to Ubuntu, and I need to print a paper for school tomorrow.  Please help.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libpng3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 936B of archives.
After unpacking 24.6kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe libpng3 1.2.15~beta5-1ubuntu1 [936B]
Fetched 936B in 0s (3032B/s) 
Selecting previously deselected package libpng3.
(Reading database ... 106014 files and directories currently installed.)
Unpacking libpng3 (from .../libpng3_1.2.15~beta5-1ubuntu1_all.deb) ...
Setting up libpng3 (1.2.15~beta5-1ubuntu1) ...
matt@mattspc:~$ sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
matt@mattspc:~$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
matt@mattspc:~$ cd /usr/share/cups/model;sudo lpadmin -p MP160 -P canonmp160.ppd -v cnij_usb:/dev/usb/lp0 -E
lpadmin: No such file or directory

---

### Post by waste301 on 2007-09-17
bump

---

### Post by waste301 on 2007-09-17
Bump

---

### Post by mikeyphi on 2007-09-17
Have you tried the suggestion on that printer page - use System/printing - 'new printer' and select MP150, see if the driver works on your system. If not - ask again.

---

### Post by mikeyphi on 2007-09-17
I think you might have a typo in your code:
matt@mattspc:~$ cd /usr/share/cups/model;sudo lpadmin -p MP160 -P canonmp160.ppd -v cnij_usb:/dev/usb/lp0 -E
lpadmin: No such file or directory

I think there is an unwanted / at usb/lp0 -E
It should read /dev/usblp0 -E

---

### Post by waste301 on 2007-09-17
Sorry for the long delay, I had to go to work for a few hours.

I tried altering the command as you suggested with no result.

However, progress has been made.

The printer appears under system-->printers

When I try to print, it appears in the jobs list under the correct printer.

However, the printer automatically pauses, and when I hit resume, it just goes back to saying:

paused: job-hold-until-specified

I feel like I'm close - please note anyone who reads this, I do not think Step 6 of the installation process woked correctly [here]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160").

All of the other steps - even the ones afterward seemed to work fine.

Also note: when I try to extract anything to /usr/share/cups/model its says I don't have permission.

---

### Post by waste301 on 2007-09-17
bump

---

### Post by waste301 on 2007-09-18
Hello, I've got a MP160 Canon printer, that I am trying to get to work with Ubuntu

The printer appears under system-->printers

When I try to print, it appears in the jobs list under the correct printer.

However, the printer automatically pauses, and when I hit resume, it just goes back to saying:

paused: job-hold-until-specified

I feel like I'm close - please note anyone who reads this, I do not think Step 6 of the installation process worked correctly [here.]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160")

All of the other steps - even the ones afterward seemed to work fine.

Also note: when I try to extract anything to /usr/share/cups/model its says I don't have permission.

---

### Post by callan79 on 2007-09-18
> **waste301 said:**
> Hello, I've got a MP160 Canon printer, that I am trying to get to work with Ubuntu


Hi There,

I don't have this printer (in fact, I don't have a printer at all) so I'm not really a lot of help, however I can tell you that I had similar problems setting up a Canon Pixma iP1300 at a relative's home.

The only way I got it working was with Turboprint - [www.turboprint.info](http://www.turboprint.info)

Perhaps get the Turboprint trial version and see how you go?

Cheers
Callan

---

### Post by SPRL on 2007-09-18
I have an MP130 and 450 and I have not been able to get them to work. I have read that most Canon printers and all in ones will not work in linux.

---

### Post by Daveth on 2007-09-18
if you do not have permission to paste into that folder then make yourself superuser for a short while i.e. used sudo in front of your command. 

Why do you think step 6 failed? Did you just cut and paste the command into a terminal or attempt to type it? It is a 3 tux printer as you will note so it should work, although a little complicated with those 4 rpms.

As of 14-Dec-2006, Turboprint have supported your printer. The low-medium quality outputs are free but the high quality driver functions are bannered until you buy the key. The reviews have been favourable- been toying with them for my HP to photo print.

---

### Post by stchman on 2007-09-18
> **waste301 said:**
> Hello, I've got a MP160 Canon printer, that I am trying to get to work with Ubuntu

The printer appears under system-->printers

When I try to print, it appears in the jobs list under the correct printer.

However, the printer automatically pauses, and when I hit resume, it just goes back to saying:

paused: job-hold-until-specified

I feel like I'm close - please note anyone who reads this, I do not think Step 6 of the installation process worked correctly [here.]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160")

All of the other steps - even the ones afterward seemed to work fine.

Also note: when I try to extract anything to /usr/share/cups/model its says I don't have permission.

According to [www.linuxprinting.org](www.linuxprinting.org) your printer works perfectly under Linux.

---

### Post by needspeed on 2007-09-22
HI,
I have a MP210 and temporarily failed....but have a look at this thread.

[http://ubuntuforums.org/showthread.php?t=556980](http://ubuntuforums.org/showthread.php?t=556980)

This person has a MP160 Working.

Needspeed

---

