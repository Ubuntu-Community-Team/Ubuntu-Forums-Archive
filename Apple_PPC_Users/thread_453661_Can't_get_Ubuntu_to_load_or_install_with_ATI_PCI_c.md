---
title: "Can't get Ubuntu to load or install with ATI PCI card in- WHY???"
date: 2007-05-24
forum: Apple PPC Users
---

### Post by joshjani on 2007-05-24
Sorry if I keep posting the same question, but I cannot get Ubuntu to even start the install process if I have a PCI ATI Rage 128 card in the system. 
 
Beige G3 (Old World) 350mhz CPU clocked to 400, 320mb RAM 40g IDE drive

Ubuntu installed fine when using internal video- but I could only get 800x600, which is next to useless on a 17" monitor. So I got a Mac ATI Rage128 and popped it in. MacOS works fine on it. Couldn't boot to Ubuntu. If I remove the card, Ubuntu goes fine.

I can't reconfigure xorg, because I can't get to Linux. So I decide to start from scratch and do the whole install process again, with the card in this time. Nothing doing- I can't even get the install to start.

If I check the "no video" option in BootX, I get a line of garbled green at the top of the screen. I can't read it, so I restart- but only back to MacOS. Unchecking the "force video" has no effect, either. As I write this, I've been watching what happens as I try to start Ubuntu- basically nothing for 3 minutes, then a reboot back to MacOS.

MacOS9 is useless to me- I really want to run Ubuntu. Could anyone PLEASE provide some info on how I get this to happen, WITH the ATI card in place? Otherwise, I'm Ebaying all the parts I can salvage and giving up.

---

### Post by stmiller on 2007-05-24
What version of Ubuntu? Try Feisty, the latest version if you aren't already. You may have to install with the alternative CD which goes right to an installer, and bypasses using X.

I'm not familiar with BootX but there's a way to boot into single user mode (no X) to edit and get your /etc/X11/xorg.conf file all set in the console, and then reboot to see if it works.

There are log files you can view by doing this:

$ sudo less /var/log/Xorg.0.log

$ sudo less /var/log/messages

$ sudo less /var/log/syslog

and look for any radeon or display errors which may help diagnose what's going on.

---

### Post by joshjani on 2007-05-24
> **stmiller said:**
> What version of Ubuntu? Try Feisty, the latest version if you aren't already. You may have to install with the alternative CD which goes right to an installer, and bypasses using X.

I'm not familiar with BootX but there's a way to boot into single user mode (no X) to edit and get your /etc/X11/xorg.conf file all set in the console, and then reboot to see if it works.

There are log files you can view by doing this:

$ sudo less /var/log/Xorg.0.log

$ sudo less /var/log/messages

$ sudo less /var/log/syslog

and look for any radeon or display errors which may help diagnose what's going on.

Thanks for the reply- I have to use bootX because the G3 I'm running is Old World and cannot boot from the Ubuntu CD. The version I am using is 6.06 Alternate install. I tried Xubuntu 7.04, but it never made it to the install screen. I may have been doing something wrong at that point, though, so I'll try it again.

I may buy a VRAM module for this thing, too, and just up the onboard video to 6MB. That should give me the ability to do 1024x768, right?

---

### Post by stmiller on 2007-05-24
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

Have you read through this page? Might have some hints to get the installer going on an old world mac. From there we can troubleshoot to get that video card going after it's installed.

---

### Post by joshjani on 2007-05-24
> **stmiller said:**
> [https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

Have you read through this page? Might have some hints to get the installer going on an old world mac. From there we can troubleshoot to get that video card going after it's installed.

OH YES!!! that page has been burned into my monitor!


I took the card out, install is now proceeding. I think I'm just going to get a VRAM module and see if that helps for screen resolution.

JC

---

### Post by joshjani on 2007-05-24
Actually, now that I'm looking, I'd have to spend more $$ for that vram module (4mb) than I did for the ATI Rage 128 16mb!

But I'm very confused by this. The Mac already has ATI video built in, and I really thought Ubuntu would just see the new ATI card, use the ATI drivers I presumed it was already using, and away we go. But as soon as I put the card in, I cannot boot to Ubuntu. Once again, Mac OS runs just fine, so I know it's not the hardware.

Are there kernel arguments I can use in the bootX dialog to make this card work? Is Ubuntu Dapper missing some ATI stuff? Since I can gt this running without the card, what do I have to do to add the card once I get a good installation?

---

### Post by stmiller on 2007-05-24
I can help you, if you give me more info. When you say it doesn't boot, where does it stop? Does the kernel start loading, and the it freezes? Does it seem to boot up entirely but doesn't start X?

Can you get to a console and post the logs here?

What is your /etc/X11/xorg.conf? etc, etc.

---

### Post by joshjani on 2007-05-25
> **stmiller said:**
> I can help you, if you give me more info. When you say it doesn't boot, where does it stop? Does the kernel start loading, and the it freezes? Does it seem to boot up entirely but doesn't start X?

Can you get to a console and post the logs here?

What is your /etc/X11/xorg.conf? etc, etc.

Well, the biggest problem I have is that it doesn't seem to even START booting to linux. I think the kernel starts loading- I can hear the CD spin up, but something happens very early in the process that hangs me up before the MacOS screen even disappears. I know you wrote that you weren't familiar with BootX- it's an app that lets me boot from MacOS9 to Linux. It runs as an extension or as an app in the Apple menu.

So, I boot to OS9, run BootX with the vmlinux and initrd files from whatever install CD I'm using, and I'm supposed to get to the install screens, follow the procedure, and have a dual boot system at the end of the day. I know it works- I've done it! 

BUT- if that stupid card is in there, I get nowhere- not even far enough to drop to a shell and read any logs, enter any commands, etc. Take the card out, and I'm back, but only at 640x480 or 800x600. And only at 640x480 on the mac side.

I can enter kernel arguments in BootX before I boot to Linux, so I'm hoping there's something that I can type there that will allow for the PCI card through the installation until Ubuntu can detect and load drivers.

Right now I'm starting from scratch yet again, this time reformatting and writing zeros to my drive. I'm going to install for the time being with no ATI PCI card in, get a good install, and then attempt to put the card in the system.

Thanks for the offer of help. I'm getting ready to give up, as I don't really have a use for this machine when I get it going! But it's a mountain to climb, now- I have to do it just 'cause it's there!

Thanks-
JC

---

### Post by stmiller on 2007-05-25
JC:

I could help you, but you will have to post the /etc/X11/xorg.conf file from your install here on the forum. You have to give us more specific details and log files so we can figure out what is wrong. The logs we need are the ones I have posted on this thread. If you give us those, I can tell you what is possibly going wrong. Linux makes log files of boot time and retains any errors. So post those logs if you need help!!

---

### Post by joshjani on 2007-05-25
> **stmiller said:**
> JC:

I could help you, but you will have to post the /etc/X11/xorg.conf file from your install here on the forum. You have to give us more specific details and log files so we can figure out what is wrong. The logs we need are the ones I have posted on this thread. If you give us those, I can tell you what is possibly going wrong. Linux makes log files of boot time and retains any errors. So post those logs if you need help!!

Thanks for the help- but it's a moot point, now. I had to give up! All of a sudden I wasn't able to install OS9, either. No matter what I did, I kept getting a message at boot that there was no bootable hfs partition. So I put all the original parts back in, installed OS9, and plan to take the whole thing to Goodwill as a donation. The 40gb drive I was trying to use in it functions just fine as a storage drive for my XP/UbuntuStudio machine, and I'll have some parts on eBay soon!

---

