---
title: "HOW TO - fixing the etc/resolv.conf file for internet access via dial-up in Kubuntu 7"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by its_toby on 2007-09-04
HI all,

I'n certain that there will be others who will need help with this problem so I thought I would share what I have learned all in one place.

when opening the KPPP to set up a dial-up internet account, if you get the error message 
**/etc/resolv.conf can not be found** 
or something of that nature it's probably missing (at least it was for me).  This file apparently was keeping me from connecting with my ISP.  I had to make a file in kwrite (you can use any text writer that you like) under root permisisons and then save it to the **root:/etc** directory (remember it's not the root  under your /home/[yourname]/etc directory) I thought it wouldn't matter but it did.

once you save it, open /etc and make sure that its there.  If it is, reboot.

once your back up and running reopen KPPP and you should be good to go.

remember when setting up your external modem to set your baut rate as close to your external modem's speed or it will probably connect at 9600

good luck!!

---

### Post by flutti-tutti on 2007-09-23
thanks for sharing your solution.

i am having the same problem besides a few others on Kppp and a dial-up modem.

my question to you is -- did you make a blank file of "etc/resolv.conf"?
Or, did you write something on it?
I am new to K/Ubunku and have tried to migrate from MS-Windows OS.
Thanks

---

### Post by Maestro23 on 2007-09-23
> **flutti-tutti said:**
> thanks for sharing your solution.

i am having the same problem besides a few others on Kppp and a dial-up modem.

my question to you is -- did you make a blank file of "etc/resolv.conf"?
Or, did you write something on it?
I am new to K/Ubunku and have tried to migrate from MS-Windows OS.
Thanks

To make a file, you can use the touch command.

> touch filename

In his case, the file was in /etc which is owned by root.  So it would be:

> sudo touch filename

*Don't know if he did it that way, but it is one way to create a new file via command line.

---

