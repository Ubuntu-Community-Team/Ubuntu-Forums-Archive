---
title: "Installing Ubuntu...."
date: 2005-05-19
forum: Absolute Beginner Talk
---

### Post by SRXy on 2005-05-19
Hi all...I'm a total Linux newbie and would like some assistance.

I would like to install Ubuntu on my PC. I'm currently running XP on one HD and would like to know how to install Ubuntu onto a seperate HD and have it boot from there...is it possible? I would like to keep XP....my fiance is not to keen to make the switch!

Please help

---

### Post by Zelut on 2005-05-19
[QUOTE=SRXy]Hi all...I'm a total Linux newbie and would like some assistance.

I would like to install Ubuntu on my PC. I'm currently running XP on one HD and would like to know how to install Ubuntu onto a seperate HD and have it boot from there...is it possible? I would like to keep XP....my fiance is not to keen to make the switch!

Please help[/QUOTE]
 You can run a dual-boot system, sure.  Its really pretty easy.

When you boot from the ubuntu install CD it'll ask you about the drives & partitions you want it installed to.  It should sense both of your HDDs so you can tell it to install to the second HDD.  This will, of course, erase any information you have on the second drive so make sure you have anything backed up.

ubuntu will then install a program called GRUB which will allow you to select which operating system you want to boot to.  It will probably default to ubuntu but you can fix that easily as well.  If you need any more help...

---

### Post by SRXy on 2005-05-19
who...that was quick!!! Thanks. It'll be a completely virgin HDD, so there won't be any data to worry about getting erased.  Cool thanks

---

### Post by zenlord on 2005-05-19
[QUOTE=SRXy]who...that was quick!!! Thanks. It'll be a completely virgin HDD, so there won't be any data to worry about getting erased.  Cool thanks[/QUOTE]
 Before you proceed: The Ubuntu-installer should detect your previous Windows-installation. If it does not list all of your other OSses, you should not proceed! I installed Ubuntu for the first time this week, and all went perfect!

Also: let GRUB install itself in the MBR on the first (windows-)HD. If you should wish to delete linux entirely, it is as easy as fdisking/formatting the second hard drive and doing a /fixmbr on the first HD!!

Zl.

---

### Post by Zelut on 2005-05-19
The ONLY part of the ubuntu installation that I find not so user-friendly is the section on partitioning & installing GRUB.  If you've done it before & you're familiar with it it isn't so much of a problem but for newbies it can seem daunting.

It will ask you where you want to install the GRUB loader.  I always install it to the MBR (master boot record) but some people don't like doing this.  Its up to you but that is what I suggest.  The reason some people are reluctant is because if the MBR is corrupted it wont allow you to even boot into windows (but it can be fixed, don't worry).

the installation defaults should work fine for what you're needing.  Just tell it to install to the second drive, install to MBR & you should be A-OK.

---

### Post by shador on 2005-05-19
[QUOTE=kuyaedz]The ONLY part of the ubuntu installation that I find not so user-friendly is the section on partitioning & installing GRUB.  If you've done it before & you're familiar with it it isn't so much of a problem but for newbies it can seem daunting.

It will ask you where you want to install the GRUB loader.  I always install it to the MBR (master boot record) but some people don't like doing this.  Its up to you but that is what I suggest.  The reason some people are reluctant is because if the MBR is corrupted it wont allow you to even boot into windows (but it can be fixed, don't worry).

the installation defaults should work fine for what you're needing.  Just tell it to install to the second drive, install to MBR & you should be A-OK.[/QUOTE]
 When do u get to choose where to install GRUB? I've installed Ubuntu a couple of times and the only option i've seen with GRUB is if you want to install it or not. At the far end of the CD installation

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=SRXy]I'm currently running XP on one HD and would like to know how to install Ubuntu onto a seperate HD and have it boot from there...is it possible?[/QUOTE]


Thats how I do it. Two things:

A. Make sure Windows is installed first

B. Make sure the Ubuntu install CD does not  install over the window's drive. It defaulted to format the primary drive with the default settings. Tell it no when it wants to write changes to disk the first time and make sure that Ubuntu isn't nuking your XP install. I had a friend that couldn't get them to work together, and when I went to his house to find the problem I discovered that he just kept hitting enter during the Ubuntu install and he nuked his windows drive instead of the one meant for Ubuntu. Unfortunately I can't give you exact directions how to do it, but if you have more questions please ask them.

For teh record, I've never had a problem with the grub.

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=kuyaedz]
the installation defaults should work fine for what you're needing. [/QUOTE]

No, not really. The Ubuntu install default in most cases will want to erase the Windows drive.

---

### Post by SRXy on 2005-05-20
erm...now you've got me worried. Is there anywhere I can get a series of screen shots to show what to expect during the install. I'd like to be fore-armed, if you know what I mean. 

I'd REALLY hate to format the primary drive, so I'd like to get an idea of the options I'll be faced with during the install

Thanks

---

### Post by Zelut on 2005-05-20
[http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

That site has some screen shots on the installation so you shouldn't come to any surprises.  Those screenshots aren't for a dual-boot installation but it'll still give you some idea.

When you get to the screen on partitioning (screenshot #7) yours should list two HDDs.  If you select the second one you should have nothing to worry about.  Just make sure you take your time and read everything.  It's not a race  :grin: 

If you have more questions feel free to let me know.  If you can catch me while I'm online I'd be willing to walk you thru via IM if that makes you more comfortable :)

---

### Post by SRXy on 2005-05-20
Thanks for the info...I'll be installing this weekend when my new HD arrives.  I'm still unclear where I chose where to install grub....

---

### Post by poofyhairguy on 2005-05-20
[QUOTE=SRXy]Thanks for the info...I'll be installing this weekend when my new HD arrives.  I'm still unclear where I chose where to install grub....[/QUOTE]


DO you plan to dual boot? I suggest the default in that case.

---

