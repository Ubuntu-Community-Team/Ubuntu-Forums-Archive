---
title: "Odd partition"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by oldjock on 2007-09-02
I have installed Feisty 7.04 on an amd 1.6 ghz with 1gig ram and an 80gig HD. I dual boot with WinXP and the system runs fine.
I recently startd using Gnome and found an Icon for Hda8 on the desktop as well as my XP partitions.  On opening the Hda8 it contains a 0byte file named Lost+Found last modified several months ago. What is the purpose of this file and can I reclaim all or part of the 6gig partition it occupies.
I have a copy of Gparted on a CD

Regards Oldjock

---

### Post by be4truth on 2007-09-02
It looks to me that the partition hda8 is an empty linux partition. When you format a linux partition the operating system makes this folder and put everything in it in case of a crash.

---

### Post by airtonix on 2007-09-02
Lost+Found is a folder....if you delete that folder it will be automatically created again.

Imagine you do an fsck....
imagine that the drive has errors....due to reboot whilst cpu and harddisc access is ensuing.
imagine that you find recoverable chains.

the Lost+Found folder is where these recoverable chains end up as.

it happned to me

I (thought) that I had lost my entire season one of Blood the last vampire.....but no all the episodes were numerically named 000001.000 or something.....and deposited into the Lost+Found folder.

---

### Post by oldjock on 2007-09-02
Thank you, I realise it seems to be a legitimate partition but can I delete it to reclaim the space.

---

### Post by justleen on 2007-09-02
yes, you could remove it... and create a new partion, or resize the partition in front of it.
have a look a [gparted]("http://gparted.sourceforge.net/") (available in the repositories) if you want you mess with your partition table

---

### Post by oldjock on 2007-09-02
Thanks, I just wanted confirmation that I was not deleting a system file. 


oldjock

---

