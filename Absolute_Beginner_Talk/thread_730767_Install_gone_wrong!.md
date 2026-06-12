---
title: "Install gone wrong!"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by JNMann on 2008-03-21
I'm still reading all the help files so please forgive me for being impatient and posting this!

Having tested the CD boot Ubuntu and being blown away I thought I have a go at the install.

I used the install button from the Ubuntu desktop and all seemed to go well.  Got a bit confused over the drive setup as I have several and took a while to work out which was which.  Eventually settled on installing on a clean drive.

Rebooted after instal and all I get is a blank screen, no XP, no Ubuntu!  Hopefully I havn't messed my Xp install up but not that bothered if I have.

Should I re-install everything?  Really need to have duel boot on 2 seperate sata drives.  Xp is on a 2 drive raid.

Appreciate any advise please.....go easy I'm new to these 'better' OS's!

Cheers,
Justin

---

### Post by Jimmyfj on 2008-03-21
You can just install the lot once more I think - But plz remember to defrag your Windows partition before installing Ubuntu. And make sure to let the installer chose the drive for you during install. Simply accept the installers suggestion on resizing your existing partition.

For your own sake make sure that you have only one drive attached to your computer during install and do not fool around with Gparted unless you know what you're doing. Just plug in the other drives you got after install and take it from there.

---

### Post by JNMann on 2008-03-21
Many thanks for the reply Jimmy.

So, I plug in my 2 drive raid (only) and install WinXP.  Then I plug in my next drive and using the installer it will choose this drive as it will have (slightly) more free space?  Can i then simply dual boot ?

Justin

---

### Post by philinux on 2008-03-21
> **JNMann said:**
> 
Rebooted after instal and all I get is a blank screen, no XP, no Ubuntu!  Hopefully I havn't messed my Xp install up but not that bothered if I have.



Hopefully XP is still there just not accessible at the moment. You might not have to reinstall just yet.

When you boot up do you get any messages like this before the blank screen?

grub stage 1.5

then

grub loading

---

### Post by bumanie on 2008-03-21
Hmm, this is a bit hard to answer seeing you can't boot into either OS, but it is obvious that something has gone wrong. I fear you may have mucked up xp. Before you go to a complete reinstall of both OSes, you could try to fix the mbr of xp and see if you can boot it. If it is only the mbr that has mucked up and the rest of the system is OK, this will save you a lot of work and will also mean that your saved data should still be in tact. As long as you did not format the xp drive/partition, your data should be OK.
Put xp disc in drive, start computer and go to recovery console. In recovery console choose the OS you want to fix (usually 1), type in administrator password --> enter. Then type fixboot --> enter
fixmbr --> enter
exit -->enter
Try to reboot. If you can't reboot, it is likely that xp is beyond saving and you will have to do a complete reinstall. If it does boot, post back and someone can help you with how to install ubuntu if you wish. 
Also you could try gparted live cd and see if all the drive partitions are still intact and also see how much space is used. You can guage whether all the information is there or not or whether it has been wiped.

---

### Post by JNMann on 2008-03-21
Thanks again for the input guys.  Not sure if any message came up b4 it went blank, I'm at work now so will check later today and post back.  tried the fixmbr but still doesn't boot...will try again following your instructions.

Will post back later, if I have to install XP again it's not the end of the world but always nicer not to have to!

Cheers,
Justin

---

### Post by JNMann on 2008-03-21
OK....fixmbr etc. didn't work so reinstalled WinXP.  Disconnected drives containing XP, connected different drive.  Installed Ubunto onto this drive and boots perfectly.  Plugged other drives back in and rebooted again but cannot choose XP or Ubunto....any ideas guys?

Think we're getting there ;-)

Many thanks,
Justin

---

### Post by spiderbatdad on 2008-03-21
Maybe bypassing the grub menu due to the method you used. Try pressing esc after bios screen to bring up grub menu. If this works you can edit /boot/grub/menu.lst to comment out "hidden menu"

---

### Post by JNMann on 2008-03-21
OK, disconnected Ubunto drive, XP boots fine.  Reconnected Ubunto drive, boots straight into XP, how can I get it to dual boot from here?

Justin

---

### Post by JNMann on 2008-03-21
Oh dear oh dear.....Disconnected XP drive, reconnected Ubuntu drive, wont boot!  What on earth am I doing wrong!  Is there a better way to install?  I just thought giving it it's own drive would be better...please help!

:-(

---

### Post by Nikhil Gohil on 2008-03-21
is there any message when you connecty only the ubuntu drive?

---

### Post by JNMann on 2008-03-21
Oh so strange......now it's booting into Ubunto again!  Can't explain that but it boots!

It booted into low graphics mode asked me for login name and password then seems to hang on brown screen with arrow which I can move around with mouse.

---

