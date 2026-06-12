---
title: "[SOLVED] Install XP after Ubuntu Install?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by dominicw on 2008-04-14
I messed up with a repartition and lost my Windows XP install.  I repartitioned the drive to have 10 GB free for Ubuntu and 50gb free for Windows.  I installed Ubuntu not knowing that the suggested method was Windows first/Ubuntu second. 

So do I have to start over?  I am happy with my install and using Ubuntu for a while now.  I have my files on here and also have all my tweaks in place.

I am running 7.10 on a Dell XPS M1210 - 1gb ram 1.8ghz Duo Core.

Thanks in advance, I noticed the forum is full of answers for Windows XP first installs, but I am hoping someone can help with my case.

Dominic

-Happy Defector From Freespire

---

### Post by Saint Angeles on 2008-04-14
boot up a live CD of ubuntu and run gparted.

you can change the size of your ubuntu partition from there... make whatever size partition you want. just keep it as free space or make an ntfs partition...

then pop in the windows disc and select the partition you just made. if theres an option for installing a bootloader, make sure don't.

if you do, you will need to install grub again.

---

### Post by Amstell on 2008-04-14
check out super grub.....just burn the image and boot it up....instructions are easy to read....

this will replace your boot loader to grub so you can keep both partitions

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Peace

---

### Post by jflaker on 2008-04-14
Windows tends to do a predatory install if you are not careful........it will wipe your current partition.

During the XP install, you will see the options for choosing the partition, carefully choose the correct one.

The other option is to install VirtualBox and install it on a Virtual system........

---

### Post by dominicw on 2008-04-14
These answers took too long  (2 minutes!!!!!)  :)   What a great community, thanks for these suggestions.

I went to Virtual Box website, but do not understand fully what it is.  It seems like an emulator...is that true?

I may attempt a full install on my ntfs partition I made.  Whats the worst that can happen...I have to spend 10 minutes reinstalling Ubuntu.  

Again,  thanks for the feedback - I had no clue before I got these responses.

Dominic

---

### Post by Michael.Godawski on 2008-04-14
Hi. You can also check out these site. There just choose your configuration.
[http://apc.simbient.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apc.simbient.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by dominicw on 2008-04-14
Michael,

This is the choice I am going with, thanks.  How much of my 80gb drive should I leave for Ubuntu?  I have it set for 10GB now.  Inderstand it depends on how much personal files I have, but what is the rule for Ubuntu and a healthy amount of apps?

Dominic

---

