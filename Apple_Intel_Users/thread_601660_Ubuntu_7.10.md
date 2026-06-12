---
title: "Ubuntu 7.10"
date: 2007-11-03
forum: Apple Intel Users
---

### Post by shavital on 2007-11-03
First contact with Linux, Mac user since 1994. Running now Tiger, planning to upgrade to Leopard next week, wish me luck and I welcome tips related to Parallels under Leopard.
After installing Parallels and Windows XP Pro, installed Ubuntu 6.06 to learn basics, erased it and tried to install 7.10, didn't succeed. 
Installed 7.04 and upgraded to 7.10 (from within 7.04), now running fine. 
Upgraded GnuPG 1.4.6 (that came with the distribution) to 1.4.7. Imported my keyrings from OSX. Have enabled gpg-agent for installed gpg2 2.0.4. I welcome information from gpg users who have compiled gpg 2.0.7, on top of 2.0.4.
Linux is amazing.
Questions:
- till now I have used i386 releases. Is this the right choice for my Macbook (information in signature)?
- haven't succeeded to set printing. I use an HP 1305 wired to an iMac (Panther) in an in-house LAN. No problem printing from any machine in the LAN (this Macbook and a PPC Powerbook).
- Ubuntu 7.10 is running on kernel 2.6.22-14-generic. I have read that the current stable kernel is 2.6.23.1. I have tried to build the current release, but made some mistakes, and it didn't compile. Since it's a long process, is there any advantage, in terms of Ubuntu's performance, to build and install that kernel?

---

### Post by cyberdork33 on 2007-11-03
> **shavital said:**
> First contact with Linux, Mac user since 1994. Running now Tiger, planning to upgrade to Leopard next week, wish me luck and I welcome tips related to Parallels under Leopard.
After installing Parallels and Windows XP Pro, installed Ubuntu 6.06 to learn basics, erased it and tried to install 7.10, didn't succeed. 
Installed 7.04 and upgraded to 7.10 (from within 7.04), now running fine. 
Upgraded GnuPG 1.4.6 (that came with the distribution) to 1.4.7. Imported my keyrings from OSX. Have enabled gpg-agent for installed gpg2 2.0.4. I welcome information from gpg users who have compiled gpg 2.0.7, on top of 2.0.4.
Linux is amazing.
Questions:
- till now I have used i386 releases. Is this the right choice for my Macbook (information in signature)?
- haven't succeeded to set printing. I use an HP 1305 wired to an iMac (Panther) in an in-house LAN. No problem printing from any machine in the LAN (this Macbook and a PPC Powerbook).
- Ubuntu 7.10 is running on kernel 2.6.22-14-generic. I have read that the current stable kernel is 2.6.23.1. I have tried to build the current release, but made some mistakes, and it didn't compile. Since it's a long process, is there any advantage, in terms of Ubuntu's performance, to build and install that kernel?

Not using gpg, so can't help you with that.

you can use 32bit or 64bit releases on core2 cpus. I recently upgraded to using 64bit (AMD64 version) with Gutsy 7.10 since they have worked out most of the compatibility issues.

I always found printing from Ubuntu or windows to a printer shared on a Mac a big pain. It was my understanding the 7.10 can see bonjour shares now, so I really don't know why you are having problems. May need to provide some more information. What protocols are you sharing with? How have you attempted to add it to Ubuntu? I recently got a network connected HP printer so that I didn't have to deal with sharing issues.

No real need for upgrading the kernel. Ubuntu will periodically release new kernel builds. If you would like to try the latest, there is a tutorial in the FAQ for accomplishing this.

---

### Post by shavital on 2007-11-03
> **cyberdork33 said:**
> 
you can use 32bit or 64bit releases on core2 cpus. I recently upgraded to using 64bit (AMD64 version) with Gutsy 7.10 since they have worked out most of the compatibility issues.

I'll try it.

I always found printing from Ubuntu or windows to a printer shared on a Mac a big pain. It was my understanding the 7.10 can see bonjour shares now, 

That was the first option I searched for, but couldn't find it.

so I really don't know why you are having problems. May need to provide some more information. What protocols are you sharing with? How have you attempted to add it to Ubuntu? I recently got a network connected HP printer so that I didn't have to deal with sharing issues.

I have tried, by all available options, to add a printer. Used, without success:
- Current device: Host name [the host name of the iMac that has the printer hardwired[ and the default port offered: 9100
- samba: used what I believed to be the correct settings, but result is 'Printer unaccessible', whether I use, or not, a user name and a password.
- AppSocket/HP JetDirect. Nothing
- IPP- no queues found.
- LPD/LPR - nothing
This printer, although located in a LAN, has no IP Address.

No real need for upgrading the kernel. Ubuntu will periodically release new kernel builds. If you would like to try the latest, there is a tutorial in the FAQ for accomplishing this.

Yes, I followed the tutorial, and everything seemed to progress fine, until I goofed somewhere in the cli. After more that 5 hours at it, I really didn't feel like starting anew. Maybe I'll do that later, if Ubuntu does not releases a new kernel build any time soon, I'm not really in a hurry.. What occupies me now is "to brace myself" towards Leopard. I am not overly concerned, because I remember almost identical situations when upgrading to Panther, Tiger. 

Thank you for your feedback.

---

### Post by cyberdork33 on 2007-11-04
> **shavital said:**
> Yes, I followed the tutorial, and everything seemed to progress fine, until I goofed somewhere in the cli. After more that 5 hours at it, I really didn't feel like starting anew. Maybe I'll do that later, if Ubuntu does not releases a new kernel build any time soon, I'm not really in a hurry.. What occupies me now is "to brace myself" towards Leopard. I am not overly concerned, because I remember almost identical situations when upgrading to Panther, Tiger. 

Thank you for your feedback.
What tutorial were you following ? There is a lot of outdated info out there now.

---

### Post by shavital on 2007-11-04
> **cyberdork33 said:**
> What tutorial were you following ? There is a lot of outdated info out there now.

I'm answering here from a different laptop, while I'm upgrading my Intel laptop to MacOSX 10.5 (Leopard), I can't access for the time being the information I need in order to reply to your question.

I don't remember the specific name of the thread I used (it really had a specific name). I'll answer as soon as possible.

---

### Post by cyberdork33 on 2007-11-04
> **shavital said:**
> I'm answering here from a different laptop, while I'm upgrading my Intel laptop to MacOSX 10.5 (Leopard), I can't access for the time being the information I need in order to reply to your question.

I don't remember the specific name of the thread I used (it really had a specific name). I'll answer as soon as possible.
That's ok. With leopard the process is a bit easier!

---

### Post by shavital on 2007-11-04
> **cyberdork33 said:**
> That's ok. With leopard the process is a bit easier!
Now on the Intel machine, after completing its upgrade to Leopard (using the 'Nuke and Pave' method).
1. The name of the kernel upgrade thread is Master Kernel Thread, Kernel.org Information.
2. But I believe this is now irrelevant. After I got Ubuntu booted and working (with a warning that I am sending to the Ubuntu team, it's a screen shot), I stopped the machine and rebooted in recovery mode. Among all the kernel options available, there was 2.6.23.1, which I selected. The system monitor indicates that, indeed, the kernel version is 2.6.23.1.
Well, so much for upgrading to Leopard, and thanks to the Ubuntu team for releasing the new kernel.

---

### Post by rutty on 2007-11-04
I'm trying to install Gutsy with a trial copy of Parallels in Leopard on my new iMac. The install conks out when it tries to launch a display server - it crashes 6 times and says something bad has happened (no kidding!).

As much as I like the look of Leopard I really don't want to lose track of Ubuntu - I feel like a traitor to the OS as it is! If you have any links to a recent procedure I'd be very interested

Hope it goes well with your try ;)

---

### Post by shavital on 2007-11-04
> **rutty said:**
> I'm trying to install Gutsy with a trial copy of Parallels in Leopard on my new iMac. The install conks out when it tries to launch a display server - it crashes 6 times and says something bad has happened (no kidding!).

As much as I like the look of Leopard I really don't want to lose track of Ubuntu - I feel like a traitor to the OS as it is! If you have any links to a recent procedure I'd be very interested

Hope it goes well with your try ;)

I am a newbie of 5 days to Ubuntu, and had the same problem when I tried to install Gutsy.

1. If you have assigned more than 512MB memory to the virtual machine, that could be the cause of your problem.

2. When you are in Parallels, and can see the graphic panel that displays the configuration of the virtual machine:
- if it says running or suspended, or anything that is not 'stopped', use the Action command to actually stop the virtual machine.
- click the start green triangle, and as soon as the graphic panel starts to rotate, press and hold the 'escape' key, until a black display with white letters shows. This is the procedure to reboot the virtual machine in recovery mode.
- if everything goes well, you should get a display where different booting options are available, each option being a kernel version. If the first option is kernel 2.6.23.1, select it (using the arrows keys in your keyboard), and then hit the Return key. This should make Ubuntu 7.10 boot using that kernel version, which is the current stable version.
- if you don't get 2.6.23.1,, try the option kernel 2.6.22-14-generic recovery mode, and hope for the best.

Again, I am a newbie, I'm just summing up what can be read in the forum's posts.

Good luck

---

### Post by rutty on 2007-11-04
Cheers for the tips - I've only ever tried Parallels for a few hours so still finding my feet.

I've managed to get it working - of a sort. It's in Vesa crap graphics mode but it's up!

I followed the instructions here:

[http://infosonic.wordpress.com/2007/10/21/ubuntu-710-install-guide-parallels-macbook-pro/](http://infosonic.wordpress.com/2007/10/21/ubuntu-710-install-guide-parallels-macbook-pro/)

There are some good pointers in the comments. I've got a bit of playing around to do to get it working how I want ;)

It's fun to try if nothing else!

---

### Post by shavital on 2007-11-05
> **rutty said:**
> Cheers for the tips - 
[...]

It's fun to try if nothing else!

You're welcome, thanks for the pointer, and yes, it's fun to try.

---

