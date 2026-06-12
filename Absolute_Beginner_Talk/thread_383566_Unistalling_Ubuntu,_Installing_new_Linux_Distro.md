---
title: "Unistalling Ubuntu, Installing new Linux Distro"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by dRock1286 on 2007-03-13
Alright...
**Note:  I have two harddrives and run all my WinXP stuff on one and Linux Stuff on the other**

First off, I installed Ubuntu on my computer only to find it is extremely hard to get my wireless card running.  I don't have the time right now to work it out.  So I found a distro that is pretty much user/newbie friendly and will allow my card access almost right out of the box.  Ubuntu is great, I just don't have the time for it right now. So...

I would like to unistall Ubuntu and then install Mandriva in its place.  However, when I unistall Ubuntu, I get a GRUB Error 17 when trying to load just WinXP.  (I have even tried to just load from my first harddrive that has WinXP on it.)  Keep in mind, there is no linux or linux kernels or anything on my second drive.  How can I get rid of Ubuntu and then have my computer able to run WinXP without getting any errors?

Also, when I try to install Mandriva One 2007 Gnome on my second drive, I get GRUB Error 15.  How can I install another Linux Distro (which I guess runs on a different kernel?) and get no errors on GRUB?

Any help ridding my of these errors would be great.

---

### Post by dRock1286 on 2007-03-13
Bump...I need this fixed today...

Anyone know how to?

---

### Post by dRock1286 on 2007-03-13
Or can I install the new linux in a new partition and load from it to avoid all of the bogus crap?

---

### Post by Bachstelze on 2007-03-13
It's normal that you get a GRUB error when you uninstalled Ubuntu since some files it needs are stored on the Ubuntu partition. Just boot from your Mandriva CD and install it. It will also install it's own GRUB that will overwrite Ubuntu's.

---

### Post by Zzl1xndd on 2007-03-13
just so I understand you have already removed Ubuntu? and have you already installed Mandriva? and are just having an issue with Grub?

---

### Post by dRock1286 on 2007-03-13
Yes.  I have unistalled Ubuntu and installed Mandriva and still get the Error 15 in GRUB.  Isn't that becuase it can't find the kernel?  It had locked me out of my computer because I couldn't get it to load WinXP either.  So I reinstalled Ubuntu to get GRUB working so I can access WinXP...And that's where I am now.  I want to get rid of Ubuntu and install Mandriva without GRUB errors...

---

### Post by dRock1286 on 2007-03-13
> **HymnToLife said:**
> It's normal that you get a GRUB error when you uninstalled Ubuntu since some files it needs are stored on the Ubuntu partition. Just boot from your Mandriva CD and install it. It will also install it's own GRUB that will overwrite Ubuntu's.

So you're saying that after installing Mandiva from the Live CD, it *should* just have fixed itself?

---

### Post by louieb on 2007-03-13
This is easy. When you install Mandriva or any other Linux distro and you want to get rid of the current distro. When you install the new distro tell it to format and install in the old distros partition(s). 
But before you do you may want to look in /boot/grub/menu.lst and copy down the XP entry in case you need it for the new distros GRUB configuration file. Most distros are pretty good at picking up windows but from time to time  you have to it manually.

---

### Post by jdfreshwater on 2007-03-13
yes if you install madriva on your linux partition, it will write a new grub configuration and allow you to have win xp and mandriva, instead of ubuntu.

---

### Post by Famicommie on 2007-03-13
It won't necessarily fix itself. GRUB can be a tricky beast. Use a win98 disc/cd and run the command "fdisk /mbr". That will replace GRUB completely, and allow Mandriva to install it's own version of GRUB.

---

### Post by civilmonkey on 2007-03-13
I had a similar problem when trying to fix my Win XP install:

When I deleted my paritions which contained Ubunto 6.10 I got reboot errors as well.  It was because I had over written my windows master boot record (MBR) with GRUB.  I needed to re-create the windows MBR.

For windows XP I found this helpful.  MAKE SURE you make a backup copy of boot.ini just in case.  [http://www.short-media.com/articles/repair_windows_xp](http://www.short-media.com/articles/repair_windows_xp)

Now I use Windows boot loader to boot linux so it makes a new linux user like myself much happier.

---

### Post by dRock1286 on 2007-03-13
And if I don't have a win98 disc?  My WinXP came with my computer.  Can I run it in CMD or anything else?

---

### Post by dRock1286 on 2007-03-13
My XP works fine...its just getting to it.  GRUB won't let me through it...  But, if I do reformat and then install Mandriva on the second drive, will it build its own GRUB to load XP from?

---

### Post by jdfreshwater on 2007-03-13
> **dRock1286 said:**
> My XP works fine...its just getting to it.  GRUB won't let me through it...  But, if I do reformat and then install Mandriva on the second drive, will it build its own GRUB to load XP from?
It should rebuild grub and allow you to access XP.  Most systems will build grub on their own and detect all previously installed Operating Systems.

---

### Post by civilmonkey on 2007-03-13
For me it was the same.  I deleted Ubuntu, then I couldn't get to XP. 

It kind of works like this (but don't quote me).

You boot up, the MBR of the active partition points to a boot loader, then the boot loader lets you chose which operating system to load.  If you deleted Ubuntu, GRUB (the Ubuntu boot loader) can't find it anymore.  Maybe your GRUB can't find XP for some reason.  

If you didn't delete XP, you should be able to make a new MBR and tell the MBR to load the windows boot loader, which in turn will boot windows.  (see my first post with link)

If you have windows running again and everything is fixed, you can start fresh and install you new linux distro.  At least, that's what I had to do.

If you want, for you next linux, don't let the linux boot loader overwrite the working MBR. Instead put it on the linux partition (not your windows partition).  Then use the windows boot loader to call linux.  There are lots of links if you google 'dual boot xp ubuntu'.  (the tutorial I used was [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/))

good luck!

---

### Post by dRock1286 on 2007-03-14
Alright...don't have the Windows CDs.  Is there a way to partition my Linux harddrive and dual boot another Linux distro from that?

---

### Post by dRock1286 on 2007-03-14
bump

---

### Post by Famicommie on 2007-03-14
> **dRock1286 said:**
> Alright...don't have the Windows CDs.
[http://www.bootdisk.com/](http://www.bootdisk.com/) :D
> **dRock1286 said:**
> Is there a way to partition my Linux harddrive and dual boot another Linux distro from that?
Yes. Just make sure to use the same SWAP space for both partitions. You should also set up any planned partitions now, so that you don't have to resize them later.

---

### Post by dRock1286 on 2007-03-14
> **Famicommie said:**
> [http://www.bootdisk.com/](http://www.bootdisk.com/) :D

Yes. Just make sure to use the same SWAP space for both partitions. You should also set up any planned partitions now, so that you don't have to resize them later.

Is there any way you can link to a walkthrough or tell me how yourself...  Doesn't it have to do with editing the partition table when installing a new linux distro?

---

### Post by dRock1286 on 2007-03-14
And also...will it use the same GRUB menu and not screw up if I install another linux distro on a separate partition?  And...can I make another partition that I can download files into with Windows and read and use them in my Linux partition?  (my internet isn't up and running in Ubuntu yet...)

---

### Post by dRock1286 on 2007-03-14
bump

---

### Post by dRock1286 on 2007-03-14
Nevermind.  I got the internet to work now.  I guess I was having a wireless router problem.  I think I wasn't being allowed in the network because it was password protected.  Today, my dad reformatted his computer and made the router without WPA/WEP...and now I can get on without any problems.  So...now that that's all worked out, I think I'll stay...I kinda like it here...   :P

---

### Post by Smuve on 2007-03-14
As someone who has been in similar situations, I have found that disconnecting the windows drive while installing linux will alleviate these kind of problems in the future.  Then you can use your BIOS to select the boot disk.  Some people find this cumbersome, I like it.  Do what's best for you.

---

### Post by dRock1286 on 2007-03-14
Yeah...I did that in the beginning..but once you've done it the wrong way (well...just leaving the first hdd plugged in...not necessarily wrong)  it will *ALWAYS* look for the linux stuff...so I screwed it up.

---

