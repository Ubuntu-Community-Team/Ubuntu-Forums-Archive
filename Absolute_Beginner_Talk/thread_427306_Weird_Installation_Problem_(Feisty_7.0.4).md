---
title: "Weird Installation Problem (Feisty 7.0.4)"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2007-04-29
Please help and I apologize if this has already been covered, but I could not locate.

I successfully made my installation disc, but when I tried to get it to boot, my computer gave me the following:
"[B]BusyBox v1.1.3 (Debian 1:1,1,3 -3ubuntu3) Built-in shell(ash) Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off (initramfs)_"[/B]

My computer is an old Dell PC, Dimension 8200, running an old version of XP Home.  It has 564kb memory and 2.4 ghz intel processor, so I don't think the problem is a lack of hardware capability.

BTW, the CD does run on another computer--my much newer laptop.

---

### Post by apunc1 on 2007-04-30
[http://ubuntuforums.org/showthread.php?t=426224](http://ubuntuforums.org/showthread.php?t=426224)

---

### Post by starcraft.man on 2007-04-30
I had this same problem, I had a CD write drive and a DVD burner, I unplugged the CD drive and it booted fine from my DVD Burner. I believe its a small glitch with recognizing two drives on the same IDE line (HDD or CD) If you have two drives or two cds unplug one of them and try again, can always readd them manually.

---

### Post by Aurora@FleetBuzz on 2007-04-30
Thanks, guys.  After I posted this thread, I found this one.
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)
Warning:  it's 14 pages long!  Lots of suggestions, but I'm not even remotely conversant with Linux to try most of them.  I may be forced to wait until the next distribution (ugh!).  I do know that I have a floppy and a CD RW (IDE).  Should I disconnect the floppy and give it a go?  Wouldn't bypassing it in the boot sequence accomplish the same thing?:confused:

---

### Post by apunc1 on 2007-04-30
have you tried edgy? it looks like things are ok until you upgrade to the 2.6.20-15 kernal. in feisty. i'm sure if this many people are having a problem, a fix will be made.

---

### Post by Aurora@FleetBuzz on 2007-05-01
Thanks for the suggestion.  Can Edgy be run from a cd in order to preview?

---

### Post by apunc1 on 2007-05-01
yes,the live cd version of edgy can run without changing your current settings and then you can choose to install whenever you wish by clicking the install icon on the desktop.

[http://us.releases.ubuntu.com/edgy/](http://us.releases.ubuntu.com/edgy/)

---

### Post by Aurora@FleetBuzz on 2007-05-01
Thanks.  I'll try it!  I wonder if Kubuntu Feisty ahs the same installation issues as Ubuntu Feisty?

---

### Post by apunc1 on 2007-05-01
kubuntu uses kde as its desktop environment and ubuntu uses gnome. there are some other differences in software choices but for the most part i would have your problem in kubuntu live cd as well. some installation problems can be solved by using the alternate cd instead.


by the way, have you seen this [http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off](http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off)

---

### Post by Aurora@FleetBuzz on 2007-05-01
> **apunc1 said:**
> kubuntu uses kde as its desktop environment and ubuntu uses gnome. there are some other differences in software choices but for the most part i would have your problem in kubuntu live cd as well. some installation problems can be solved by using the alternate cd instead.


by the way, have you seen this [http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off](http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off)

Yes, but as this post from **HAL8000** notes:
> No, the solution will not work for everyone. In my case I could load the live cd, install Feisty, but on reboot it would halt with the cant access tty error.
To use chroot you must have a bootable system; either on a live cd or loaded on a partition. If the busybox prompt is displayed from a live cd then there is no way (that I can see) around this problem.....
having said that, it may be possible to install 6.10 Edgy first, then do apt-get distro upgrade to update to Feisty, but I think some people have had problems with this method of install.
I'm getting the busybox prompt from the live CD.  

I'll probably go with Edgy and wait and see if the bug gets fixed.  

I can see this is all the beginning of a great adventure....:)

---

### Post by Aurora@FleetBuzz on 2007-05-02
Edgy works!  The CD runs.  Can anyone point me to a good resource for instructions on dual booting?  I am a novice (I had to look up GRUB!), so I need something virtually idiot proof.  Thanks.

---

### Post by apunc1 on 2007-05-02
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

there is also a link on that site about planning partitions for some dual boot scenarios.

good luck.

---

### Post by coolbrook on 2007-05-02
I encountered this same thing on one of my machines today.  A comedy of errors.

---

### Post by jerrylamos on 2007-05-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It's a bug.  Some of the choices of fixes are in my post "Workarounds" in "Installation & Upgrades".  For some of the knock down drag out see the Launchpad Bug URL.

My inference from several sources is Ubuntu and Debian are trying to improve boot speed by doing some things in parallel.  Unfortunately, some things get started before dependencies are ready, and crash.  This is time dependent and depends on hardware et. al. on what will fail when.

Once I found a fix to "can't access tty", the next step was increasing the LCD monitor resolution to 1280x1024 done in Terminal with sudo dpkg-reconfigure -phigh xserver-xorg.  Since then Feisty has been running solid as a rock.

Now I'm entering this from a Feisty Fawn partly upgraded to Gutsy Gibbon so I'm expecting some surprises.  I've had a couple so far which are now worked around.

Cheers, Jerry:KS

---

### Post by Aurora@FleetBuzz on 2007-05-03
I'm going to try to install Edgy Eft.  I found a very good video here by Alan Pope:
[http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu+dual+boot](http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu+dual+boot)
Makes it look easy! (if everything works).  According to the video, one can resize the partition from the Ubuntu installation, obviating the need to resize / partition the HD in advance.  

My main concern is that GRUB will recognize Windows XP so that it will display as an option in the GRUB GUI at startup.  If it doesn't....  :oops: 

Has anyone had problems with this particular facet of the operation?

---

### Post by lamalex on 2007-05-03
I've never had it not pick up win xp, if for some reason it just says "screw you" and doesn't, it's not hard to add the entry yourself

---

### Post by Aurora@FleetBuzz on 2007-05-03
> **Iamalex said:**
> I've never had it not pick up win xp, if for some reason it just says "screw you" and doesn't, it's not hard to add the entry yourself
Appreciate your help.  On the outside chance it does, could you point me in the direction where it advises how to do this?

---

