---
title: "My new MacBook"
date: 2008-12-25
forum: Apple Hardware Users
---

### Post by olavjunior on 2008-12-25
I just got a new MacBook (5.1) for Christmas! It's a nice set of hardware, but I wasn't prepared for it, I really want Gnome, but it might be nice to get to know osX as well..

But a couple of show stoppers for me:
[LIST=1]
[*]I have a 1 TB disk formatted as ext3. So if I wan't to try osx, how do I access it? Have tried mount_ext2 without any luck (device busy). (Prog: ext2fs) Maby the best solution is to reformat it to ntfs?? (Uh... windows file system.. But I've read something about uiid 501 in mac and 1001 in LInux causing some permission problems)
[*]I'm pretty fed up with hardware not working, and have been very satisfied with my last good working Thosiba laptop. So I'm not really up for spending HOURS trying to get the box to work. Should I just leave Ubuntu behind 'til the hardware gets older?  (Not sure if I can... :))
[/LIST]

Thanks for any tips!

---

### Post by WinterWeaver on 2008-12-25
I have ubuntu running on my Macbook 2.1
It's not the shiny new ones tho, I got this on in June.

Hardy is running very nicely on it, after some initial hick-ups of course.
This link will give you good help on installing ubuntu on a macbook :)

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Good Luck!

WW

---

### Post by Rog-Mahal on 2008-12-25
[This thread]("http://ubuntuforums.org/showthread.php?t=1013980") talks about a tool that might help with your ext3 disks with a bit of work. 

I'm running a Macbook 2,1 as well and all of my hardware works great with Ibex. The only thing I needed to do any kind of work on was the isight driver, and that was easy because patching the firmware is really well documented. I have no idea about the newest Macbooks though.

---

### Post by olavjunior on 2008-12-30
Well, Ive installed it, and its pretty ok. Cant get backlights on my keys to work though, but I bet Ill find a way. Click and drag is a mess as well. 

But what I need to do now is share a home between ubuntu and osx. Ive changed both users uids to the same, and I can access files from ubuntu on the osx partition. So I thought about formatting it in hfs+ without journaling. But I read somewhere that creating a new partition on my osx partition now will erase ALL data on that partion! Is that really the case?? Ive used gparted alot of times within Ubuntu and never lost any data on the remains of a partion as long as there is free space!??

---

