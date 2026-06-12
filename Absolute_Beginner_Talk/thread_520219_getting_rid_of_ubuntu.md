---
title: "getting rid of ubuntu"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by smbhat01 on 2007-08-07
i have not yet downloaded and installed ubuntu. i just want to try it out to see whether i like it, and i want to make my computer dual boot, as it as a family computer and the rest of my family do not want to use ubuntu. suppose i do not like ubuntu and want to just continue using windows xp. How do completely get ubuntu off of my computer without getting rid of xp. Please use simple vocabulary, as i am not very smart when it comes to using computers

---

### Post by Dr Small on 2007-08-07
I think (someone else may correct me if I am wrong), you just delete the partition that Ubuntu installed on. I may be wrong.

---

### Post by jmtjet on 2007-08-07
Why not just use the live CD. Then you won't have to install anything. Just pop the CD in the drive and reboot. You'll get to a desktop with the option of installing or running from the CD.

---

### Post by S15_88 on 2007-08-07
pretty sure that's it, assuming you don't have files in ubuntu u want to keep, all u have to do is pop the live cd in, but i recommend using the GParted Live CD, and delete the ubuntu partition then expand your XP partition back to what it used to be. that shouldn't disrupt anything on XP.

Thanks, Alain

---

### Post by sonofusion82 on 2007-08-07
after removing the ubuntu partitions, also do a fdisk /mbr in dos command prompt to restore windows master boot record.

[http://www.debianadmin.com/uninstall-or-remove-linux.html](http://www.debianadmin.com/uninstall-or-remove-linux.html)

---

### Post by scapalexis888 on 2007-08-07
> **S15_88 said:**
> pretty sure that's it, assuming you don't have files in ubuntu u want to keep, all u have to do is pop the live cd in, but i recommend using the GParted Live CD, and delete the ubuntu partition then expand your XP partition back to what it used to be. that shouldn't disrupt anything on XP.

Thanks, Alain

One more thing: Make sure you put a bootable flag onto the windows partition. I assume you are using GRUB to dual-boot? You don't really want GRUB if you are only booting up WinXP. You can put the flag in a Gparted Live session

---

### Post by anewguy on 2007-08-07
DO NOT, I repeat DO NOT delete your Ubuntu partitions.  You must set the MBR on your disk first (since you are dual-boot) or you will not be able to boot Windows.  Please follow this how-to:

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

It will show you how to correctly delete Ubuntu and still have a bootable Windows system.:)

---

### Post by Dr Small on 2007-08-07
See? What did I tell you? I thought I sounded wrong... :D

---

### Post by tashmooclam on 2007-08-07
It is easy to "try it to see if I like it". 
You get an Ubuntu DVD/CD from Amazon or someplace.
You can run Ubuntu off the CD all you want to, and it is NOT installed on your hard drive.
You can actually do this indefinitely, but realize that many things will happen more slowly as hard drives do things much faster than the CD/DVD drive of your computer.
Try Linux Mint while you are at it, try them both. Almost identical, but Mint has Flash, Java, etc already. 
To install onto the hard drive is something you can decide to do later.
If you are running XP, eventually you must decide anyway to use Ubuntu (good), buy Vista (bad) or buy a new computer with Vista (worse). 
You are smart not to wait and get started now.
If you can afford it, one of the Ubuntu books will help you out, but they cost $30+
:)

---

### Post by cobrn1 on 2007-08-07
Do you have a windows installation CD - you'll need one for this:

1) load up the Gparted cd. Delete the ubuntu partition and resize the windows one to fill the entire harddrive.

2) quit and boot up the windows installation Cd. once it's loaded press R to get you into the recover console. THen type fixmbr and you'll be Aok

If you don't have an installation disk then go into windows first, open up a MS-dos window and type in:   fdisk /mbr

Now you can load up gparted and delete the ubuntu partition (you won't need the cd if you do the MS-Dos thing instead.)

EDIT: of course, if your pc is reasonable modernish you could just run the live CD to get the feel for it, but it is slower than the installed thing - however, it's a really great way to try out linux without commiting it to the harddrive, so it may be worth a look. If you do install and want to remove ubuntu then follow my steps above.

---

### Post by anewguy on 2007-08-07
> **Dr Small said:**
> See? What did I tell you? I thought I sounded wrong... :D
I messed this up a few times myself, hence why I wrote the guide.  Like I've always said:  I thought I made a mistake once but I was mistaken!!:)

---

### Post by vexorian on 2007-08-07
you can use vmware on windows and a light weight thing, I tried xubuntu and it works pretty well provided your computer is good enough, that really works out if you just want to try and don't want to interfere with the rest of the family.

---

### Post by anewguy on 2007-08-07
BTW - I never did tell you - follow the advice on this thread and just run off the LiveCD for a while.  You may have a little trouble using wireless networking, you sound may not work correctly, but hey - you'll be trying out Linux and Ubuntu without the worry of messing up your family PC.  If the time comes you want to actually install Ubuntu, and since this is family PC, be sure to talk it over with your parents and siblings first.  Be prepared for them - read as much on installation as you can, paying particular attention to partitioning and dual-booting.  You want to be able to intelligently answer their "why" questions before you start, and you'll want to know there really is enough disk space, and that you've done your homework so you feel comfortable with the installation.  Be sure to ask questions if you need to - we've all been there, and that is why we are here now.:)

---

### Post by findik1 on 2007-08-18
> **anewguy said:**
> DO NOT, I repeat DO NOT delete your Ubuntu partitions.  You must set the MBR on your disk first (since you are dual-boot) or you will not be able to boot Windows.  Please follow this how-to:

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

It will show you how to correctly delete Ubuntu and still have a bootable Windows system.:)

OK unfortunately I erased ubuntu before doing that and now windows does not start automatically. How can get back to windows now?

---

