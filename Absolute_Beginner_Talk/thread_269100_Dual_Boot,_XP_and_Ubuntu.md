---
title: "Dual Boot, XP and Ubuntu??"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by netwhizkid on 2006-10-01
Hello I am completely new to Ubuntu and Linux but am dying o give it a go. I have the Live CD of Ubuntu 6.06 Dapper Drake and have booted it from the CD and have decided I want it on my PC alongside XP.

I have reformatted my XP Computer and done a new install of XP as it got corrupted. 

I have a 160GB HD on my Dell Dimension 8400 and have it in three partitions. 

I have my local Disk C at 36.6GB with my Windows Install and some files. 

I have a D drive with 90.5GB and that is almost full of files, music etc.

When I Formatted for XP I created a new Partition (which is unformatted and is about 22GB), I would like to be able to load Ubuntu onto this but don't have a clue really.

I am pretty good at XP and would like to get stuck into Linux now, any guides or help etc. on how to have the two systems booting together would be great. I am based in Ireland, which has a small amount of Linux users, and Ubuntu is regarded highly on the various messaging boards. 

Any help/advice is greatly appreciated.

Regards netwhizkid

---

### Post by Kateikyoushi on 2006-10-01
Here is a [guide]("https://help.ubuntu.com/community/WindowsDualBoot") how to set up ubuntu and windows to dual boot.

---

### Post by petit.padavoine on 2006-10-01
It's pretty straightforward to install a dual-boot system from the Live CD.

Just click on the 'Install' icon on the Desktop. You'll then have several options for partitioning, including setting everything manually.

Personally, I have a 40 GB HD with four partitions: 

[LIST=1]
[*]The Windows partition (20-25 GB)
[*]The Ubuntu /usr/bin partition --> system, applications, etc... (5-10 GB)
[*]The /home partition --> personal documents, music, etc... (4-9 GB)
[*]A swap partition --> used as spare space if your RAM is overloaded.
[/LIST]

There are other setups, it all depends on what you want.

---

### Post by waxfactor2nd on 2006-10-01
ive done just like that but i get the error 22 as i said / therefor i need some help

edit: doooh sry i thought this where the thread [http://ubuntuforums.org/showthread.php?p=1565624](http://ubuntuforums.org/showthread.php?p=1565624) which i ask for help / the names are almost the same / sry / but if you know how to help id be really glad

---

### Post by netwhizkid on 2006-10-01
= > **petit.padavoine said:**
> It's pretty straightforward to install a dual-boot system from the Live CD.

Just click on the 'Install' icon on the Desktop. You'll then have several options for partitioning, including setting everything manually.

Personally, I have a 40 GB HD with four partitions: 

[LIST=1]
[*]The Windows partition (20-25 GB)
[*]The Ubuntu /usr/bin partition --> system, applications, etc... (5-10 GB)
[*]The /home partition --> personal documents, music, etc... (4-9 GB)
[*]A swap partition --> used as spare space if your RAM is overloaded.
[/LIST]

There are other setups, it all depends on what you want.


Sounds good I will give it a try; I have 1Gig of RAM, would I still need a swap partition? I have currently three partitions as I said in my first post, with one "reserved" for Ubuntu would this one then become three or would it be subdivided within Ubuntu i.e. would I then have 5 partitions showing up in Win XP or just three? Sorry to sound confusing but I am totally new to linux. :( 

Thanks for the replies!

---

### Post by petit.padavoine on 2006-10-01
Don't worry, you're not at all confusing and much more knowing than I was when I started Ubuntuoing...

Anyway, even though you have 1 GB of RAM, it's always good to have swap, except if you really need the disk space (in my opinion).

As for partinioning, since you've already started, it would be better to look at it again from the Ubuntu install manual partitioning option, and set it up the way you like all over again, as you don't know what auto-partinioning will do. As you said, you don't want to end up with 5 partitions...

Lastly, you should check out the link posted earlier on and other guides, as I'm not at all an authority on the question :)...

---

