---
title: "ubuntu 8.04 rc on a macbook, problem with instalation"
date: 2008-04-22
forum: Apple Hardware Users
---

### Post by yousufinternet on 2008-04-22
hi every body :guitar:
i have tried today to install ubuntu 8.04 rc on my macbook 
every thing goes ok with the installer 
but the problem appears after restarting and booting into ubuntu 
it gives me an error : 
**no bootable hard disk **
or something like this
my partition table is like this:
209 mg for efi
60 gb for mac osx
13 gb for ubuntu 8.04 "/" the root directory
2 gb swap 
so what i have done wrong? :confused:
please help!!!
thanks in advance

---

### Post by JediPottsy on 2008-04-22
how are you booting to Ubuntu? Also how did you install ubuntu?

I have a MBP rev2 and installs fine with 8.04 X64 RC Alternative Install.

neway

in OSX download and install rEFIt. Its a boot manager. Reboot and dont hold alt or c or d or anything. Let rEFIt install, and choose Partitioning tool. It will run and ask to update the MBR
choose "y"

this will rewrite the drives MBR allowing grub to boot. Will also allow you to use fglrx or nv drivers and enable glx (glx requires BIOS functions and requires mbr to be enabled)

hope this helps

---

### Post by mabovo on 2008-04-22
> **JediPottsy said:**
> how are you booting to Ubuntu? Also how did you install ubuntu?

I have a MBP rev2 and installs fine with 8.04 X64 RC Alternative Install.

neway

in OSX download and install rEFIt. Its a boot manager. Reboot and dont hold alt or c or d or anything. Let rEFIt install, and choose Partitioning tool. It will run and ask to update the MBR
choose "y"

this will rewrite the drives MBR allowing grub to boot. Will also allow you to use fglrx or nv drivers and enable glx (glx requires BIOS functions and requires mbr to be enabled)

hope this helps

I have installed holding "c" no problem but rEFIt works nice too.

---

### Post by cyberdork33 on 2008-04-22
> **mabovo said:**
> I have installed holding "c" no problem but rEFIt works nice too.
you need refit to use gptsync

---

### Post by yousufinternet on 2008-04-23
i have refit already 
i will try the steps u wrote and tell you the result 
thanks very much

---

### Post by yousufinternet on 2008-04-23
ok i have updated mbr 
but now when i boot into linux from refit the tux image shows and freeze 
i have waited a lot but it didn't changed ! 
so what is wrong now?? 
thanks in advance

---

### Post by cyberdork33 on 2008-04-23
> **yousufinternet said:**
> ok i have updated mbr 
but now when i boot into linux from refit the tux image shows and freeze 
i have waited a lot but it didn't changed ! 
so what is wrong now?? 
thanks in advance
good question, but it sounds like an issue with refit since you never make it off the refit splash page.

---

### Post by yousufinternet on 2008-04-23
thanks every one 
i am writing now from ubuntu 8.04 rc 
and every thing works fine except isight of course 
the trick was
1- update mbr.
2- shutdown the computer.
3- turn it on and boot into mac osx.
4- restart and enjoy linux!! 

:)

---

### Post by cyberdork33 on 2008-04-23
> **yousufinternet said:**
> i am writing now from ubuntu 8.04 rc 
and every thing works fine except isight of course 

To get iSight working in Hardy, you need iSight-Firmware-Tools:

[http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

---

### Post by yousufinternet on 2008-04-23
i have tried this
it installed currectly 
but when i try in gstreamer-properties 
it gives me this error: 
Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

please notice that i haven't restarted the system 
i have just restarted hal

---

### Post by cyberdork33 on 2008-04-23
> **yousufinternet said:**
> i have tried this
it installed currectly 
but when i try in gstreamer-properties 
it gives me this error: 
Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

please notice that i haven't restarted the system 
i have just restarted hal
I would restart completely just to be sure, but restarting hal should do it too. Also, make sure the firmware shows up in /lib/firmware/

---

### Post by yousufinternet on 2008-04-24
it works after a full restart 
thanks very much :):):):popcorn:

---

### Post by mathew.chacko on 2008-04-24
I have similar problem with final 8.04 on Macbook 3,1
After rEFIt screen, cannot start Ubuntu. The message says "No bootable device -- insert boot disk and press any key"

I had no problem with Beta version. Some thing is really wrong. I followed the instruction. Applied Mac updates, EFI firmware update, even new eEFIt 0.11. But no success getting into Ubuntu even after several restart.


Any help... Thanks in advance...

---

### Post by cyberdork33 on 2008-04-24
> **mathew.chacko said:**
> I have similar problem with final 8.04 on Macbook 3,1
After rEFIt screen, cannot start Ubuntu. The message says "No bootable device -- insert boot disk and press any key"

I had no problem with Beta version. Some thing is really wrong. I followed the instruction. Applied Mac updates, EFI firmware update, even new eEFIt 0.11. But no success getting into Ubuntu even after several restart.


Any help... Thanks in advance...you need to select the partitioning tool in refit to sync the partitions.

---

### Post by billbear on 2008-04-25
The reason is that the hybrid GPT/MBR partition table confuses ubuntu installer.
Gusty installer decides to use the GPT and leave the MBR table untouched.
But Hardy installer decides to erase the MBR table completely and turn the disk to GPT only. This is bad because grub still needs an MBR partition table. And if there are still other "legacy" OSes on the disk like XP, vista, they will also become unbootable.
I encountered this problem yesterday, I was quad-booting OS X/XP/vista/ubuntu, and after installing Hardy, i can only boot into OS X. i ran fdisk /dev/rdisk0 and found the MBR table was gone. I rebuilt the MBR table manually in terminal. ( i forgot that i can use the refit tool to sync tables) Then i can boot all the OSes but vista said it needs to be repaired.

---

### Post by mathew.chacko on 2008-04-25
Thanks for the solution and explanation. Got fixed. I am super happy. Hoory!

---

