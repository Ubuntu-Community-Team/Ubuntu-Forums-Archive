---
title: "G-Parted Not Working :("
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-07-19
is it possible to resize the Ubuntu partition without leaving Ubuntu?

I've tried to load the LiveCD to resize the partition (bring it from 110 gb to 70 gb), and it crashed during the function. I found that it crashed when searching for errors...now I'm scared :P

Any ideas or suggestions?

---

### Post by Seisen on 2007-07-19
You can't resize the partition while it's mounted. You can download the Gparted Live-cd or if you have a usb-key you can download it to that.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by tcoffeep on 2007-07-19
:( You never read the second half of my entry.

---

### Post by Seisen on 2007-07-19
I assumed you were talking about the Ubuntu Live-cd.

---

### Post by tcoffeep on 2007-07-19
No. I had downloaded the latest ISO of G-Parted.

I've done this in the past, and once upon a month ago, resizing with G-Parted actually caused Ubuntu to be unrunnable.

I'm guessing there are no alternatives to G-Parted?

---

### Post by Seisen on 2007-07-19
I know knoppix has gparted installed on that, you download the live-cd and try that.

---

### Post by KIAaze on 2007-07-19
Yes, but on Knoppix it's also Gparted (or is it QTparted?), so that shouldn't solve the problem unless it's a more recent version I think.

There's also QT-parted, but from what I know, it's the same as Gparted, only with a QT instead of GTK.
I think both are GUI frontends to GNU parted (but I could be wrong).

Another program that might help you is gpart:
[http://www.stud.uni-hannover.de/user/76201/gpart/]("http://www.stud.uni-hannover.de/user/76201/gpart/")

Or the tools on the System rescue CD:
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

P.S: To check your disk for errors, use **fsck**.

---

### Post by tcoffeep on 2007-07-19
> **KIAaze said:**
> Yes, but on Knopix it's also Gparted (or is it QTparted?), so that shouldn't solve the problem unless it's a more recent version I think.

There's also QT-parted, but from what I know, it's the same as Gparted, only with a QT instead of GTK.
I think both are GUI frontends to GNU parted (but I could be wrong).

Another program that might help you is gpart:
[http://www.stud.uni-hannover.de/user/76201/gpart/]("http://www.stud.uni-hannover.de/user/76201/gpart/")

Or the tools on the System rescue CD:
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

P.S: To check your disk for errors, use **fsck**.

When I run fsck, this pops up :

```
/dev/hda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 

```


Should I say yes? is there really that much risk?

---

### Post by KIAaze on 2007-07-19
I don't know how much risk there is, but I wouldn't risk it.

[LIST]
[*]The easiest would be to run fsck from the Ubuntu Live CD.
If it mounts your partitions automatically, you can still unmount them with the **umount** command.

Other possibilities:
[*]Configure it to run at bootup before the partitions are mounted:
[QUOTE=Woodsman]To continue drkstr's advice, you could add [color=blue]touch /etc/forcefsck[/color] to [color=blue]/etc/rc.d/rc.local[/color]. This would automatically create the [color=blue]/etc/forcefsck[/color] file, which [color=blue]/etc/rc.d/rc.S[/color] looks for to perform a forced file check upon the next boot-up. If you wanted the file system check only every other day, you could add some additional scripting instructions in [color=blue]rc.local[/color] to create [color=blue]/etc/forcefsck[/color] based upon the day of the week.[/QUOTE]
[http://www.linuxquestions.org/questions/showthread.php?t=478777]("http://www.linuxquestions.org/questions/showthread.php?t=478777")


[*]Or remount / as read-only:
```
sudo mount -o remount,ro /
```

After that, to remount it as read/write:
```
sudo mount -o remount,rw /
```

I don't know how safe those last two methods are, but since fsck seems to ask before running on a mounted system, it shouldn't be too dangerous.


[*]Eventually, there's also a way to change the frequency at which fsck runs:
[http://doc.gwos.org/index.php/ChangeDiskCheckFrequency]("http://doc.gwos.org/index.php/ChangeDiskCheckFrequency")

But the best and easiest way is probably to run fsck from the live CD.
[/LIST]

---

