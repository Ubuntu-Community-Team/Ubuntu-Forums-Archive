---
title: "Clasic n00b woes i guess..."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by emmet2125 on 2007-01-18
ok,

my dell crashed not so long ago and now WINXP simply will not boot.

i have dug out this ubuntu 6.06 LTS live CD and am now running ubuntu from it.

after much trouble i sorted out my internet connection.

anyways...

the reason i am using ubuntu is that i hope to save my documents from my HDD and re- intall windows.

but

when i use the file browser in ubuntu to try to acsess my HDD i recive an error message saying "Unable to mount the selected volume." and "error: device /dev/sda2 is not removable

error: could not execute pmount"

i figure i need to istall ubuntu to the computer but am scared to loose important documents

help much appritiated.

thanks.

---

### Post by punx45 on 2007-01-18
live CDs are often used as rescue disks, so you should be able to mount the NTFS drive and copy files to a USB drive or something like that.

this is written for full installs, but it should probably work for the live CD too.
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

DONT write to the NTFS (windows) drive.

---

### Post by annda on 2007-01-18
the liveCD is meant to be a tryout of a new operating system, so some things are a bit complicated for people who want to have extra functionalities - such as running a rescue OS. those are the details:

actually, you don't need to modify the fstab file if you just want to recover your windows files and do not plan mounting/using the disk in the future (since you want to return to windows)

in that case follow the first 2 steps (fdisk and mkdir).

(by the way: you open the terminal through System/Accessories)

after that you should type another command in the terminal:

```
sudo mount /dev/something /windows
```

"something" is the name of your windows partitions that you have found out from fdisk

you should be able to see the contents of your windows disk in the file browser now. if you still have problems with that, there's another trick: again use the terminal and type:

```
gksudo nautilus
```

this will let you run the file browser as administrator with the necessary rights and permissions to see all the files on the computer.

good luck!

---

### Post by Hendrixski on 2007-01-18
Oops, double post.  sorry

---

### Post by Hendrixski on 2007-01-18
If you're not looking to install then there are better LiveCD's than Ubuntu to help you recover data.  Some of them come with data recovery, and hard-disk forensics tools.  So if your hard-drive is totally hozed (meaning it won't mount in Ubuntu) you can use forensics tools to retrieve data from parts of it that aren't corrupted.  Often it's just a small part of the drive that craps out that causes problems.

Check out [www.distrowatch.com](www.distrowatch.com) to find out which one is right for you.

---

### Post by annda on 2007-01-18
exactly, distrowatch.

this seems to be very promising, although i must admit i haven't tried it yet (no need so far)

[SystemRescueCd]("http://distrowatch.com/?newsid=03965#0")

---

