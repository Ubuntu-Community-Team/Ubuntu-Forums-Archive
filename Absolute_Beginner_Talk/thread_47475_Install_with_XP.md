---
title: "Install with XP"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by Boat on 2005-07-08
I have an XP laptop and I want to install Ubuntu in a dual boot setup. I was looking for some documentation to step me through the process of shrinking my windows partition and setting up the partitions needed for Ubunto. Can anyone point me to some documentation that might make the process a little easier?

---

### Post by Snitz on 2005-07-08
[QUOTE=Boat]I have an XP laptop and I want to install Ubuntu in a dual boot setup. I was looking for some documentation to step me through the process of shrinking my windows partition and setting up the partitions needed for Ubunto. Can anyone point me to some documentation that might make the process a little easier?[/QUOTE]
 I would like to know too
I'm running winxp right now and I wanna install ubunto after I test it on "vmware"
but how can I set the corret partitions so I don't mess with my winxp nor my other drive (D:\)
I, mainly wanna install ubunto on c:\ on the same drive that winxp is installed on..

is it possible?

---

### Post by aysiu on 2005-07-08
Dual-booting is not the same as installing Ubuntu on C:\, which isn't really possible unless you're using Qemu or VMWare. Dual-booting means there are at least two partitions--one for Windows (C:) and one for Ubuntu (which will be in a completely different filesystem format--ext3).

I wrote up a little guide for Windows to Linux users that includes a part about partitioning and dual booting. Let me know if you find it helpful... or don't.

[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

---

### Post by AlexDe on 2005-07-08
Just use something like Parition Magic, resize the windows parition, then with the new space install Ubuntu.

---

### Post by aysiu on 2005-07-08
[QUOTE=AlexDe]Just use something like Parition Magic, resize the windows parition, then with the new space install Ubuntu.[/QUOTE] Mandriva and Mepis also have great graphical installers (and they're free).

---

### Post by Boat on 2005-07-08
[QUOTE=aysiu]Dual-booting is not the same as installing Ubuntu on C:\, which isn't really possible unless you're using Qemu or VMWare. Dual-booting means there are at least two partitions--one for Windows (C:) and one for Ubuntu (which will be in a completely different filesystem format--ext3). [/QUOTE]

I thought that I could repartition and create the needed new partitions right from within the Ubuntu installer on expert mode? It's sort of amazing that there is no written guide for Linux newbees to walk them thru an installation on an XP computer. Just confirms my suspicion that Linux is not ready for prime time.

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=Boat]I thought that I could repartition and create the needed new partitions right from within the Ubuntu installer on expert mode?[/QUOTE]

You can resize NFTS with the Ubuntu installer.

> 
It's sort of amazing that there is no written guide for Linux newbees to walk them thru an installation on an XP computer. 

How is that amazing? No one has written such a thing, but seeing as how ALL of the documentation is made by volunteers (like me) the lack of anything shouldn't be amazing.

> 
Just confirms my suspicion that Linux is not ready for prime time.

Just so you know...comments like that don't help you. I know how to do what you want....but now I don't want to tell you.

---

### Post by poofyhairguy on 2005-07-09
I can't be a dick even if I try. The guide you want exists here:

[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by aysiu on 2005-07-09
I know Poofy isn't going to be a dick, but I am. People try to help you and geez...
[QUOTE=Boat]It's sort of amazing that there is no written guide for Linux newbees to walk them thru an installation on an XP computer.[/QUOTE] Translation: I'm too lazy to do [a Google search](http://www.google.com/search?hl=en&q=dual+boot+xp+linux+partitioning&btnG=Google+Search) for one. Considering you probably didn't even look at the link I gave you before, it doesn't surprise me. Does "primetime" mean you?

---

### Post by parabellum on 2005-07-09
[QUOTE=aysiu]I know Poofy isn't going to be a dick, but I am. People try to help you and geez...
 Translation: I'm too lazy to do [a Google search](http://www.google.com/search?hl=en&q=dual+boot+xp+linux+partitioning&btnG=Google+Search) for one. Considering you probably didn't even look at the link I gave you before, it doesn't surprise me. Does "primetime" mean you?[/QUOTE] :lol:

---

### Post by brim4brim on 2005-07-09
[QUOTE=Boat]I have an XP laptop and I want to install Ubuntu in a dual boot setup. I was looking for some documentation to step me through the process of shrinking my windows partition and setting up the partitions needed for Ubunto. Can anyone point me to some documentation that might make the process a little easier?[/QUOTE]
 Okay I did this and it's really so simple I'm surprised there is a walkthrough for it as it's common sense once you know anything about partitions.

You simply resize your NTFS partition so that you have enough free space for Linux using a tool such as partition magic.  Now the space you've set aside for Ubuntu should not be formatted to any partition and just left as free space.

Now reboot and boot from the cd drive with ubuntu install disc in and follow the install procedure until you get to partitioning.  Because you initially left free space there will be an option in the menu for automatically assigning part of it as swap and the rest as the actual Linux partition and you just select that and the rest of the installation is pretty much automatic.

See how simple that is.  I recommend partition magic because it's the one I used,  there are several tools and if you want you can use the software at the point of setting up partitions in the installation of ubuntu.  It doesn't provide a modifiable graphical representation as far as I know, you just enter the space to set aside and then go back out to the initial menu and let it automatically decide the best size for your swap and other parition and it'll install fine.

---

### Post by Boat on 2005-07-09
[QUOTE=aysiu]I know Poofy isn't going to be a dick, but I am. People try to help you and geez...
 Translation: I'm too lazy to do [a Google search](http://www.google.com/search?hl=en&q=dual+boot+xp+linux+partitioning&btnG=Google+Search) for one. Considering you probably didn't even look at the link I gave you before, it doesn't surprise me. Does "primetime" mean you?[/QUOTE]

Actually I did search all over the Ubuntu site for something and then I asked on this list for someone to point me in the right direction. I read the entire piece you sent but although helpful, it is not what I was looking for and was not specific to Ubuntu. 

I'm not the enemy here. I'm a guy looking to install linux and finding it harder than I think it should be. I started the install using expert mode and even the choice of language and locale leads to options with no clear meaning as to which is the correct choice. 

I'd love to see Linux suceed but if someone like me, who has been computing for years and builds his own rigs, can't find a simple way to install it or even detailed directions, how is it ever going to gain wide acceptance? I apologise if I ruffled some feathers with my injudicious "prime time" comment but the problems I'm experiencing along with the problems installing modems, some video cards and other hardware tend to support my contention. 

Again,  I recognize that folks here are volunteers and I appreciate the help.

---

### Post by UbuWu on 2005-07-09
A nice install guide with screenshots: [http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

---

### Post by aysiu on 2005-07-09
[QUOTE=Boat]Actually I did search all over the Ubuntu site for something and then I asked on this list for someone to point me in the right direction. I read the entire piece you sent but although helpful, it is not what I was looking for and was not specific to Ubuntu.[/quote] Can you tell us exactly what you're looking for? You have to understand that things like setting up partitioning and a dual-boot are not Ubuntu-specific instructions. They can be done with almost any Linux distribution. If you like graphical partitioners, you can use Mepis' QTParted or Mandriva's [DiskDrake](http://www.easylinux.de/Artikel/ausgabe/2005/02/078-deinstallieren/winpart.png). I use only Mepis and Ubuntu distributions for desktop use, but I always use Mandriva's partitioner. 

> I'd love to see Linux suceed but if someone like me, who has been computing for years and builds his own rigs, can't find a simple way to install it or even detailed directions, how is it ever going to gain wide acceptance? What are rigs? I don't consider myself a computer genius at all, but I've learned Linux. There are a couple of things you have to understand. First of all, most issues people encounter with Linux have to do with installation, and most users don't ever install Windows. Windows comes pre-installed. If you buy a pre-installed, pre-configured Linux computer, you probably won't have to worry about partitioning or finding drivers for video cards, etc.

I also happen to like Ubuntu a lot, but if you like more GUI configuring, I'd definitely recommend Mepis.

---

### Post by slade_slater on 2005-07-19
Linux has never been more ready for primetime than it is now.  And that being said, if you need a good graphical installer to resize partitions, qtparted is one answer-you can obtain it (as stated earlier) by using a Mepis live CD, or if you don't want to download 700 MB go to [http://www.sysresccd.org/](http://www.sysresccd.org/) and download their system rescue CD.  It will boot up in console, then you type something like run_qtparted and it will ask you a few questions and fire it up.  I have used this to resize my laptop many times in my never-ending quest to find the perfect distribution (seeing as Ubuntu is about the only one that will detect the majority of its hardware, I've finally settled for Hoary, which is probably one of the best distros IMHO).  Just so you know I figured it out (as stated earlier) with google.  Sometimes all it takes is a little web savviness (sp?) to figure out what you need.  Linux may be primarily volunteer-based, but the community is very good about documenting their problems/fixes.  Also you can't come into the world of Linux and expect it to behave exactly like Windows (and frankly, who would want it to do so?).  They are two different creatures.  That doesn't make linux harder or less 'ready,' rather it makes it just different.  Approach it with an open mind and I think you'll find it a refreshing and viable alternative to other operating systems...  [....end sermon.....]   :grin:

---

### Post by Lord Illidan on 2005-07-19
I have been trying to use Linux for two years now, always finding some problems. I won't say that Ubuntu hasn't got its share of problems, but it is the best distro available.
Also, realise that when people ask for help, they ask nicely....so don't repeat that primetime comment..

Linux is not going to be easy if you are new from the Windows world, so take it as a challenge. I thought I was a pc genius when I took the A+ cert. at 13, but I was humbled when I realised that I could not understand anything about Linux..

Now, at the age of 16, I am using Linux as my primary OS..and the terminal is my friend...

---

### Post by lotusleaf on 2005-07-20
[QUOTE=Boat]I'm not the enemy here.[/QUOTE]

Do you work for Microsoft?

---

