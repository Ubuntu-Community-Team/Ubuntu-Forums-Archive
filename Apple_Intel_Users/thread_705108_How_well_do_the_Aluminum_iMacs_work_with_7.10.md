---
title: "How well do the Aluminum iMacs work with 7.10?"
date: 2008-02-23
forum: Apple Intel Users
---

### Post by gutsy08 on 2008-02-23
Hello, I'm considering getting a aluminum iMac (or maybe a Macbook... or Macbook Pro) to run Ubuntu on and I'm wondering how well the iMac would work. I've noticed that the latest documentation for the iMac in the wiki is rather sparse and outdated for the Core 2 Duo models: [https://help.ubuntu.com/community/iMacCoreDuo]("https://help.ubuntu.com/community/iMacCoreDuo")... 

1. Do the instructions using the instructions for the Macbook (or Macbook Santa Rosa perhaps?) still apply?

2. Also, there seems to be a lot of documentation for setting up and even compiling a custom kernel for the Macbook and also for the Macbook Pro to a lesser extent, but I have found very little for the iMac.  Am I looking in the wrong places or is there simply less documentation and support for the aluminum iMac?

3. How well does the ATI Radeon 2400 XT or 2600 PRO work with the available drivers?  Does Compiz work well?

4. Are there any issues associated with virtualizing Ubuntu that are machine specific?  I'm considering Parallels, Virtualbox and VMware Fusion, and I'm curious what works the best.

5. Are there any other hardware specific issues?  I'm wondering how well the new aluminum keyboards work as I have heard about some compatibility problems with them.  Do all the function keys work?

I'd also be very interested in hearing about any other issues with the iMac compared to the Macbook with Ubuntu.  Anyhow, thanks in advance if you can answer all or some of these questions!

---

### Post by handy on 2008-02-23
> **gutsy08 said:**
> 
Hello, I'm considering getting a aluminum iMac (or maybe a Macbook... or Macbook Pro) to run Ubuntu on and I'm wondering how well the iMac would work. I've noticed that the latest documentation for the iMac in the wiki is rather sparse and outdated for the Core 2 Duo models: [https://help.ubuntu.com/community/iMacCoreDuo]("https://help.ubuntu.com/community/iMacCoreDuo")... 

I am dual booting Leopard & Ubuntu 7.10 on an aluminium 24" iMac.

You need to install [***_rEFIt_***]("http://refit.sourceforge.net/") then install the Ubuntu 7.10 64bit Alternate, it is really easy on the iMac.  You may have to do a simple fix for the sound.  I have not been keeping up with that one, you will easily find the thread if you search for it.  Also, I'm sure that Hardy will not have any sound issues with the iMac.

> **gutsy08 said:**
> 
2. Also, there seems to be a lot of documentation for setting up and even compiling a custom kernel for the Macbook and also for the Macbook Pro to a lesser extent, but I have found very little for the iMac.  Am I looking in the wrong places or is there simply less documentation and support for the aluminum iMac? 

There is no need to compile a custom kernel for the iMac.

> **gutsy08 said:**
> 
3. How well does the ATI Radeon 2400 XT or 2600 PRO work with the available drivers?  Does Compiz work well? 

I'm running Guild Wars on the iMac & it looks better than it ever did on my other machine which has an nVidia 7950GT /512 DDR3 video RAM.  Don't know about Compiz, I don't use it.

> **gutsy08 said:**
> 
5. Are there any other hardware specific issues?  I'm wondering how well the new aluminum keyboards work as I have heard about some compatibility problems with them.  Do all the function keys work?  

The function keys don't work, but you can map them to work, there is a thread on the subject.

> **gutsy08 said:**
> 
I'd also be very interested in hearing about any other issues with the iMac compared to the Macbook with Ubuntu.  Anyhow, thanks in advance if you can answer all or some of these questions!

My understanding is that the iMac is probably the easiest of the current crop of Macs to install Ubuntu on.  It certainly was no problem for me, I just had to spend a few minutes to get sound out of it.

---

### Post by cyberdork33 on 2008-02-23
Yea, the issue is the fact that most everyone has a Macbook / Macbook Pro and that it is just so simple on the iMacs... If you would like to edit / create a wiki page from your experience, I am sure it would be helpful to others.

---

### Post by handy on 2008-02-24
> **cyberdork33 said:**
> Yea, the issue is the fact that most everyone has a Macbook / Macbook Pro and that it is just so simple on the iMacs... If you would like to edit / create a wiki page from your experience, I am sure it would be helpful to others.

I should do that to relieve some of the unnecessary stress that poor iMac owners put themselves through.

***[Edit:]**  I just had a look at the Wiki, it is poor regarding the iMac.  I will think about what I can do (if anything) to improve the situation.*

---

### Post by ronocdh on 2008-02-25
> **handy said:**
> I should do that to relieve some of the unnecessary stress that poor iMac owners put themselves through.

***[Edit:]**  I just had a look at the Wiki, it is poor regarding the iMac.  I will think about what I can do (if anything) to improve the situation.*
I'm a MBP user, too. I try to be as helpful as I can in this community, but without any direct knowledge of Ubuntu on an iMac, I'm always searching for strong resources to point new users to. Unfortunately, it appears the iMac tutorials have always lagged far behind those for the MBs and MBPs.

Wiki on!

---

### Post by handy on 2008-02-25
> **ronocdh said:**
> I'm a MBP user, too. I try to be as helpful as I can in this community, but without any direct knowledge of Ubuntu on an iMac, I'm always searching for strong resources to point new users to. Unfortunately, it appears the iMac tutorials have always lagged far behind those for the MBs and MBPs.

Wiki on!

I would want to have a separate iMac section, not one that mostly shares with the MacBooks as it is now; even if it means some small amount of duplication in the info'.  

The way it is now is messy to my mind.  

If someone is a Linux or Ubuntu beginner, they don't want to be trying to work out which part of the instructions are for the iMac & which are for the notebooks.

I know I wouldn't.

---

### Post by cyberdork33 on 2008-02-25
Pretty much everything is the same between the pre-santa rosa Macbook Pro and the pre-aluminum iMacs. I know that Wi-Fi is different, and there was the option for Intel Graphics on some of the low-end iMacs at one time. (I think it was limited to the 17" variety...)

There is good information about the hardware in various Macs here:
[http://www.apple-history.com/](http://www.apple-history.com/)

There is also an app for OS X called MacTracker with a great deal of data.

---

### Post by fdbuck0 on 2008-02-27
@handy : You mention that you use the Ubuntu 7.10 64bit Alternate disc. Is there any specific reason for using the alternate disc ? Would it work also with the normal install disc (32 or 64 bit) ?
I have an iMac 24" 2.8 GHz, and I already did the partitioning of the 500 GB disk, leaving 100 GB for OSX, and installed rEFIt. Booting from a normal install disk worked, but when I try to "check CD for defects" or "Start and install Ubuntu", nothing happens, giving an error message that booting failed (or something like that).

I will try again with the alternate 64-bit disc tonight.

---

### Post by cyberdork33 on 2008-02-27
> **fdbuck0 said:**
> Booting from a normal install disk worked, but when I try to "check CD for defects" or "Start and install Ubuntu", nothing happens, giving an error message that booting failed (or something like that).

I will try again with the alternate 64-bit disc tonight.I'd say that things are happening, you just can't see it. You might have better luck with the alt cd.

---

### Post by handy on 2008-02-27
> **fdbuck0 said:**
> @handy : You mention that you use the Ubuntu 7.10 64bit Alternate disc. Is there any specific reason for using the alternate disc ? Would it work also with the normal install disc (32 or 64 bit) ?
I have an iMac 24" 2.8 GHz, and I already did the partitioning of the 500 GB disk, leaving 100 GB for OSX, and installed rEFIt. Booting from a normal install disk worked, but when I try to "check CD for defects" or "Start and install Ubuntu", nothing happens, giving an error message that booting failed (or something like that).

I will try again with the alternate 64-bit disc tonight.

For the same reason that I haven't jumped in & done the wiki, on the Ubuntu install for the iMac, it's that my memory fails me; thus far months have gone by since I did my research prior to my install of Gutsy on my iMac.  I did read that using the alternate install of the 64bit version of Gutsy was the way to go.  That is what I did, & it was the smoothest of all the many Ubuntu installs that I have done over the last nearly 2.5 years.  Therefore for the iMac I highly recommend the 64bit alternate install of Ubuntu, because it was so kind to me.  Of course for first time readers I must say that you must first install [***_rEFIt_***]("http://refit.sourceforge.net/") & of course shrink the OS X partition so as to be able to fit Ubuntu on.

To get Ubuntu on the iMac. You DO NOT need Bootcamp to do this! Assuming you have a single hard disk installed, with a default OS X partition.

Before you proceed: please make sure you have a current backup of your system. The following procedure is risky and could damage your system and/or make it unbootable.

   1. Boot into OS X
   2. Install [***_rEFIt_***]("http://refit.sourceforge.net/") (again I know, I'm just being kind :-))
   3. Repartition your hard drive. There are a variety of ways to do it, but the following way works for all, so let's say you want to resize your OS X partition to 200GB and create a new 200GB Linux partition. Open a terminal and type:

          sudo diskutil resizeVolume disk0s2 200G Linux Linux 200G

    I'll add some other ways to do the partitioning thing here soon, because the above is a bit more harsh than it has to be.

   4. Download the Ubuntu 7.10 Gutsy Live CD and burn it
   5. Restart
   6. When the rEFIt menu comes up, check if the partition tables are synced.
   7. Shutdown
   8. Start it again with the "c" key pressed to boot from the CD
   9. When Ubuntu comes up, click on the "Install" icon on the desktop
  10. Choose "Manual" partitioning and select the new (probably called /dev/sda3) partition as your root
  11. Ignore the warning about the swap partition
  12. Click on "Advanced" before finishing the installation and make sure that the boot loader is installed on /dev/sda3 (or whatever your root partition is) rather than (hd0) or similar
  13. Remove the CD and reboot
  14. Once you're back in Ubuntu, open a terminal and create your swap file (for example a 2GB one):

          dd if=/dev/zero of=/swap bs=1024 count=2097152
          mkswap /swap
          swapon /swap
          chmod 600 /swap

## I did not do the above swap file thing, I don't need it at all, I have 1gig of RAM & as far as I'm concerned swap is completely unnecessary.

  15. Done!

Cyberdork33, please if you will, do a verify on the above, I may have missed something?

The above was stolen from [***_here_***]("http://macprolinux.blogspot.com/2007/10/installing-ubuntu-710-gutsy-on-mac-pro.html") & modified to suit.

---

### Post by cyberdork33 on 2008-02-27
> **handy said:**
> Cyberdork33, please if you will, do a verify on the above, I may have missed something?

The above was stolen from [***_here_***]("http://macprolinux.blogspot.com/2007/10/installing-ubuntu-710-gutsy-on-mac-pro.html") & modified to suit.Looks good to me, although I would let Ubuntu make a swap partition, but I guess it really doesn't matter.
The way I normally recommend is, once starting the LiveCD, start the Partition Editor, select the second partition you just created and delete it. Then start the installer and choose to "install in the free/unused space"(I can't remember what it says exactly). This will automatically create an appropriately sized swap, and use the rest of the space for the root partition.

Can you hibernate using a swapfile rather than a a partition?

---

### Post by handy on 2008-02-27
I think that we can refine an iMac install in this thread pretty quickly & then we (I) can put it in the wiki. It is all but done I think.  I'd like to sort out the partitioning & make that clearer for different versions of OS X?  What do you think?

***[Edit:]** Hey you are the Mac man, I just had a glance at who is doing all the hard work in this sub-forum.  Thanks man, for all of those people you are helping; a smiley don't do it so I won't paste you one this time.  I will later for other things though I'm sure... ;-)*

---

### Post by cyberdork33 on 2008-02-27
> **handy said:**
> I think that we can refine an iMac install in this thread pretty quickly & then we (I) can put it in the wiki. It is all but done I think.  I'd like to sort out the partitioning & make that clearer for different versions of OS X?  What do you think?Yea If you get a better page started I can try to contribute. I am working Hardy stuff now, so i might be able to add some notes about that. I am off to some business right now.

I like the commandline method myself. There is a method to use Disk Utility in Leopard outlined here: [http://ubuntuforums.org/showthread.php?t=594298](http://ubuntuforums.org/showthread.php?t=594298)
You also might mention that you can use (recent versions) of gparted to shrink HFS+, and that it can be a bit difficult to "uninstall" Ubuntu due to difficulty growing HFS+.

---

### Post by handy on 2008-02-27
Cyberdork33, could you please help me refine the iMac install process, so that it is perfect, (because that is the kind of guy I am & I think you are too). 

I may also need help in any way shape or form regarding previous versions of the iMac, as in pre aluminium bodies, & any variations of hardware in those bodies.  
How much trouble do I want to get myself into here? :lolflag:

I'm not sure how far I'll go with the pre aluminium bodies.

***[Edit:]** I hadn't read your previous post when this was written, so it is a little out of context, which is a forum problem I guess.*

---

### Post by handy on 2008-02-27
> **cyberdork33 said:**
> Yea If you get a better page started I can try to contribute. I am working Hardy stuff now, so i might be able to add some notes about that. I am off to some business right now.

I like the commandline method myself. There is a method to use Disk Utility in Leopard outlined here: [http://ubuntuforums.org/showthread.php?t=594298](http://ubuntuforums.org/showthread.php?t=594298)
You also might mention that you can use (recent versions) of gparted to shrink HFS+, and that it can be a bit difficult to "uninstall" Ubuntu due to difficulty growing HFS+.

Thanks, I'll look into that thread & do some surfing to try to do the best by our brethren...  Scary word to someone like me!

---

### Post by cyberdork33 on 2008-02-27
> **handy said:**
> Thanks, I'll look into that thread & do some surfing to try to do the best by our brethren...  Scary word to someone like me!
Well, the beauty of a wiki is that you don't have to make it perfect. You put what you know, and I put what I know, and the result is something better than either of us could do alone.

---

### Post by fdbuck0 on 2008-03-10
> **cyberdork33 said:**
> I'd say that things are happening, you just can't see it. You might have better luck with the alt cd.

This weekend I tested with a Hardy Alpha5 CD, desktop 64bit LiveCD version, and it booted nicely.
The only different thing that I did this time was to burn the CD on my iMac self instead of burning it on my laptop (Toshiba, running Ubuntu 7.10).
Maybe the superDrive in the iMac doens't like CD's from other drives ?

I didn't have the time to actually install Hardy Alpha5 this weekend, but I noticed that the wireless network adapter was not detected in the LiveCD.
Maybe this is still an alpha issue ? Is the wireless adapter in the 24" iMac a problem for Ubuntu ? I'll have a look tonight with a liveCD from 7.10.

---

### Post by cyberdork33 on 2008-03-10
> **fdbuck0 said:**
> This weekend I tested with a Hardy Alpha5 CD, desktop 64bit LiveCD version, and it booted nicely.
The only different thing that I did this time was to burn the CD on my iMac self instead of burning it on my laptop (Toshiba, running Ubuntu 7.10).
Maybe the superDrive in the iMac doens't like CD's from other drives ?

I didn't have the time to actually install Hardy Alpha5 this weekend, but I noticed that the wireless network adapter was not detected in the LiveCD.
Maybe this is still an alpha issue ? Is the wireless adapter in the 24" iMac a problem for Ubuntu ? I'll have a look tonight with a liveCD from 7.10.
It is a broadcom device and a poorly supported one at that... You need to use ndiswrapper.

---

