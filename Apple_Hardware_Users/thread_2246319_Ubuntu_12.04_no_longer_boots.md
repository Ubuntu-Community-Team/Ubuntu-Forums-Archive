---
title: "Ubuntu 12.04 no longer boots"
date: 2014-09-29
forum: Apple Hardware Users
---

### Post by Tim_Johnson on 2014-09-29
I have had ubuntu 12.04 installed on my Mac Mini for several months and working fine. Now my system fails to boot ubuntu. 
Here are symptoms
Using the boot manager (pressing ALT/OPTION key on startup)
3 Icons :
1) EFI Boot (starts up rEFInd)
2) Windows HD (Instead of Linux Logo) - if selected, just a black screen
3) If the install USB is plugged in, shows as Windows USB, if selected - black screen again
If EFI boot is selected or if I let the system start up rEFInd I get the following selections
1)Apple - and if selected boots into OS X 10.7
2)Penguin Icon with "Boot Linux from FAT Volume" as label
3)Penguin Icon with "Boot Linux from Linus 2" as label
   NOTE : "Linus" is the label for my hard drive
4) If I have the install USB plugged in, then I will see a USB Icon labeled as "Boot Legacy OS From FAT Volume"
selections of 2 - thru 4 fail to produce anything but first a Penguin Icon and then if I press the CONTROL key - a black screen.
I just removed rEFIt and installed rEFInd, prior to that I was after numerous attempts and head scratching able to boot into ubuntu
and I ran boot-repair with diagnostics - the post repair diagnostics can be seen at
[http://paste.ubuntu.com/8451835/](http://paste.ubuntu.com/8451835/)
And here is the output from diskutil
```

inus:~ tim$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Linus                   359.2 GB   disk0s2
   3:       Microsoft Basic Data                         42.0 GB    disk0s3
   4:                 Linux Swap                         8.5 GB     disk0s4
   5:       Microsoft Basic Data                         69.0 GB    disk0s5
   6:       Microsoft Basic Data                         21.0 GB    disk0s6

```
Please help! Gawd, I hate using OS X, it runs like a broke-down animule compared to fluxbox on ubuntu, sheesh....

---

### Post by Tim_Johnson on 2014-09-30
This is a serious, serious problem folks. If there is no one here that can help, perhaps a different forum with a different skill set can be recommended. 
If I can't boot back into ubuntu by October 1, I have a real mess on my hands, even with current backups.....

---

### Post by este.el.paz on 2014-09-30
@Tim:

I'm a tad busy right now, but, couple points, if 12.04 was running fine, and then, after installing rEFInd, it isn't . . . then there **might** be some issue there.  Did you e.g., check the md5sum number of the rEFInd file?  And, did you install it the easy "drag n drop" way in Terminal to the OSX user . . . so it creates a file "EFI" in the oSX HD?  Maybe try another install of it, or post a question on their forum on SourceForge and see if they can help out there???

In terms of the other points I'd have to read through again, but as far as the partitions goes, showing Linux there as "microsoft" does seem "interesting" . . . did you do "automatic" install of 12.04, or did you "choose other option" and manually set them up"?  Without looking, but from many installs, it usually says "linux" swap or whatever; although yes in the boot manager, linux will be shown as "Windows" . . . .  I don't see a "bios_grub" partition either?  

e.e.p.

---

### Post by Tim_Johnson on 2014-09-30
> **este.el.paz said:**
> @Tim:

I'm a tad busy right now, but, couple points, if 12.04 was running fine, and then, after installing rEFInd, it isn't . . . then there **might** be some issue there.  Did you e.g., check the md5sum number of the rEFInd file?  And, did you install it the easy "drag n drop" way in Terminal to the OSX user . . . so it creates a file "EFI" in the oSX HD?  Maybe try another install of it, or post a question on their forum on SourceForge and see if they can help out there???

In terms of the other points I'd have to read through again, but as far as the partitions goes, showing Linux there as "microsoft" does seem "interesting" . . . did you do "automatic" install of 12.04, or did you "choose other option" and manually set them up"?  Without looking, but from many installs, it usually says "linux" swap or whatever; although yes in the boot manager, linux will be shown as "Windows" . . . .  I don't see a "bios_grub" partition either?  

e.e.p.
Thank you for the reply. To clarify, 12.04 ran fine with rEFIt for months but the boot failure occurred while I was still using rEFIt.
I did _not_ do a md5sum check on rEFInd but did install using the "drag n drop" method with no options switches.
Ubuntu 12.04 was installed with a manual partitioning scheme. 
I'm going to "replay" part of the diskutil list with attribution for the partitions ```

  3:       Microsoft Basic Data                         42.0 GB    disk0s3  root (/)
   4:                 Linux Swap                         8.5 GB     disk0s4
   5:       Microsoft Basic Data                         69.0 GB    disk0s5 (/home)
   6:       Microsoft Basic Data                         21.0 GB    disk0s6 (usr/local) 
```
Your observation is correct : I _did not_ put /boot on a separate partition.
Thanks for the tip on SourceForge, I've also posted to my local LUG and I'm also going to run some Mac repairs such as fsck in single-user mode (see [http://support.apple.com/kb/TS1417](http://support.apple.com/kb/TS1417))
I suspect the problem is on the Mac side and has to do with its booting procedures (FYI : I'm a newbie in that area)
thanks again

---

### Post by este.el.paz on 2014-09-30
> **Tim_Johnson said:**
> Thank you for the reply. To clarify, 12.04 ran fine with rEFIt for months but the boot failure occurred while I was still using rEFIt.

I'm going to "replay" part of the diskutil list with attribution for the partitions ```

  3:       Microsoft Basic Data                         42.0 GB    disk0s3  root (/)
   4:                 Linux Swap                         8.5 GB     disk0s4
   5:       Microsoft Basic Data                         69.0 GB    disk0s5 (/home)
   6:       Microsoft Basic Data                         21.0 GB    disk0s6 (usr/local) 
```
Your observation is correct : I _did not_ put /boot on a separate partition.


@Tim:

For the most part the technical aspects of linux exceed my skillset, but I have done a number of OSX/linux dual boot and triple boot set ups . . . here, even though technically what you are doing with the multiple partitions should be OK, it ***might*** be complicating the situation . . . and, also generally swap is "last" . . . .  First thing is OSX should be "at the top" which I think you have done, but any OSX install or upgrade needs to be done, before the linux, so if you did any OSX upgrade recently you would need to "re-bless" rEFInd to get it to work again.

If you can't get it to work from your other sources for my linux set up I just do the three partitions, 10MB flagged as "bios_grub;" . . . whatever you want for system and user as one partition, flagged as "/" . . . and set as "ext4"??  I think that's right; and then 1x to 2x RAM set as "swap" . . . .  After install, with rEFInd installed on OSX side, shut the computer down and then do a start up . . . that should get rEFInd properly oriented . . . .

e.e.p.

---

### Post by Tim_Johnson on 2014-09-30
Thanks again e.e.p. - I don't know how swap ended up as partition 4 instead of 6. I've done multiple installs using the same partitioning scheme, but with swap at the end.
Perhaps I made an error with gparted (likely) or there is a system corruption causing a misread (less likely). 

What would be the syntax to bless rEFInd?
I think that I have to find out how to set up refind.conf

---

### Post by este.el.paz on 2014-09-30
> **Tim_Johnson said:**
> Thanks again e.e.p. - I don't know how swap ended up as partition 4 instead of 6. I've done multiple installs using the same partitioning scheme, but with swap at the end.
Perhaps I made an error with gparted (likely) or there is a system corruption causing a misread (less likely). 

What would be the syntax to bless rEFInd?

@T_J:

It might not matter the order, but when working with the linux gods you can never tell what kind of mood they will be in . . . .  The re-bless thing I just did the other day, but I just copy/pasted it . . . I have a thread on the rEFInd discussion where I ask about "how to get rEFInd" working after OSX upgrade" and the reply was about his website "rodbooks" and saying "#8 is the question/answer" . . . so you could find my thread or you could look over his wiki . . . like I said, I don't know what I'm doing, I just follow instructions . . . .  If it doesn't show up for you, let me know here and I'll try to find the link.  It's easy enough, Terminal in OSX, . . . the bless command with the "EFI" pointer . . . .  His wiki is pretty thorough, just have to wade through to find it.

e.e.p.

---

### Post by Tim_Johnson on 2014-09-30
Aha! I see the discussion at [http://sourceforge.net/p/refind/discussion/general/](http://sourceforge.net/p/refind/discussion/general/) 
Will get on board with that and let you all how it turns out.
cheers

---

### Post by este.el.paz on 2014-09-30
[http://sourceforge.net/p/refind/discussion/general/thread/346ee733/](http://sourceforge.net/p/refind/discussion/general/thread/346ee733/)

Yeah, page 2 . . . same user name

---

### Post by Tim_Johnson on 2014-09-30
I haven't found your posting, but did find instructions in rEFInd wiki. Still no luck though, I've registered with sourceforge and will try to post a query directly to the developer.
rEFInd is locating my linux distro, but it just hangs when selected. I'm presuming there is something wrong the linux, as opposed to rEFInd, but I'm hoping that there is a way to boot with
rEFInd by referencing (or copying) from my linux boot -- (I've got fuse-ext2 installed so that I can read my linux partitions from OS X). 
To complicate things, following [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-mac-in-os-x--cms-21253](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-mac-in-os-x--cms-21253), I've created an install USB stick, but
that doesn't work either (sigh!). Sliding backwards here, 'cuz that is how I originally had 12.04 installed....
thanks for the help.

---

### Post by este.el.paz on 2014-09-30
> **Tim_Johnson said:**
> I haven't found your posting, but did find instructions in rEFInd wiki. 
To complicate things, following [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-mac-in-os-x--cms-21253](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-mac-in-os-x--cms-21253), I've created an install USB stick, but
that doesn't work either (sigh!). Sliding backwards here, 'cuz that is how I originally had 12.04 installed....
thanks for the help.

T_J:

I posted the link in #9 of this thread--it has the link to the wiki where "#8" is the answer.  Anyway, remain calm, there is always something going on in Linux, first thing, repeat after me, "OSX is not too bad on apple hardware" . . . it's the native system, it does a fine job . . . don't get into this "hating thing" . . . let that go.  All OSs have something they do well and something they fail miserably at . . . .

Next, so you are saying that your "bootable USB" is not booting?  Can you boot the 12.04 LiveDVD?  We first need to see if it's a "hardware" problem or a "software" problem . . . try to boot the LiveDVD you hold the C key on restart from OSX or whatever, and try to run the LiveDVD desktop . . . if that works, try to "nuke and pave" . . . from OSX DU erase the "linux" partitions and set them as "Free space" if you can . . . then run the linux installer and see if you can pick "automatic" "install into largest free space" option, and just let the installer run the show . . . if that doesn't work, then do "manual" but get the GRUB partition flagged . . . possibly rEFInd needs to hand the system to the GRUB boot interface . . . .  Keep trying, if it was working, it should  work again, just have to figure out what went off--possibly a kernel update??  You could try to fall back to an earlier kernel, etc, but for the most part 12.04 is very good . . . .



e.e.p.

---

### Post by Tim_Johnson on 2014-09-30
e.e.p.: I don't know what you mean by the LiveDVD desktop. I am not familiar with it. See [http://computers.tutsplus.com/tutori...s-x--cms-21253]("http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-mac-in-os-x--cms-21253")
I set up a Live _USB_ for 14.04 LTS as per those instructions but it doesn't boot either (as opposed to a successful boot of 12.04 earlier on rEFIt).
I am not into the "hating thing" - I find that Ubuntu suits me much better than OS X - and that is because 1) I am who I am 2) I am a developer for
open-source web apps and ubuntu is much friendlier to those programmers who like to do things their own way. 
I will try the following
1)Redo the Live USB and see if I can get that to boot.
2)Post to sourceforge/rEFInd (as you did) for a solution.
You gave me a thought tho' - problems did start after a kernel upgrade. One of the questions I will ask is how to reference an older kernel using rEFInd....
I still haven't had time to read the rEFInd wiki, so that is on my TODO list.
Thanks again. I appreciate all of the help that you have given me.

---

### Post by este.el.paz on 2014-10-01
> **Tim_Johnson said:**
> e.e.p.: I don't know what you mean by the LiveDVD desktop. I am not familiar with it. See [http://computers.tutsplus.com/tutori...s-x--cms-21253]("http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-mac-in-os-x--cms-21253")
I set up a Live _USB_ for 14.04 LTS as per those instructions but it doesn't boot either (as opposed to a successful boot of 12.04 earlier on rEFIt).
I am not into the "hating thing" - I find that Ubuntu suits me much better than OS X - and that is because 1) I am who I am 2) I am a developer for
open-source web apps and ubuntu is much friendlier to those programmers who like to do things their own way. 
I will try the following
1)Redo the Live USB and see if I can get that to boot.
2)Post to sourceforge/rEFInd (as you did) for a solution.
You gave me a thought tho' - problems did start after a kernel upgrade. One of the questions I will ask is how to reference an older kernel using rEFInd....
I still haven't had time to read the rEFInd wiki, so that is on my TODO list.
Thanks again. I appreciate all of the help that you have given me.

@T:

> Please help! Gawd, I hate using OS X, it runs like a broke-down animule compared to fluxbox on ubuntu, sheesh....

That was just humor . . . .  Alrighty, LiveDVD is one of the download options, or it will say "desktop" somewhere in the .iso . . . so if you have an "alternative" installer then the only thing it does is give you a GUI installer, no desktop apps, etc.  So, wherever you got the iso for your USB flash drive, was it for the "desktop"?  But, I'd suggest first getting 12.04 working again, before trying 14.04, which has its own learning curve.  If you can burn a desktop iso to a DVD and boot it up then you can look at software side . . . i.e, rEFInd issues, or new kernel, etc . . . although Ubuntu is pretty good about not breaking systems with upgrades, it could happen depending on dependencies you have.

But, rEFInd will not do anything for picking older kernels, that would be through Yaboot or GRUB, whichever gets installed with your 12.04, if it's Yaboot, then when you get to the Yaboot window, hit "tab" key and it will show "linux old" as an option . . . type that in and hit return.  If you don't have GRUB or Yaboot installed, you could begin there.

Hopefully you found my thread that I gave the link for in post #9???  It should link you to the wiki where the re-bless commands are shown???

e.e.p.

---

### Post by Tim_Johnson on 2014-10-01
Did find your link. Despite my hyperbole, Mac ain't all that bad for development and I have kept it in shape to quickly switch back to in case something happens on another partioned OS.
I believe that my ubuntu is seriously borked and in time I will either re-install 12.04 or go for 14.04. I don't expect 14.04 would be much of a learning curve for me. In the meantime,
I'm just going to stick with OS X, it pretty much works for me as does ubuntu, except that it _is_ a bit slower (and my wife says I should slow down anyway) and even though apt-get beats the heck 
out of macports, macports is acceptable. I intend to play with virtualbox a bit and try some guest linuxes (sp?) on it. 
Cheers
tim

---

### Post by este.el.paz on 2014-10-01
> **Tim_Johnson said:**
> Did find your link. Despite my hyperbole, Mac ain't all that bad for development and I have kept it in shape to quickly switch back to in case something happens on another partioned OS.
I believe that my ubuntu is seriously borked and in time I will either re-install 12.04 or go for 14.04. I don't expect 14.04 would be much of a learning curve for me. In the meantime,
. I intend to play with virtualbox a bit and try some guest linuxes (sp?) on it. 
Cheers
tim

Great.  Having a dual boot system is probably best for apple hardware.  Indeed 14.04 wouldn't be a learning for you, but maybe for your machine . . . you might need an xorg.conf file . . . .  But, right, these days I'm thinking that VB or Parallels or VMFusion . . . might be best for running other system, but inside OSX.

Take care,

e.e.p.

---

