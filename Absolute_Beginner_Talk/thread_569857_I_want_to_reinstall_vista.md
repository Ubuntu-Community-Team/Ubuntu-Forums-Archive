---
title: "I want to reinstall vista"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by framed on 2007-10-07
So a friend of mine comes over, and tells me that I just have to try out ubuntu. I had heard a few good things about it, so I figured I'd give it a whirl.

I proceeded to *install* it instead of "trying it out", only to have my HDD formatted. As angry as I was that I just lost my music collection and other programs, I had no one to blame but myself. Well, let me just say that my linux experience has not been a pleasant one, and I want to go back. 

So I pop in my vista upgrade disk, and low and behold, I'm unable to reinsall vista because I'm no longer upgrading from windows XP (even though I did own XP). I've looked around, and can't find my XP disk.

So I go pick up a new full install vista home premium, fully confident that I will be able to get my old OS back. 

I fire it in the tray, enter the CD key, and find out that I still can't install cause my HDD isn't properly set up for vista installation. 

I'm sure that this has something to do with when I put ubuntu on my HDD, but don't know what to do to get plain ol windows back. 


What do I have to do?
Thanks in advance.

---

### Post by Frak on 2007-10-07
Use the formatting utility that comes with Vista and you'll be just fine. It will do all the work for you.

---

### Post by jayaramk on 2007-10-07
when u install ubuntu or any other linux... the file system it takes is ext3 which is not supported by any of the windows operating systems.... so u need to format ur hard disk and convetr them to fat32\nfts partitions... *deleted*

---

### Post by jrlii on 2007-10-07
I'm guessing you will have to run a partitioning program to get the disk into a state Vista is willing to deal with. . . 

Always, Always! ALWAYS! backup your data before you fool with operating systems, be they Window, Mac or Linux. (Sorry, I couldn't help myself. . .)

As cheap as hard disks are, it may be easier to just buy a new one. . .

---

### Post by rsambuca on 2007-10-07
You can also do it with just your upgrade disk, but you have to install it twice.  The first time you don't enter your trial and you will have a trial period.  You can then just install again, over this, and it will recognize the trial vista, and you can upgrade over top of it, this time entering your product key.

---

### Post by Sklasko on 2007-10-07
Reformatting your hard drive from the Vista installation disk is a simple process. Not everyone in this forum is objective when they give advice on Windows, so don't let anyone tell you to stick with Ubuntu if you don't want to.

Vista should give you the option to format your HDD to NTFS. Fairly simple.

---

### Post by HermanAB on 2007-10-07
Hmm, I can feel your pain...

The Ubuntu install system is a little lacking.  If your friend had given you almost any other distribution, then it would have made your machine dual booting and everyone would have been happy.  So, for a second try, I would recommend Mandriva over Ubuntu.  Mandriva has better wizards.

A simple solution is to zero out the first little bit of the disk drive before trying to install Windoze.  Boot with a Live CD, such as Ubuntu or Knoppix, then do:
$ sudo dd if=/dev/zero of=/dev/sda bs=512 count = 1

Hope that helps!

Herman

---

### Post by jrlii on 2007-10-07
Sounds like the stuff on this thread, though it deals with XP rather than Vista.

[http://ubuntuforums.org/showthread.php?t=569274](http://ubuntuforums.org/showthread.php?t=569274)

I didn't have a bit of trouble with my Ubuntu install, but when I installed Windows on my current disk, it was partitioned with the assumption that I would be getting Linux, rather than th default all-one-big-happy-partition Windows wanted to do.

---

### Post by framed on 2007-10-07
Okay I've tried to format via the vista option, but it just results in an error message. Is there any way I can format within linux (keep in mind I have no idea how to do anything in linux so a complete tutorial would be needed).

---

### Post by rsambuca on 2007-10-07
If you still have the Ubuntu liveCD, you can use gParted and format the drive as ntfs.  You should then be able to install Vista.

---

### Post by RyanZec on 2007-10-07
> **HermanAB said:**
> Hmm, I can feel your pain...

The Ubuntu install system is a little lacking.  If your friend had given you almost any other distribution, then it would have made your machine dual booting and everyone would have been happy.  So, for a second try, I would recommend Mandriva over Ubuntu.  Mandriva has better wizards.

A simple solution is to zero out the first little bit of the disk drive before trying to install Windoze.  Boot with a Live CD, such as Ubuntu or Knoppix, then do:
$ sudo dd if=/dev/zero of=/dev/sda bs=512 count = 1

Hope that helps!

Herman

I will admit that the installer for ubuntu with an existing partition on the hard does not work well but i don't know why he did not A. Try out the liveCD version first and/or B. Back up his data.  I would still recommend ubuntu, you guys have bay far the best community of any distro i have tried(and i have tried mandriva and did not like their community).  Ubuntu also seem to be one fo the fast growing Linux Distro according to google trends [http://www.google.com/trends?q=Ubuntu%2CMandriva%2CFedora%2CSuse%2C+gentoo](http://www.google.com/trends?q=Ubuntu%2CMandriva%2CFedora%2CSuse%2C+gentoo)

---

### Post by HermanAB on 2007-10-07
'Buntu is a nice lightweight system and I use it myself, but I also use Redhat (ugh), Fedora (yuck), Centos (same ugh), Mandriva (cool), OpenBSD (damn) and Solaris (aaaaargh)...

Each one has its place under the sun and if you are the Windoze pointy clicky wizardy kind, then *nothing* beats Mandriva.  I use it because it is a heavy installation, with every tool I need already installed, so it saves me lots of time with what I do for a living.  

I mainly run Xubuntu in virtual Machines, because it is small and light weight, with a heavy Mandriva underneath as the host system.

Cheers,

H.

---

