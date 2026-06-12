---
title: "Can you install while running Ubuntu?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-01-07
Didn't see any posts that seemed to cover this, so here goes with what is probably a dumb question:

I currently run Ubuntu dual-boot with an old copy of Win98SE off a 10gig drive - 4 gig for Windows, 6 (including swap) for Ubuntu 7.10.  I just added a 80gig drive physically to the system, and what I would like to do is install Feisty to that drive.  I still have the Feisty LiveCD, so is there a way while running Gutsy to start the installation process off the LiveCD, or is the only choice I have to boot the LiveCD?  It's not that big of a deal either way around, but I am curious!:)

Thanks in advance!:)

---

### Post by Xavieran on 2008-01-07
I'm pretty sure that you have to run the Live disc to install it...

---

### Post by bodhi.zazen on 2008-01-07
Naw, you can install using chroot :

mount the new partition.

Install with chroot

chroot into the new /

sudo apt-get install ubuntu-desktop

Install grub and a kernel

reboot

[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

You do not need to "set up" the chroot, just install it and then install a kernel, grub, and ubuntu desktop.

You can also install from the .iso : 

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) (see the section on "no CD")

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

	[http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive](http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive)

[http://ubuntuforums.org/showthread.php?&t=316093](http://ubuntuforums.org/showthread.php?&t=316093)

---

### Post by anewguy on 2008-01-07
I appreciate the knowledge as I assume others will as well!

I did decide to take a slightly different route - I *THINK* I'm getting another computer - not new, but newer than what I've got right now.  So, I downloaded the server version and plan to try that so I have a file/print server and a "normal" install on the other.  Thing is, I know bubcus about any of it, so I guess I'll need to do some reading and just play with it to see if I can get it going.  What the heck - I'll still have my normal install I'm running now on the 10gig drive, so at least I won't be without a computer.

So, for a big question, just where the heck should a guy start once he has downloaded the installation CD for the server?  Where do I find information that can explain in some pretty basic terms the general ideas and then the details?

Thanks so much, everyone!  You're fantastic at this stuff!:)

---

### Post by bodhi.zazen on 2008-01-08
Well, a server install has no GUI, so start with familiarizing yourself with the CLI (ie terminal) and bash commands. You can install server software on your desktop and learn to set up servers from just the CLI.

Next you can either install the server version or play with in in VMWare / VBox

See also : [http://ubuntuforums.org/showthread.php?t=193305](http://ubuntuforums.org/showthread.php?t=193305)

Also look at how to secure the servers you want to install, like say ssh :

[uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by anewguy on 2008-01-08
Thanks, Bodhi.  I now have some place to start.  Used the command line YEARS ago when we had 2 Unix boxes at work besides the big mainframe that was my baby.  But, never had to set up a server.  All we really did was a few things to hosts file and a couple of others but nothing as an actual server.  This will give me something to learn with.  BTW - can I also install either KDE or gnome desktop in server, and will it have X support or is that why I would be limited to the command line?

Thanks again - you really rock at this stuff!:)

---

### Post by hyper_ch on 2008-01-08
Well, a server is nothing more than a computer that offers services to other (networked) computers. You can install a gui, that's not a problem but having a gui on it will decrease it's performance - which is normally unwanted (and not really necessary). Most "services" don't have an appropriate gui for configuration or at least advanced configuration either so you'll have to work manually on config files and for this you don't need a gui.

Of course, if performance is no problem for you and if you are more calmed using a gut, install one...

---

### Post by Raptor45 on 2008-01-08
Assuming this is for basic home use, there is no real reason to use the server version. The desktop version should work fine, and I'd be surprised if you noticed anything different performance wise.

Thats assuming you don't want to experiment of course.

---

### Post by bodhi.zazen on 2008-01-08
> **anewguy said:**
> Thanks, Bodhi.  I now have some place to start.  Used the command line YEARS ago when we had 2 Unix boxes at work besides the big mainframe that was my baby.  But, never had to set up a server.  All we really did was a few things to hosts file and a couple of others but nothing as an actual server.  This will give me something to learn with.  BTW - can I also install either KDE or gnome desktop in server, and will it have X support or is that why I would be limited to the command line?

Thanks again - you really rock at this stuff!:)

Yes, you can install a gui or various web tools (webmin, myphpadmin). You can forward X applications over SSH. Or the desktop over VNC (FreeNX).

> **hyper_ch said:**
> Well, a server is nothing more than a computer that offers services to other (networked) computers. You can install a gui, that's not a problem but having a gui on it will decrease it's performance - which is normally unwanted (and not really necessary). Most "services" don't have an appropriate gui for configuration or at least advanced configuration either so you'll have to work manually on config files and for this you don't need a gui.

Of course, if performance is no problem for you and if you are more calmed using a gut, install one...

+1. hyper_ch summarized the issue very succinctly. I agree the CLI is intimidating at first, but especially with a dedicated server, it is unnecessary. A majority of the administration is editing files and can be done with vim (or nano if you prefer) or restarting services (/etc/init.d/ssh restart).

Example, it is not uncommon to admin a remote or "headless" server over ssh.

another invaluable tool is screen

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

		[http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

---

### Post by daflame on 2008-01-10
> **bodhi.zazen said:**
> Yes, you can install a gui or various web tools (webmin, myphpadmin). You can forward X applications over SSH. Or the desktop over VNC (FreeNX).


There are resources for FreeNX too that you can load in a chroot.  Here is the forum that was setup for Gutsy:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by bodhi.zazen on 2008-01-10
Thanks daflame.

Freenx is the rage but I have never been able to get it working. I have tried twice and it seems buggy and, since I could not get it running, unreliable. It disables my (open)ssh keys. Too bad there was no simple way to import them.

I may try your how-to if I have time, I hope it goes better then the last time I tried.

To be honest I do most of my remote work via ssh and rarely need to forward X apps, let alone an entire desktop. I have been using VNC over ssh when needed, which is fairly fast with a light desktop and  compression. Was hoping freenx would be faster, but alas freenx just would not allow me to make a connection and I had to remove it to re-enable ssh.

---

