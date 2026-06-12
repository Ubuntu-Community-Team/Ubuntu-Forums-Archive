---
title: "I think I busted my kernel"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Wayno-san on 2007-11-28
Not sure how this happened but my most recent kernel listed in GRUB (2.6.22-14-generic) no longer works.... Basically when I select it it goes into the Graphical Boot screen with the ubuntu text and "thermometer".  The thermometer gets almost half-way to the first notch and then the screen goes black and I get dumped into "BusyBox v1.1.3" with a (initramfs) prompt.  As far as I see there are no error messages or hints of what went wrong.  I have no idea what to do at this point.... up until now the updated kernels get magically added to my GRUB when Ubuntu updates itself and I'm happy as a clam to load in, and use, the latest and greatest kernel.

What's the easiest way to fix this situation?  I can still boot into the older kernels....

Thanks!

ps:  I did put an effort into trying to use the search command but I guess I'm not sure what exactly it is that I need to look for.  I tried doing up update-initramfs of that kernel version but that didn't have any positive effect.

---

### Post by BlocknBleed on 2007-11-28
I don't know enough to really help but I do know you can boot up using the liveCD and try to troubleshoot from there. At least then you can get inside your system and have a look.

from what I understand the linux kernel is "unbustable". You would have to do something legendarily stupid to damage it. It's probably not as bad as it looks.

---

### Post by Wayno-san on 2007-11-28
I agree, it's probably still there, but for some reason, just doesn't want to load.  I did try the liveCD but I don't see much in terms of diagnosing an installed Ubuntu... and I don't know enough about Linux to know where to start...   I'm learning though!

---

### Post by Mister.Vash on 2007-11-28
It could be that a file system check is occurring on your drive ( fsck ).  To see what is happening, on the console while your system is booting, do the following:

( Source [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) )

Modifying boot options in GRUB

    *

      If you need to get into the grub menu, to modify boot options or choose a different kernel, you need to press 'ESC' just after it starts. By default you have to press 'ESC' very quickly. To increase this time edit /boot/grub/menu.lst, increasing the seconds in the TIMEOUT part. Alternatively you could have the menu always come up at boot time. To do this, comment out 'hiddenmenu' by inserting a # at the beginning of the line.

      After pressing 'ESC' you will be presented with a list of kernels and operating systems that you can boot. To modify the boot options highlight the operating system you want to edit and press 'e'. There you will be presented with lines starting with 'root', 'kernel', 'initrd', 'quiet' and 'savedefault'. **To receive a more verbose boot process you can remove the 'quiet' line by highlighting it and pressing 'd' to remove that line. You will also need to highlight the 'kernel' line press 'e' to edit and remove the word 'splash' from the end of the line . After making any necessary modifications you can press 'b' to boot that operating system. These modifications will not persist across reboots. **




The options that you want to try are removing the splash and quiet so you can watch the console as the system boots.

---

### Post by nikoPSK on 2007-11-28
press esc or whatever it says at startup and choose a different kernal to fix your problem. This might not work.

---

### Post by Wayno-san on 2007-11-29
OK, I enabled verbose mode per suggestion above and here is where it looks like it stops:

```

Running /scripts/init-bottom

mounting /root/dev on /dev/.static/dev failed
No such file or directory
mounting /sys on /root/sys failed
No such file or directory
mounting /proc on /root/proc failed
Target file system doesn't have /sbin/init

```

Any ideas?  I can boot into a couple of older kernels no problem so I can troubleshoot from there if anyone can guide me.

Thanks!

---

### Post by Wayno-san on 2007-11-29
I could really use some help with this because I noticed that when I run the older kernel my CPU utilization does not fall below 50%.  Basically one core will run near 100% and the other near 0% and then they'll switch back and forth like that.  I looked at the task manager and nothing there was showing running with a high utilization but the system is acting VERY slow....

---

### Post by nikoPSK on 2007-11-29
did you run any malicious commands? say an rmrf something?

---

### Post by Wayno-san on 2007-11-29
Dont' know what rmrf is!  LOL!  I only ran "Swiftweasel" during that session an I even closed that down but was still getting the crazy high utilization.

Is there a way to force Ubuntu to perform an "auto" kernel update?

---

### Post by nikoPSK on 2007-11-29
rm rf will remove your ubuntu system. Did you maybe (or an app) execute a fork bomb? I know apps under development can accidentally execute fork bombs.

---

### Post by Wayno-san on 2007-11-29
No idea what a "Fork Bomb" is either... 

:(

---

### Post by nikoPSK on 2007-11-29
executes one process which executes two processes which in turn execute 4 processes. Happens very fast and can badly mess up something.

---

### Post by Wayno-san on 2007-11-29
Is there a way to force my Ubuntu to upgrade from Feisty to Gusty again?  That way I can boot into the older kernel and hopefully it will correct whatever is messing up my newer load...

No, I don't think it was a Fork Bomb.  I think then both my cores would have jumped to 100% CPU utilization.... correct?

---

### Post by nikoPSK on 2007-11-29
correct, if your back in fiesty just do this:

```
#update-manager -c -d 
```

---

### Post by Wayno-san on 2007-11-30
Upgrading to version 8.04... keeping my fingers crossed.

---

### Post by nikoPSK on 2007-11-30
8.04? uhh, thats feisty.

---

### Post by Wayno-san on 2007-11-30
Nope, "Hardy Heron" Alpha.  I think you were thinking 7.04.  It's what came up when I typed in "#update-manager -c -d".

---

### Post by nikoPSK on 2007-11-30
oh, well good for you! I should get hardy.:)

---

### Post by Arthur Archnix on 2007-11-30
This was confusing. Were you running a feisty system and then did a dist-upgrade to Gutsy? If you are actually trying to get a hardy system up and running then you should direct problems to testing, there is sure to be a forum on here devoted to those wishing to run and test Hardy.

---

### Post by Wayno-san on 2007-11-30
No I had Gutsy, I was just trying to get my latest kernel working... but since I didn't know/couldn't figure out how to fix it.. I "updated" my Ubuntu.... 10 minutes remaining on the install... hopefullly it won't explode.  8-[

BTW, I'm assuming this will update my kernel.  That might be a bad assumption but my moneys on it now and the roulette table is spinning....

---

### Post by meierfra on 2007-11-30
edit:  deleted.  didn't read the latest post

---

### Post by Wayno-san on 2007-11-30
Well, I'm glad that that wasn't real money because I would have lost.... No new kernel and the 2.6.22-14-generic still crashes on bootup into BusyBox... :confused:

---

### Post by nikoPSK on 2007-11-30
so it's still dead?

---

### Post by Wayno-san on 2007-11-30
Yeah, I'm trying to do more searching on the forums/google to see if I can find a way to fix this.  Additionally, the Hardy ended up hosing my NVidia setup when I tried to enable Compiz so now my second kernel isn't booting up either... LOL!  
At least I'm pretty sure I can fix that problem though...

---

### Post by ptn107 on 2007-11-30
Happened to me on my laptop.  All I did to fix it was boot an older kernel and run this in a terminal:
```
sudo apt-get install --reinstall linux linux-generic linux-image-generic linux-headers-generic linux-restricted-modules-generic -y
```
and boot back into 2.6.22-14-generic afterwards.

** I did have issues when compiling custom kernels afterwards, but if you don't do that kind of stuff then don't worry.

---

### Post by nikoPSK on 2007-11-30
well, if you don't have anything important, just wipe your hd and de a clean install of gutsy.

---

### Post by Wayno-san on 2007-11-30
ptn107, 
I tried your suggestion... it looks like the command completed successfully but unfortunately it still stops booting and dumps me into BusyBox when I try the latest kernel.

nikoPSK,
I don't have a lot of important data on the OS but I did spend a lot of time getting it set-up.... I'll keep looking for a solution for now.  Who knows, this might happen again sometime in the future... would be nice to know how to fix it.

---

### Post by nikoPSK on 2007-11-30
well, I've reeinstalled gutsy 5 times since, 40 minutes for the installation. 10 minutes to set up the tv on it and set my Soundblaster audigy as default card. Not too bad. So I'd say go ahead. (up to you.)

---

### Post by Arthur Archnix on 2007-11-30
After a clean install of Gutsy and applying all updates, which I did last week, I'm running the 2.6.22-14-generic kernel. No special updates were required. I'm sure someone will correct me if I'm wrong, but I believe this is the same kernel it shipped with.

So, I guess what I'm asking is, are you having trouble getting the 2.6.22-14 kernel to run, or are you trying to install some other kernel? If so, which one and what instructions are you following to do so? Or is this an upgrade from Feisty? In which case, I say backup data, wipe clean, do a clean install of gutsy.

---

### Post by Wayno-san on 2007-11-30
I can't get the 2.6.22-14-generic kernel boot option to boot up.  I think I will do that clean re-install.  My biggies were getting my graphics card and monitor to work (there was something about it not liking certain frequencies [Viewsonic v2025wm), then I think I had some issues with the sound card (SB Audigy 2), getting the extra buttons to work on my Logitec MX500 mouse, and finally setting up my printer.  For some reason CUPS didn't like me using my printer through the print server on my router (D-Link 714P+).  Took me a while to get those up and working.  This time I'm going to back up the partitions....

---

### Post by nikoPSK on 2007-11-30
well, hopefully everything goes well, good luck and bon voyage!

---

### Post by Wayno-san on 2007-12-01
Thanks bro, I appreciate your efforts to help me.  One day I will learn the secrets of Ubuntu... :)  Until then... it's re-install time!

Peace, out.

---

### Post by nikoPSK on 2007-12-01
Good luck and I hope you don't have any more problems! 

PS This happened three times: I was in gutsy, I used eny to get my GPU drivers and It destroyed my x-windows system. I did that three times....

:lolflag:

---

