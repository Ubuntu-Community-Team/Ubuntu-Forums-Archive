---
title: "No more daps for dapper..."
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Emceay on 2006-07-13
Just when I thought everything had fallen into place... #-o

I had a little trouble dual booting a couple days ago. Yesterday I managed to get XP and ubuntu to install each to two SATAs.
Before that, I had ubuntu on an IDE. So I was migrating files from the IDE to the SATA XP drive while in XP.

When I was finished, I rebooted up to ubuntu again only to find the hang on mounting drives. Given a few seconds, the usb devices would flash and then I'd get a black screen with the good ol':
> 
mount: Mounting /dev/sdb1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Busy Box v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off
# _

And then it just freezes... what happened man? you used to be cool.

It doesn't seem to care what I do, I unplugged USB devices, changed boot order, disabled the IDE and tried just the SATAs, Tried changing master/slave order. Nothing seems to work, and the TTY error doesn't allow me to enter any text.

At this point i've been staring at it and the links ubuntu demon posted on the subject for an hour and a half and i'm starting to lose my temper. It seems really temperamental/flimsy without justification.

Is there any way I can edit files crucial to ubuntu to fix this?
I can't log into it at all, all I can do is log on the live CD or  a fresh, driver-less install of XP. A nightmare. :mad: 

Someone lend a hand and keep me from reversing my loving open stance on trying linux. I was okay with losing my entire XP install for Ubuntu until it too crapped out on me.

I'd post .list files and stuff but I have no idea how to access them since it won't let me type.

If I unplug the SATAs, I can access the IDE install of ubuntu, but that's no help - that's the one I want to remove.

So, to sum it up: SATA1 has XP, SATA2 has Ubuntu that I love but doesn't work, and the IDE has Ubuntu I want to delete.

---

### Post by Emceay on 2006-07-13
Is there no way to turn 'job control' on? I've restarted my computer dozens of times now and my scalp is starting to hurt. :(

*Nevermind. Ironically, it was faster to just reformat and reinstall Ubuntu than wait for help.* ](*,)

---

### Post by Draaku on 2006-07-25
I have the same problem atm. i thought my drive had failed since it has been operating fine until a few days ago. I may just pull it and use another.

---

