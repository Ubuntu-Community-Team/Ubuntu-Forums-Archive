---
title: "Can't get Ubuntu to start"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2007-09-03
I have Ubuntu installed on my laptop; I used WUBI. Everything there is good.
Now I want to put Ubuntu on my desktop. I would really like to do it without the training wheels (WUBI), but maybe later (that looks like it's going to be a REAL headache).
So, I installed WUBI and rebooted into Ubuntu but as far as I can get is a black screen that says;
Booting GRLDR.....
Turning on gate A20... success.
And then it stops, with no disk activity.
Here's the info I think is important.
I sure hope someone can get me past this, I really want Ubuntu running on my desktop.
I would like to have the WUBI folder on K:. K is a SATA drive.
I have a Abit Fatal1ty AA8XE motherboard.
Thanks for any help you can provide.

[IMG]http://farm2.static.flickr.com/1231/1314658197_ad0c52fbf7.jpg?v=0[/IMG]

---

### Post by SOULRiDER on 2007-09-03
Installing from the Live CD is REALLY easy. You can downlaod the CD from:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

For installation help see:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

And it would be nice if you also read aobut how software is installe don linux too:
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

Remember we are here for you int he forums and you can also ask for help on IRC when you are installing so dont be scared!

---

### Post by stevelasvegas on 2007-09-04
Thanks for the links. MyAbit Fatal1ty AA8XE is an Intel Pentium 4 System Board Socket 775, not listed in the supported hardware. I know that doesn't mean it won't work, but I can't get it to even boot. I've run the Live CD, it works, that would mean to me that it should run. I guess I'm looking for someone who has the same motherboard that is running Ubuntu to confirm that it does run. This motherboard is a couple of years old. I'm stuck.
Anyone?

---

### Post by SOULRiDER on 2007-09-04
Do you see GRUB? Can you boot into Windows? Do you get any errors when you try to boot linux?

---

### Post by spur on 2007-09-04
The table showing your hard disks says 'k' is an ntfs drive. To use Ubuntu you will need a partition that is linux friendly. (ext 2 or reiserfs). I haven't used wubi at all so if that gets installed and works on an ntfs disk then ignore what I just said.
If you install from the live cd you will be prompted to create a partition and a swap partition as you need both.
Pardon me if you already knew this but it seems to me if you have tried to install from the live cd already then it didn't install at all. Or was that table referring to before your install?):P

---

### Post by stevelasvegas on 2007-09-06
This conversation has moved here [http://ubuntuforums.org/showthread.php?t=542397](http://ubuntuforums.org/showthread.php?t=542397).

---

