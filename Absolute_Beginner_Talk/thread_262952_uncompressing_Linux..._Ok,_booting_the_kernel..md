---
title: "uncompressing Linux... Ok, booting the kernel."
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by shookone30 on 2006-09-22
OK, I am new to Linux and so far I am enjoying it but man am I frustrated as I have been unsuccessful at booting up Dapper Drake Server on my laptop (HP nc6000) with a Pentium M 1.4Ghz

The live desktop cd boots fine and runs perfectly but after installing the server which goes find and installation completes and the pc restarts I get past grub and then the machine freezes at "Uncompressing Linux... Ok, booting the kernel." I have looked for help else where on the forums but a lot of this same problem has to deal with windows users running vm ware and receiving this issue.

So far my forum research has led me to try the following tactics all of which have been unsuccesful:

1. Disabling USB Legacy Support
2. Changing the boot priority of the cd-rom to after hard drive
3. Re-Installing Dapper Drake again
4. Using Grub to edit Kernel and entering acpi=off (not sure if done correctly, like i said i'm newbie)

If anyone has any other suggestions for me it would be greatly appreciated.

Thanks in advance

---

### Post by christhemonkey on 2006-09-22
I have found, that when booting up:
If a usb device, like a flashdisk/usbstick is inserted, it stops at this stage.

---

### Post by xpod on 2006-09-22
You might be better trying the "alternate cd" ,mate.It`s a "text" installer and dont use all the resources the live cd does and thats good if you aint got a lot.i use it myself now.
It`s just as simple as the live cd but without the "gui".
Answer a few questions and off you go.
It is mabey easier to understand if you have the partition for Ubu already made but is just as simple to do from the cd

EDIT:sorry i misread that and thought you were stuck at getting the cd to run

---

### Post by shookone30 on 2006-09-22
No,not any USB stick or any USB devices attached at all and I'm having this problem.:-({|=

---

### Post by stiankarlsen on 2006-12-11
For me, the problem was my USB keyboard..

So basically, go into the bios and disable usb keyboard/mouse USB controller.

---

### Post by richyrichuk on 2007-05-14
thanks for that, it was USB on my system aswel, unplugged everything and it worked.....

---

### Post by firestorm_v1 on 2007-11-18
[http://ubuntuforums.org/showthread.php?p=3796999#post3796999](http://ubuntuforums.org/showthread.php?p=3796999#post3796999)

Had this same issue.  Try this and see if it works for you?  

I have run it in VMware server without issue, but this issue had me b0rked for a while.  None of the acpi=off, noapic or nolpic options worked for me.  I was about to say fsck it and go to RedHat 7.3 (i know it's old) but found this somewhere else.

---

