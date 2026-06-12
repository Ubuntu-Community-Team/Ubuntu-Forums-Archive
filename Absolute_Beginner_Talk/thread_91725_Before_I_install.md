---
title: "Before I install"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by Boca on 2005-11-17
I have a few questions. I DLed the live DVD, just ran it and it works fine. I'm going to install into a 10GB partition next to XP. On the same drive is a 40GB FAT partition for programs. Do I need to make small partitions for boot and swap? Which file system (ext2, etc... gave me about 5 different choices on the live DVD) do I choose or does it matter? 

Thx!

---

### Post by pja on 2005-11-17
Boca - No, the Ubuntu installer will take care of that for you.  I have never bothered with configuring the partitions for Linux, always leaving it to the installer to pick what it thinks best.

I dual boot using a second hard disk so I allow Ubuntu to use the complete drive.  I assume that when you are installing it onto the same drive as Windows there is a dialogue to let you say how big you want to make the Linux partition.

If you have a Windows based partition manager then you could use that to create the third partition first and then let Ubuntu install into that.  I'm sure others with more experience of dual booting on a single drive will correct or amplify these comments.

I would use Google to do some more work on dual boot partitions on the same drive.

When installed, Ubuntu (all Linux variations) will install a 'boot loader' or boot menu into the master boot record (MBR) of your primary hard drive (say C: in Windows terms).  This is of no consequence and will not impact your existing Windows or other partitions.  The problem comes when you decide to get rid of Linux and want to 'junk' the boot loader.  This took me ages to resolve several years ago, so here is the solution:

Boot your PC from a MS-DOS floppy disk.  Run fdisk with the following switch:

**a:\> fdisk /mbr**

and that will set your master boot record back to its pristine state.

Hope any of this helps,
Peter

---

### Post by TeeAhr1 on 2005-11-17
Honest to God, this was exactly my question two days ago.  

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

This is a pricelessly good guide to doing that very thing.  I went through the entire installation with that printed out next to me on my desk.  But you can't print it from there!! *grr*  The tables and the images get messed up, or at least I couldn't do it from home *or *work.  After an unholy amount of time wasted messing with it, I saved the website as a PDF and printed it like that.

EXCEPT: I the instructions at the very end for mounting the partition for "shared data" do not work, at least for me!  I don't know why, but am trying damn hard to find out.

---

### Post by mcmillan on 2005-11-18
Like pja said you can let Ubuntu do it for you. The standard (at least with Hoary which I still have) is to just use have a / partition and swap, which is the minimum. I personally would prefer to have /home as it's own partition and am going to change this once I have time to upgrade to Breezy and will be doing lots of backing up anyway.

---

### Post by pja on 2005-11-18
This is a very good explanation of the Ubuntu install process.  There is only one problem that i can see:  **nobody** would set their 'Time Zone Configuration' to "***... Brisbane (Queensland ... )***" - surely you would set it to "***... Sydney (New South Wales ... )***.

Nice piece of work,
Peter ;-)

---

### Post by Boca on 2005-11-18
Thx for the help so far! I'm just about ready to install but am pondering whether or not to install GRUB in the MBR. 

This site, [http://users.bigpond.net.au/hermanzone/p2.htm]("http://users.bigpond.net.au/hermanzone/p2.htm") says he hasn't had any problems doing that while this site, [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/]("http://www.crhc.uiuc.edu/%7Emjmille2/howtos/dual-boot-linux-and-windows/") says not to do it and set up XP to handle the dual booting. 

I'll post back later on how it goes :)


[SIZE=1]
[/SIZE]

---

### Post by pja on 2005-11-19
I have been 'fooling around' with Linux for several years now and have never had a problem with Grub being installed in the MBR.  And even if you do, then it is so easy to get rid of (A:\>fdisk -mbr).

Good luck,
Peter  :smile:

---

### Post by Boca on 2005-11-19
[QUOTE=pja]I have been 'fooling around' with Linux for several years now and have never had a problem with Grub being installed in the MBR.  And even if you do, then it is so easy to get rid of (A:\>fdisk -mbr).

Good luck,
Peter  :smile:[/QUOTE]

Well, am now posting using FireFox in Ubuntu :) Had some problems trying to install from the live DVD so DLed the install CD and here I am. Ended up installing GRUB to the MBR.

I've been able to customize FF to what I wanted by downloading and installing extensions. But now I need to learn how to navigate Ubuntu. I've never used Linux before so I need the most basic and beginner instructions (which includes the next few things I need to do know after the install). I've never used the command line before (don't even know how to get to it yet :) so if someone can point me where I can start to learn I would appreciate it!

Thx!

---

### Post by pja on 2005-11-19
[QUOTE=Boca]...But now I need to learn how to navigate Ubuntu. I've never used Linux before so I need the most basic and beginner instructions (which includes the next few things I need to do know after the install). I've never used the command line before (don't even know how to get to it yet :) so if someone can point me where I can start to learn I would appreciate it!...[/QUOTE]

There is one simple fact with Ubuntu, you don't have to use the command line very often; Ubuntu includes many gui based tools to help you.

The place to start, I think, is the [Unofficial Ubuntu 5.04 Starter Guide]("http://ubuntuguide.org/"); I know this is the '5.04' version and you are probably running 5.10, but most of the advice still relates (repositories is probably the main difference as their name changes for Breezy).  This is a great source of information.

The other thing that has helped me more than anything is I started to keep a diary/note book of all the things I did.  Running apt-get and dpkg package management utilities are the first entries.  The other early difficulty (after using other distros) was the use of 'sudo' rather than 'root'.  This was particularly difficult at the start but now I think it is great and is a key part of 
what makes Ubuntu much easier than other distros to manage.

One thing that has changed with Breezy is the lack of a "Run" option on the 'Applications' menu.  This can be overcome either by using the [Alt] + [F2] keyboard short-cut (which brings up the "Run" dialog) or by inserting a button on the Task/Menu bar.

The other on-going problem I have is trying to understand the Linux directory heirarchy and where applications are put (the Linux equivalent of C:\Program Files) but I guess this is just time and patience and eventually it will come.

Installing modems and printers has also been a major headache, but now I have ADSL broadband (which requires no setup) and I recently purchased a Samsung laser printer which includes Linux drivers (shame about my nice and expensive Canon laser which did not).

I am happy to share any of my limited experiences.

Regards,
Peter  :D 
pjafrombbay[at]yahoo.com.au

---

### Post by mcmillan on 2005-11-19
While you don't need to use the CLI for a lot of things, it is really good to learn. The starter guide is a good place to start, since a lot of what's on there requires som command line. At least in Hoary the terminal is under system tools in the applications menu. I think it's also in the toolbar by default, but I may have added that myself (I can't remember). There's also a few guides I've come across that seem really helpful. The only one I've really gone through was [Getting Started with Linux]("http://www.linux.org/lessons/beginner/toc.html") I think it's pretty good, though it is a bit advanced, with a lot of emphasis on using the command line over doing much of anything with the gui. But it's a good place to learn how to do a lot. The rest I haven't really had time to look at too carefully, but have seen recommended on forums a lot. I just haven't had much time to really go through them since school started. 

[Rute]("http://rute.2038bug.com/index.html.gz") looks really through, maybe a little too through, but it seems like it would be a reference for future use.

[Linux Newbie AdministratorGuide]("http://linux-newbie.sunsite.dk/") It's written from the point of view of someone working with Red Hat or Mandrake, but a lot seems applicaple for all distros

[Ultimate Linux Newbie Guide]("http://www.linuxnewbieguide.org/index.php") I just found this a couple days ago, it's not real in depth compared to the others, but it seems like a good place to get started.

[Linux Knowledge Base and Tutorial]("http://www.linux-tutorial.info//modules.php?name=Tutorial&pageid=224") Another tutorial that seems like it will cover a lot of material that would be good to know. 

Hope this helps with some sources for information

---

### Post by Boca on 2005-11-19
mcmillian and pja, thx for the replies ,links and encouragement!! 
I've been rooting around and finally found 'Terminal. Also figured out how to change my boot order since I have to use XP for my work. 

Just found out my Canon ip3000 isn't listed in the drivers so[ found some]("http://tinyurl.com/bb65o") that I downloaded to my desktop. They are .rpm files so have to figure out how to install them. 

I figured out how to mount a fat32 partition that I use with XP so I'm learning quite a bit today. So far, I'm liking what I see with Ubuntu:)

---

### Post by aysiu on 2005-11-19
[QUOTE=Boca]Thx for the help so far! I'm just about ready to install but am pondering whether or not to install GRUB in the MBR. [/quote] There's no reason not to install Grub to the MBR.

1. Ubuntu's bootloader (Grub) will recognize Windows and add it automatically to the boot menu.
2. Windows' bootloader will definitely never recognize Ubuntu, and even if it didn't, would not add Ubuntu to the boot menu.
3. Even if you really screw things up, there's a way to restore Windows' bootloader to the MBR (it's a command in Windows called fixmbr that you do from recovery mode).

> 
This site, [http://users.bigpond.net.au/hermanzone/p2.htm]("http://users.bigpond.net.au/hermanzone/p2.htm") says he hasn't had any problems doing that while this site, This site is a work of genuis.

> [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/]("http://www.crhc.uiuc.edu/%7Emjmille2/howtos/dual-boot-linux-and-windows/") says not to do it and set up XP to handle the dual booting.  This site is a well-intentioned piece of crap that makes people think doing a dual boot is more complicated than it really is.

---

