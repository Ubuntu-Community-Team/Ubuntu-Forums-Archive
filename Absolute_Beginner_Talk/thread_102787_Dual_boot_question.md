---
title: "Dual boot question"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by CanadaGradeEh on 2005-12-12
I know you guys probably hate these topics question, but atleast you're getting more traffic;) 

Anyway, from a bit of chatter with some people earlier it looks like I'm going Ubuntu for my first Distro. I have an 80 GB IDE HDD that I'm using for Windows and gaming right now with 20 GB free to install Linux if I want to, but if possible I want to be able to use my old 20 GB IDE HDD as my Linux HDD. If I format and install the 20 GB HDD as the slave drive, could I use it as a dual boot setup then? I want to be able to choose either Windows or Linux at startup to boot (boot using one HDD or the other). Could I do that?

I'll have more questions to ask after.

PS - I just saw my title. Whoever made up the forum ranks for this messageboard kicks ass.

---

### Post by nikopol on 2005-12-12
Yep - no problem at all. Fire away

---

### Post by Turtle.net on 2005-12-12
Yes, during the installation you will be able to choose how you want to organise drives and partitions.
Ubuntu does the rest for you ;)

---

### Post by CanadaGradeEh on 2005-12-12
Ok, so here comes the question load. First off though, I'll let you know that, even though I am asking a lot of questions to things that may seem simple to you, I know a bit about how things work so I'm not a complete newbie. Just mostly newbie :D heh

First: How can I format my 20 GB hard drive.. JUST format it. Obviously I'm not wanting to install Windows so I won't do it with the Windows CD. This may seem simple to you, but I've never done it before so I don't know.
From a bit of reading I've done I may want to try Mepis, but I don't want to just give up from what I've read; I'm not going to be scared off. I think I'll stick Mepis in free space on my big hard drive and have Ubuntu to itself on the seperate, smaller hard drive.
And, just to make sure here (I know you already answered Turtle), I will be given an option to boot from either one HDD or the other at bootup?

More questions to come. I'll just stick 'em to you one at a time. While I wait for a reply I'll just read around the forum more. Thanks a lot guys!

---

### Post by bored2k on 2005-12-12
The Ubuntu installer has a disc partitioning step that could format your drive should you want to. It's so easy there's no way to explain it.

---

### Post by LoclynGrey on 2005-12-12
Just let Ubuntu "format/partition" your separate 20GB HDD during the install.
You will then have to go modify your boot loader.

I've got a separate hdd dual boot, but with Ubuntu on a 40Gb as a master and then windows on another 40Gb as a slave.
I edited my grub boot loader to give me the choice at post boot screen for either Ubuntu or Windows.

Edit: an easy way to set it up is to disconnect your windows drive, connect your ubuntu drive and just do a normal install.
I don't know how to modify a windows boot.ini file (because I have grub do my boot loader stuff) but there should be some info already posted on this forum somewhere.

---

### Post by CanadaGradeEh on 2005-12-12
Ok, so I think I'll try that first. I didn't know the installer did that automatically. I'll disconnect my Windows drive, put in my smaller drive, then install it. Great.
But how do I edit the boot loader? Would that be in my BIOS? I guess I could just use this Grub loader like you, but I don't have any idea about that either.

Thanks for the info thus far guys. I'll go get my other HDD now for when I actually start this thing :D Oh jeez, I love friendly forums :)

---

### Post by super on 2005-12-12
you may want to keep the 80gb drive plugged in. that way you can install grub onto the mbr (master boot record) and boot both linux and winxp right away.

editing grub is pretty easy. (assuming you know how to read! :p ) [here is an example]("http://www.ubuntuforums.org/showthread.php?t=102088") of the grub config and how to edit it.

ps: good to see another canadian! :D

---

### Post by nikopol on 2005-12-12
[QUOTE=CanadaGradeEh]Ok, so I think I'll try that first. I didn't know the installer did that automatically. I'll disconnect my Windows drive, put in my smaller drive, then install it. Great.[/quote]

probably simpler you leave it plugged in - it'll do the boot load automagically then.
> But how do I edit the boot loader? Would that be in my BIOS? I guess I could just use this Grub loader like you, but I don't have any idea about that either.
you can edit the bootloader within ubuntu - but as I've said, it should set itself up correctly if you leave the win hd in during install.

---

### Post by CanadaGradeEh on 2005-12-12
Thank you for the welcome :) I've been on a lot of Canadian-based sites recently, so while signing up it didn't occur to me that I may be slightly alone here :(  Good to know I have some hosers with me! :D 

Ok, so here are the last of the questions until I shut down and do everything.
This is what I'll be doing?
1. Install Grub first
2. Burn Ubuntu to a disk
3. Have the disk in my drive and shut down
4. Begin format and installation process

Is that it? It won't matter if I burn Ubuntu onto a DVD would it? All I have are blank DVD disks right now. I'd think it wouldn't though.

*EDIT*

Oh, and another emberassing question: which file(s) do I download? I'm running on a Barton 2500+ so I'm pretty sure I don't download any of the amd64-labelled ones. I'd guess i386 files..

---

### Post by CanadaGradeEh on 2005-12-12
Hmm, post to top and also say that GRUB is looking confusing lol. Where can I download it, and how should I install it? (first I have to find out the order of things here).

---

### Post by CanadaGradeEh on 2005-12-12
I hate to be pushy, but I'd like an answer :P
I just want to get this done tonight since I'm all hyped up for it :D
I'm just making sure I do everything right is all.

---

### Post by super on 2005-12-12
1. Burn Ubuntu to a disk
2. Have the disk in my drive and shut down
3. Begin format and installation process (this process will Grub at the same time)

grub is part of the ubuntu installation. you don't need to download it seperately. also barton is a kind of 'amd athlon' right? so x86 kind of install file that you want. it should be called ubuntu-5.10-install-i386.iso

have fun! :D

---

### Post by matthewv on 2005-12-12
You were right: you need the i386 file. Burn the iso, reboot, boot off the cd, and tell ubuntu to take over the second hard drive. It will do so, then ask you something about the boot loader. You should be fine with the defaults. It will then reboot: go to ubuntu, finish the install and you're all set.

---

### Post by CanadaGradeEh on 2005-12-12
Super, you're super! :D Thanks a lot guys. Wish me luck.

*EDIT*

WIsh me luck in an hour and a half :P lol. DL'ing faster than I expected atleast.

---

### Post by unisol on 2005-12-13
i386 it is! good luck heres hoping you enjoy ubuntu as much as i do

---

### Post by datakid on 2005-12-13
Now, this may seem sillier, but I've just installed ubuntu on an old machine I've got lying around here. I wanted to install win2k but for some reason it wasn't working - I'll get a new copy of the win2k disk tomorrow.


What I was wondering was if my overwriting the mbr when installing ubuntu would be causing the problem? 
(I've installed ububntu 2ce and debian numerous times, I'm just a little rusty) 

Should I download another mbr writer for an NTFS partition?

I've created a spare partition that is Fat32 which I wanted to install the win2k on - is there anyway to get a dual boot system that way, or must windows be installed first, then linux? I'm pretty sure that fat32 will need to become ntfs at somepoint, and if so when?

Cheers

---

