---
title: "Installing XUbuntu as second boot..."
date: 2008-04-04
forum: Apple PPC Users
---

### Post by veganjustice on 2008-04-04
Okay, I have an iBook that is a YDL laptop, I have an 80g hard drive already partitioned into two separate parts, other than the boot and swap partitions... Anyways... I have 40 for YDL, and I wanted the other 37 or whatever for XUbuntu, I have never had just a dual boot Linux machine, so Not sure how to function around installing it on that partition, making sure I don't screw up the boot screen.

A little update... I went ahead and popped the XUbuntu disc into the machine to try and install on that second partition. I got to the partition menu, saw all the partitions, the boot part. the swap, and the two I created. One having YDL on it... so I chose to have the second partition formatted so I can install Ubuntu onto it, and it said it was going to make changes to that and the swap partition, said OK. and then it gave me a warning that no Root Device was selected, to fix it back at the partitioning menu. Any idea what I did wrong?

Anyone offer up any assistance? 

Thanks...

---

### Post by stream303 on 2008-04-05
I'd probably go for the easy route - just leave that 37mb left over as "free space".

Then let the Ubuntu installer use guided partitioning to install to the free space and automatically do all the partitioning for you, as well as detecting the YDL install which it would put into the yaboot menu as an option when booting up.

At least, this is how it is supposed to go. :)  Definitely do a backup!

---

### Post by veganjustice on 2008-04-05
That does sound easy, but it isn't partitioned as free space, from when I partitioned it at the YDL install. Can I erase it and leave it as free space from the Xubuntu installer? Then install it? :confused:

Thanks!

---

### Post by stream303 on 2008-04-05
I believe so.  This time with Ubuntu, go into manual partitioning, and just delete the 37mb partition, and then use the go-back feature by tabbing to start again with guided partitioning for free space.

It's been awhile, so I'm not sure if when you use manual partitioning to delete the 37mb partition, you have to actually go ahead and write the changes to disk, and then do the go-back...

---

### Post by veganjustice on 2008-04-05
I will go ahead and try this later. I am about to leave the house, so I can't try it now. But thanks a lot. I'll keep you updated. Thanks!

---

### Post by veganjustice on 2008-04-06
I deleted it and made it free space, and then went back and started the install. All is working fine. It is installing now. Let's just hope that yaboot recognizes them both and all is well. 

I'll let you know. Thanks

---

### Post by stream303 on 2008-04-06
Great!  Look forward to the results.

Hopefully  you won't have too much of a hard time and have to resort to passing kernel parameters at boot, editing the yaboot.conf and following up with ybin, or editing your xorg.conf for screen resolution issues.

If they do show up, we can tweak those, but at least now Xubuntu for the most part should be properly installed to your disk.....

---

### Post by veganjustice on 2008-04-06
Okay, XUbuntu installed fine, but at the boot menu, I have 2 options. L which is GNU/Linux and c which is CDRom... L used to be YDL. No longer. 

After I choose L, it takes me to the second part, I hit help, then TAB, and it says Linux                OLD              hda3-Yellow
So I am not too sure what is going. 

It was suppose dto only format free space and the swap partition. So YDL should still be on that first 40g partition. But my boot menu doesn't let me choose it.

What next? hahaha. Thanks!

---

### Post by ubuntubrian on 2008-04-06
I'm really curious to see the outcome of this. I tried 2 Linux distros, Fedora and Debian and Yaboot did not handle it well and I lost Fedora completely. I have read quite a few posts that deal with Yaboot and it seems that it is quite important to run ybin after any modification of yaboot.conf,manual or otherwise.
I'm too chicken to try this without really detailed instruction.
Good luck though!

---

### Post by stream303 on 2008-04-07
> **veganjustice said:**
> After I choose L, it takes me to the second part, I hit help, then TAB, and it says Linux                OLD              hda3-Yellow

Cool.  Now when you hit tab to see your options, if you want to boot YDL, just type
```
hda3-Yellow
```

at the boot:  prompt.  This will boot the YDL kernel.

Once you have it memorized, you don't need to hit tab anymore, just type hda3-Yellow for ydl.  Otherwise, you can type Linux to boot to Ubuntu kernel, or you can just let both prompts time-out and it will take you to Ubuntu automatically.

---

### Post by stream303 on 2008-04-07
> **ubuntubrian said:**
> I'm really curious to see the outcome of this. I tried 2 Linux distros, Fedora and Debian and Yaboot did not handle it well and I lost Fedora completely. I have read quite a few posts that deal with Yaboot and it seems that it is quite important to run ybin after any modification of yaboot.conf,manual or otherwise.

Yaboot should handle it pretty well if both installations are on an internal drive, and aren't trying to use a dual-hd driver that is in some G5 towers, or using an external firewire that mandates manual intervention of yaboot.conf.

I'd keep it simple at first - for example, I'd just cut the drive in half so to speak.  I don't know how Fedora handles partitioning, but I'd just try to use the most automatic option and use a slider (or whatever they use) to select only half the drive to install to.

Then, install Debian on the other half, this time using guided partitioning (not manual) and install to the rest of the free space.  If all goes well, yaboot should detect the fedora install along with Debian, and at the boot: prompt, you'll be given a choice.  Ybin (and mkofboot) are really only needed if yaboot install fails, and when changing yaboot.conf's parameters to make the system aware of changes.

You can see that the last Linux that is installed, ends up being the default kernel booted if you do nothing at the yaboot prompts when it times out.

---

### Post by mjp216 on 2008-04-07
did you format the partition?

---

### Post by veganjustice on 2008-04-07
Yeah, that is exactly what I thought... I typed hda3-Yellow first time I saw that, and all it does is reboot back to the original boot menu. When I type it, it goes through the initializing, like normal for YDL, then at the end, it says WARNING: Unable to open console or something like that then restarts...
Something else that might work? Thanks

---

### Post by veganjustice on 2008-04-07
> **mjp216 said:**
> did you format the partition?

Yes, when I first installed YDL a while back on this iBook, I split the partition because I knew I eventually wanted this to be a dual boot laptop... I ended up formatting both partitions. YDL was fine, I got around to installing ubuntu, and it wouldn't work. So as it was suggested, I deleted that second partition and left as free space, then chose the 'go back' feature and then went through the guided partition of free space, and all went fine. It started installing, and then it was fine. It default boots into XUbuntu, which is fine, no problems, but I can't get into YDL when I type hda3-Yellow. IT just reboots the computer back to the boot screen. 
That YDL partition wasn't touched on the install of Ubuntu, just the free space partition and the swap partition.

Any ideas?

---

### Post by veganjustice on 2008-04-09
So I went ahead and started over. I did a back up, then I put the YDL disc back in, of course when it scanned for previous installs, it found it, but since I can't boot into it, I went ahead and did the fresh install. Erased both partitions, split them down the middle, made the second partition all free space, well, made both free space, then installed YDL on the first one, went through the install, booted fine into the OS afterwards, then I ran the Xubuntu disc, I followed Guided partitioning this time for free space, all went well, but at the boot menu, I ONLY have GNU/Linux, I hit L for that, it shows Linux old hda3-Yellow.

I can hit enter again for Ubuntu, or I can type hda3-Yellow, when I do that, it flies through all the script it lists, then at the end, the computer reboots right back to the original boot menu.

My Yellow Dog Partition won't boot, it is there, I know, but won't boot. 

Any ideas? Thanks


Jordan

---

### Post by oswaldkelso on 2008-04-09
[http://www.intuitive.com/blog/ubuntu_linux_yellowdog_linux_and_mac_os_x_all_on_one_powerbook.html](http://www.intuitive.com/blog/ubuntu_linux_yellowdog_linux_and_mac_os_x_all_on_one_powerbook.html)

this is a bit old but may help . I recently had a play with other ppc distros Just to see how they were. Yellow dog 6, fedora 8 and hardy heron. fedora worked fine, yellow dog had some minor problems but borked my osx boot partition! and hardy heron installed fine but failed to create a boot partition. I fixed it with the debian net install cd I had lying around buy using it to right the partitions then quiting out something I could not get hardy to do (though I could with the worty alt cd) Hardy installed fine then.   

[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

