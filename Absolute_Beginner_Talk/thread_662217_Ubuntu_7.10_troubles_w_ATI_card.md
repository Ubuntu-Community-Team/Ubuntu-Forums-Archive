---
title: "Ubuntu 7.10 troubles w/ ATI card"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by ArmoredCavalry on 2008-01-08
Today, I did a clean install of Ubuntu 7.10, when I went to boot the GUI would not start, I got a message saying :

```
The display server has been shut down 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0

```

I have an ATI Radeon HD 3850 video card. Apparently 7.10 has some issues with ATI cards in general? I know ATI can be a pain in Linux, but I just had 7.04 working yesterday with my card, seems like it **should **work in a **newer** version of Ubuntu...

If there isn't a way to get the video card working, is there any reason I should not just re-install 7.04? I was hoping that wireless might go more smoothly in 7.10, is this the case?

Thanks, AC

---

### Post by shareMenaPeace on 2008-01-08
Hello armoredcavalry.
since recently ATI didnt supported linux, meaning they didnt released drivers officialy. SO people hacked the drivers somehow. Now they support them.
Anyway this specific ATI card 3850 and it seems the complete series is bad with support.

WHat i suggest

try ENVY a very neat tool to install the drivers ... 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Use manual install and try aroudn with the driver version options there. 

Maybe use even linuxmint.com, which enhanced my ATI incredible (Dont ask me why), first i installed restricted drivers than with manual envy.

Cheers + Good Luck to you :D

:popcorn:

---

### Post by shareMenaPeace on 2008-01-08
This is also related. 
[http://ubuntuforums.org/showthread.php?t=639094&highlight=ATI+3850](http://ubuntuforums.org/showthread.php?t=639094&highlight=ATI+3850)

---

### Post by ArmoredCavalry on 2008-01-08
Hey, thanks for the reply. I'm checking out Envy right now, looks like it might be worth a shot. I was actually just looking at mint today, I'll have to download that on my other PC while I'm trying Envy. :)

Thanks, AC

---

### Post by shareMenaPeace on 2008-01-08
mint rox so much its liek ubuntu what you expect and not get :)

---

### Post by ArmoredCavalry on 2008-01-08
Wow, this is really strange. When I went to install envy via recovery mode, it gave me an error, because not all the dependencies were installed. I don't have my wireless working yet, so no internet. I tried doing startx anyways, just to see if it made a change... and Gnome boots up fine. lol 

Strange part is I can't even start the envy GUI to install drivers, because of the dependencies, but hey, the Gnome is running, so I'm happy for now. :)

---

### Post by blueridgedog on 2008-01-08
> **shareMenaPeace said:**
> mint rox so much its liek ubuntu what you expect and not get :)

In what way is it different?  The community seems substantially smaller, but perhaps there are other features...

---

### Post by shareMenaPeace on 2008-01-09
> **blueridgedog said:**
> In what way is it different?  The community seems substantially smaller, but perhaps there are other features...

Ubutnu is nice from the look, but sometimes you see those really nice tweaked screens which you never come close. Its something like this is all done once you install it.
Also the overaqll process seems tweaked and minimized to the really nessassary stuff.

Also the only think i had to install was Virtualbox, AWN (dock), VLC, Blender, RealPlayer - which i did from the online repos with a view clicks and all runs like ... just smooth (Ok didnt run blender yet).
Ok this might sound standard to some people but now comes the strange part. I run ubuntu since edgy on 2 notebooks and i was really testing around, and of course tried to tweak it too.

Somehow whatever i do .. even runnnign windows xp on a virtualbox with a windows music application - it just runs smooth - its almost scary :D

It boots up faster, its nicer (how it is structured and grouped). It is like my ubuntu experience has doubled suddently.

Really strange but linuxmint is hardcore uber sweetness in caramel :) I recommend to EVERYONE to just download the live cd (daryna) and install it fresh without an eye blink :)

Cheers
:popcorn::popcorn::popcorn:guitar::guitar::guitar:

---

### Post by blueridgedog on 2008-01-09
I will give it a test.

---

### Post by Mohonri on 2008-01-10
I'm in a similar situation--I have a Radeon HD3850, and I'm trying to install 7.10 with no success.  I get the same error during installation, and haven't been able to find a solution anywhere.

I don't have the same problem with 7.04, so I'm in the middle of installing it now.  However, I'd really like to upgrade to 7.10.  But it sounds like even if I successfully upgrade to 7.10, I'll run into this problem again.  It's weird, because I see several people in the forum who seem to have a newer ATi card running without any issues.  Any other suggestions?

---

### Post by ArmoredCavalry on 2008-01-10
> **Mohonri said:**
> I'm in a similar situation--I have a Radeon HD3850, and I'm trying to install 7.10 with no success.  I get the same error during installation, and haven't been able to find a solution anywhere.

I don't have the same problem with 7.04, so I'm in the middle of installing it now.  However, I'd really like to upgrade to 7.10.  But it sounds like even if I successfully upgrade to 7.10, I'll run into this problem again.  It's weird, because I see several people in the forum who seem to have a newer ATi card running without any issues.  Any other suggestions?

I got 7.10 working, but just barely.I think what did it was deleting xorg.conf, which forced xserver to write a new, working one. (you can do this either through the recovery counsule, or windows use this ([http://www.fs-driver.org/](http://www.fs-driver.org/)) from windows). A newer ATI card? The 3800's are the newest, and ATI doesn't even have the Linux drivers out for them yet, which is the problem I ran into. So it seems that right now, me and you will have to run any version of Llinux without 3d acceleration. Just hope that ATI gets some drivers out for our card soon.

P.S. I ended up installing PCLinuxOS Gnome edition. I would have installed the KDE one, but it doesn't support SATA driver, so I couldn't even install it to my HD. The reason I like PCLinuxOS is because my **wireless took 3 steps (in built in GUI program) to get working** (why can't Ubuntu do that??).  Only downside is the Gnome version does not have much software you can install, as it is not the main (KDE) version. :(

---

### Post by Mohonri on 2008-01-10
> **ArmoredCavalry said:**
> I got 7.10 working, but just barely.I think what did it was deleting xorg.conf, which forced xserver to write a new, working one. (you can do this either through the recovery counsule, or windows use this ([http://www.fs-driver.org/](http://www.fs-driver.org/)) from windows). A newer ATI card? The 3800's are the newest, and ATI doesn't even have the Linux drivers out for them yet, which is the problem I ran into. So it seems that right now, me and you will have to run any version of Llinux without 3d acceleration. Just hope that ATI gets some drivers out for our card soon.I somehow got the impression that the Linux drivers were already out for the 38x0 cards, but apparently I was mistaken.:(  (incidentally, I was planning on dual booting Win2k and Gutsy, but found out that there aren't any Win2k drivers either!  Tsk, tsk, tsk)  I guess I'll just have to sit and wait for a while...in the meantime, I think I'll just sit tight with 7.04.

PSEUDOEDIT:  Yeah, I heard about the 38x0 support in the Catalyst 7.12 drivers [over at Phoronix](http://www.phoronix.com/scan.php?page=article&item=947&num=1).  However, I can't seem to find the driver on the ATI site or anywhere else.

PSEUDOEDIT2:  Ok, so here's the page from ati.amd.com:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
The release notes don't mention the 38x0 series, but apparently plenty of people have had success with it.

---

### Post by ArmoredCavalry on 2008-01-10
> **Mohonri said:**
> I somehow got the impression that the Linux drivers were already out for the 38x0 cards, but apparently I was mistaken.:(  (incidentally, I was planning on dual booting Win2k and Gutsy, but found out that there aren't any Win2k drivers either!  Tsk, tsk, tsk)  I guess I'll just have to sit and wait for a while...in the meantime, I think I'll just sit tight with 7.04.

PSEUDOEDIT:  Yeah, I heard about the 38x0 support in the Catalyst 7.12 drivers [over at Phoronix](http://www.phoronix.com/scan.php?page=article&item=947&num=1).  However, I can't seem to find the driver on the ATI site or anywhere else.

PSEUDOEDIT2:  Ok, so here's the page from ati.amd.com:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
The release notes don't mention the 38x0 series, but apparently plenty of people have had success with it.

Hm, interesting it says in the FAQ: "The ATI Proprietary Linux driver currently supports Radeon 8500 and later AGP or PCI Express graphics products, as well as ATI FireGL 8700 and later products. We do not currently plan to include support for any products earlier than this. Drivers for earlier products should already be available from the DRI Project or Utah-GLX project."

Technically this *would include* the 3850. I think I'll try the driver out, not like I have anything to lose. :) Good find.

---

### Post by Mohonri on 2008-01-11
Well, I tried following the instructions on the [BinaryDriverHowTo](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), but here's how it turned out:
Installing from Ubuntu repositories:  Restricted Drivers Manager said I didn't need any restricted drivers.  So I went to the [instructions](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3) for installing it after downloading the latest drivers from the ati site.  When I got to the step where you create the .deb packages, I got an error complaining about not finding ./debian/compiz-manager, and it aborted.

So I tried [envy](http://www.albertomilone.com/nvidia_scripts1.html), which (I think) successfully installed the driver.  However, I couldn't enable desktop effects, and it sure seems like moving windows around the desktop and scrolling within a window are really slow.  Supposedly the 7.12 driver supports 2D and 3D acceleration, so I'll have to install some game to test it out, but I'm honestly not too hopeful at this point.

The only reason for the 3850 was to play games, so if ATi had decided to release a Win2k driver for it, I wouldn't consider any of this an issue.  Grrr.

---

### Post by pdaigneault on 2008-01-11
Hi all, I have a 3850 ATI card and I used Envy to install. I had to reinstall my old card to get envy installed since I could not boot with new 3850. Insatlled Envy to remove my old drivers and installed newest drivers for 3850 before rebooting installed new card and everything OK now.

---

### Post by ArmoredCavalry on 2008-01-11
> **pdaigneault said:**
> Hi all, I have a 3850 ATI card and I used Envy to install. I had to reinstall my old card to get envy installed since I could not boot with new 3850. Insatlled Envy to remove my old drivers and installed newest drivers for 3850 before rebooting installed new card and everything OK now.

By everything o.k. you mean you got **3D acceleration working??**

---

### Post by Mohonri on 2008-01-11
> **ArmoredCavalry said:**
> By everything o.k. you mean you got **3D acceleration working??**So if I understand you correctly, you:
Installed ubuntu with old video card
Installed envy
Removed drivers and installed new drivers
Shut down
Installed new video card
Boot fine.

Am I understanding that right?  I'd like to know the answer to the 3D acceleration question, too.

---

### Post by crackmonkey on 2008-01-17
I managed to get a Radeon 3850 working in Ubuntu 7.10 by using Envy. The driver works, but I'm not sure how to confirm if 3D is working (at least the controls for 3D stuff like anti-aliasing in the Catalyst Control Center can be changed so I'm guessing that 3D works). The Compiz-Fusion eye candy works so I know that compositing is working as well.

This was off a fairly clean and new install of Ubuntu, and I believe that the Ubuntu Restricted Extras were installed first. The Restricted Driver Manager reports I don't have hardware that requires restricted drivers, so I was stuck going a manual route to get the ATI drivers installed.

For whatever reason, when I tried manually installing the driver (not using Envy) I just broke the display configuration every time, requiring that I restore xorg.conf from backup. After I saw how easily Envy took care of it all (and correctly from what I can tell), I'm pretty happy with Envy now and will continue to use it, until the state of drivers and the driver installers improves such that Envy is no longer "necessary".

The bad news is that the screen resolution doesn't seem to want to go above 1280x1024. With my wide-screen monitor at native 1680x1050 resolution everything is squished and looks "fatter" than it should be. So far I've been unable to resolve that, apparently this is a known issue: "Connecting a display device that supports 1680x1050 to a system running Linux may result in a maximum display resolution of 1280x1024 only being available" (from the Catalyst 7.12 Linux i386 driver release notes).

I'm really hoping that ATI can fix this widescreen resolution problem in the next driver release. If anyone knows how to make the correct resolution work in this configuration I'd love to hear about it, but I'm willing to wait for an ATI-supported fix. Working with xorg.conf manually is frustrating and error-prone to say the least.

---

### Post by Mohonri on 2008-01-18
> **crackmonkey said:**
> I managed to get a Radeon 3850 working in Ubuntu 7.10 by using Envy.Did you do a clean install of 7.10?  When I attempted to do that, I got the x-restarting-six-times-in-90-seconds problem.  Did you encounter any problems during the installation process?

---

### Post by crackmonkey on 2008-01-20
> **Mohonri said:**
> Did you do a clean install of 7.10?  When I attempted to do that, I got the x-restarting-six-times-in-90-seconds problem.  Did you encounter any problems during the installation process?

It was a mostly clean install of 7.10, (some config files and my home folder were copied from my old box) and Ubuntu Restricted Extras were probably installed. I did not get any errors at all, other than from my manual changes to xorg.conf that didn't work. Envy installed the driver properly and the Ubuntu live CD and installer did as well as could be expected with my hardware given the non-free nature of ATI's drivers (and the known issue of 1680x1050 resolution).

---

### Post by Mohonri on 2008-01-22
> **crackmonkey said:**
> It was a mostly clean install of 7.10, (some config files and my home folder were copied from my old box) and Ubuntu Restricted Extras were probably installed. I did not get any errors at all, other than from my manual changes to xorg.conf that didn't work. Envy installed the driver properly and the Ubuntu live CD and installer did as well as could be expected with my hardware given the non-free nature of ATI's drivers (and the known issue of 1680x1050 resolution).Interesting.  I may have to make another pass at this.  What's the issue with the 1680x1050 resolution?  My monitor happens to have that resolution...

---

### Post by crackmonkey on 2008-01-22
> **Mohonri said:**
> Interesting.  I may have to make another pass at this.  What's the issue with the 1680x1050 resolution?  My monitor happens to have that resolution...

With the driver that was available at the time of my first post, it simply didn't work for me (see my original post in this thread). However ATI has recently released a new driver that seems to have corrected the problem - at least for me. I manually installed the drivers that time following the [instructions here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") after having downloaded the newest driver from ATI's website.

---

