---
title: "Completly new to linux, need wireless help"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by ffmurray on 2007-09-14
I am completly new to running linux, as in i installed it yesterday.  I have a toshiba satalitte m105-s1021 and am running ubuntu 6.10 and windows xp on it.  I can not figure out how to get the drivers for my wireless to work in linux.  i think the wireless is an atheros chipset.  i found Madwifi and downloaded it on my other computer and unpacked it from a usb drive onto my laptop.  i keep opening a terminal and trying to follow the steps to unpack it and istall it but i can not get anything to work, i keep getting all kinds of error messages.  The madwifi site says something about opening a shell termila inside the folder, and i have played around for a while and cant find out how to do that.  any help on installing drivers or tarballs or anything would be greatly apreciated

---

### Post by overdrank on 2007-09-14
> **ffmurray said:**
> I am completly new to running linux, as in i installed it yesterday.  I have a toshiba satalitte m105-s1021 and am running ubuntu 6.10 and windows xp on it.  I can not figure out how to get the drivers for my wireless to work in linux.  i think the wireless is an atheros chipset.  i found Madwifi and downloaded it on my other computer and unpacked it from a usb drive onto my laptop.  i keep opening a terminal and trying to follow the steps to unpack it and istall it but i can not get anything to work, i keep getting all kinds of error messages.  The madwifi site says something about opening a shell termila inside the folder, and i have played around for a while and cant find out how to do that.  any help on installing drivers or tarballs or anything would be greatly apreciated

Hi if you could tell us the info on the card we can help better. In the terminal use the command ```
lspci
``` and post the output here. Also you may need to install build essential to install the drivers also.

---

### Post by jamvegan on 2007-09-14
Hi, welcome to GNU/Linux and Ubuntu!

If you haven't done so already, you may wish to look at Ubuntu's [documentation]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless") regarding wireless.  I don't have any experience, myself, with the Atheros chipset.  I have a Broadcom wireless card, and had to go with the ndiswrapper option mentioned in the documentation.

To answer some of your questions regarding madwifi, if you do determine that that's what you need:

You use the "cd" command to get around in the terminal.  So, if the directory you need to get to were called "madwifi", and it was on your desktop, you would get to it from your home directory (which is where you start out when you open a terminal) by typing:
```
cd Desktop/madwifi
```
Note that in Linux, unlike Windows, capitalization matters, so type all directory and file names exactly as they appear.

Your instructions may tell you to su to root.  We don't do that in Ubuntu.  Instead, we use sudo to give ourselves root privileges.  If you are supposed to su to root and then run some commands, you will instead type "sudo" before each of the commands.  So, if the instructions said to type:
```
tar xvzf madwifi
```
then instead you would type:
```
sudo tar xvzf madwifi
```
When you use sudo, you will be prompted for your password (the same one that you use to log in), but if you issue several sudo commands in a short period of time, you will only be prompted for your password the first time.

Good luck!  I hope this helps. :-)

---

