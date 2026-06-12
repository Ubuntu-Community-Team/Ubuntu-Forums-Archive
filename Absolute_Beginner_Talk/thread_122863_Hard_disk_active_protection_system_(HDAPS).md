---
title: "Hard disk active protection system (HDAPS)"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Zeno Cosini on 2006-01-28
I am using Ubuntu Breezy on an IBM Thinkpad T43. What do I have to do in order to use the hard disk active protection system? Some web pages (e.g., [http://www.cs.ust.hk/~joseph/Favorites/Debian/UbuntuOnIBMThinkpadT43.html](http://www.cs.ust.hk/~joseph/Favorites/Debian/UbuntuOnIBMThinkpadT43.html)) seem to imply that I have to recompile the kernel, while I have also found indications that newer kernel versions already include the necessary drivers etc. However, all the instructions are found are sketchy at best. Can anybody shed a light on what I actually have to do? Thanks.

---

### Post by blackphiber on 2006-04-26
looks like the driver is in recent kernels, but the patch to actually protect the disk is not yet.  read the following to get it going.
[http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS]("http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS")

*EDIT:
I could not get it going by just installing those packages. I emailed the guy running the repo and he says you still have to patch the kernel since it is not in the mainline kernel yet.  here is the email:

> Hey, thanks for providing a nice little repository for thinkpad users.
> I am using ubuntu, and having a bit of trouble with hdaps, on
> [http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS](http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS)
> I installed all the packages they say to install, but when I search
> for hdaps_protect it is not in the repository and I am guessing that
> is what is causing it to not work for me.

You need a special kernel patch that adds the ability to freeze and
queue writes to the hard disk while the APS system is activated. It
hasn't made it into the mainline kernel yet for various reasons.
ThinkWiki calls the patch hdaps_protect, but my packages call it
kernel-patch-queuefreeze. The init script for the hdapsd daemon will not
start the daemon if it doesn't detect this patch (it looks for a special
file under /sys). Currently, if you wish to use HDAPS, you must build a
custom kernel. This is what the kernel-patch-queuefreeze package is
meant to facilitate. You can use Debian's kernel-package software to
automate the process of building a patched kernel. This is what
kernel-patch-<foo> packages are for. So, install kernel-package and
kernel-patch-queuefreeze, and then read the manual page for make-kpkg
for information on how to build a kernel with patches. The particular
kernel-patch-queuefreeze version available will build on 2.6.14 or
later, but you really should use 2.6.15 or later, especially if you have
an SATA disk.

Hope this helps,
Andrew Barr

---

### Post by TekNullOG on 2007-02-13
I run Ubuntu 6.06 on an old desktop but have hesitated about putting it on my IBM T43 which runs Windows XP Pro.

1- My main concerns are getting the Active protection system to work since it doesn't seem very simple and I am far from being a Linux guru. In the previous post, I read:

> You need a special kernel patch that adds the ability to freeze and
queue writes to the hard disk while the APS system is activated. It
hasn't made it into the mainline kernel yet for various reasons.


Has this been added yet? This was posted 1 year ago. Are the installation and configuration easier?

2- The next thing I was worried about was the fingerprint software. After reading [this page]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader") I got discouraged and decided I can live without it! Does anyone know of an easier way?

3- Finally, I have a docking station with TONS of things plugged to it. Will my second screen work properly even if the resolutions are different? I have found tons of people with this problem in the forums but no one seems to have a solution.

I know I mentioned a few extra things (other than the hdaps) but hopefully, someone has an answer or 2.

Thanks

---

### Post by MCC on 2007-02-25
It has!

Simply "sudo modprobe hdaps" and HDAPS support will be enabled. Now just to get it to stay that way...

Edit: NVM, that lets me view the sensor data but won't let me stop the disk.

---

### Post by cb474 on 2007-02-26
Is there a patch for disk head parking and kernel freezing (hdaps_protect) for 2.6.17-11? If so can anyone explain how to download this and apply it to the kernel. I looked at the directions on ThinkWiki and they're a bit over my head. I wasn't even sure if I would be okay to use the patches linked to there. I'm trying to do this on a T60.

---

### Post by iamhimay on 2007-02-28
Hi all,
 
This is very possible to do. I'm reading up on it to make sure. Building a kernel is not a big deal. However, if you have a machine with the proprietary ati driver and also perhaps the madwifi wireless driver, that adds another level of complication. Those drivers are provided in Ubuntu by the linux-restricted package, and in a standard install you get a version that matches your installed kernel. So if you build a kernel, you have to account for this problem and get those drivers. You can either rebuild the restricted modules package to match your new, patched, kernel, or you can build the patched kernel and then build the fglrx and madwifi drivers from source and then disable the linux-restricted modules so the o.s ignores the non-matching driver modules. This is because you must have the linux-restricted package installed regardless of whether you use its drivers or not. The other issue is that with the fglrx driver there are different versions that may or may not lose features or interfere with things like suspend/resume.  I'm on feisty now, which is pretty stable with fglrx version 8.33.6 and kernel 2.6.20-9. So I'm loathe to start messing around with kernels and modules. I will probably wait to see how the distro shakes out and then once it's relatively final, start playing with hdaps and tp_smapi stuff. I did boot my xp  (on a t60, btw) for the fifth time since I got it, just to play with the hard drive parking and also to observe the fan behavior under a different o.s. It would be cool to have this head parking functionality in Linux. 
I highly recommend the kernel-package way of building kernels, since you can install different kernel versions easily with it. I'll post back here when I have it all working.

---

### Post by cb474 on 2007-03-02
Thanks for the explanation. If you have the time and the inclination, when you get it working, I would be grateful for a step by step explanation. I'm a newbie and don't think I could do all the things you explain on your own.

I did install the latest fglrx driver and compile the kernel using method 2 in this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.34.8_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.34.8_Driver_Manually)

So I assume I could just follow that again?

But the part about building the madwifi drivers from source and the linux-restricted modules is a bit over my head.

I guess one question I still have is if it's possible to patch the Ubuntu kernel I currently have for the hdaps, wihch is 2.6.17-11, and that way avoid having to do all the steps you mention to get fglrx and madwifi to work?

Thanks.

---

### Post by airbornespent on 2007-08-10
[This guide]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Disk_Protection") on the thinkwiki site is good, I followed it and my system rebooted with the new kernel seamlessly.
A bit of warning though is that I haven't gotten hdapsd working yet, I can manually pause the disk by issuing ```
sudo -s
echo 1 > /sys/block/sda/queue/protect
``` but the daemon is giving me trouble.
All this is supposedly going to be in gutsy (you might have install it through apt-get/synaptic) but that would be much easier than the way it is now.

EDIT: I got the hdapsd working! There is a note on the thinkwiki page I linked to above that mentions using gcc-3.4 to compile hdapsd, I ignored it at first but then I checked synaptic. You must install gcc-3.4 then when compiling hdapsd use:```
gcc-3.4 -o hdapsd hdapsd-*.c
sudo cp hdapsd /usr/local/sbin/
```

At this point you can run the command "hdapsd" to see the options, ex. "hdapsd -d sda -s 15" 

Now I simply need to figure out where is te best place to start the daemon on startup. rc.local is one place, but I'd personally like it to start ASAP after boot, which means as close to when the tp_smapi modules are loaded as possible.

---

### Post by ihavenoideax2 on 2008-02-06
I have a T61 with everything else working but APS. I know very little about kernel modules or how to implement it into mine. I am running 7.10 and i installed ts_smapi using [this guide]("http://www.thinkwiki.org/wiki/Tp_smapi"). Is there anyone who knows how to fully install it and implement it? Also is there a GUI way of managing it?

---

### Post by airbornespent on 2008-02-11
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Disk_Protection](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Disk_Protection)

That is what I followed. It is written for 7.04 but it should work for 7.10 as well. Your names  for the installation step will be different. The current kernel is 2.6.22-14 so if you are all updated you can replace 2.6.20.3 with 2.6.22.14

If you have restricted modules you'd need to compile those according to the instructions. Do all that and it should work. If you need any more help just post I'll be checking back on the thread.

---

### Post by gigaboom on 2008-02-18
Thanks to all for the info. 

I'm a 20+-year programmer in a wildly different field, and after close to 10 years of off-and-on playing with various Linux distros, mostly in frustration, and finally abandoning all my ATI graphics cards (and my Palm, pretty much), I seem to have Ubuntu 7.10 doing everything (remaining) that I need an OS to do on two desktops... if we ignore the color scanner for the moment, which I am. Breakthrough. 

Now I'm researching in preparation for installing it on my Lenovo T60p. Despite having programmed in a few different venues, I admit to being a bit daunted- every post I come across that discusses re-compiling the kernel seems to lapse into ancient Aramaic.. or maybe Urdu?.. usually right after a phrase like "it's really very simple"... maybe it's Hittite, hard to tell... and then there's a spattering of broken links, and/or links to posts having to do with different hardware entirely. Very confidence-inspiring.

I've compiled a lot of programs in my time, and I think I can get it at least to the point where I can tell that my attempt to re-compile a kernel didn't work, and fall back to the previous one, one way or another. We'll see.

Basic question that shouldn't require any exotic languages... say, for the sake of argument, that I get the notebook dual-booting, somehow scrape together enough detailed info to get a kernel re-compiled with HDAPS and whatever proprietary drivers I'm barely aware that I'm using (I don't really "get" that part- presumably they weren't compiled into the kernel BEFORE, since they were installed on top of it), and it all actually works. 

Ubuntu sort-of-spontaneously decided just recently to upgrade to kernel 2.6.22-14. I'm guessing the next time it does that, I'm back to square one? Is there any reassurance that the same patches (which seem to lag considerably behind the "stable" kernel releases) will work with the updated kernel if I try to repeat the feat? Or should I be holding back somehow on kernel upgrades to try to keep them in sync with available patches? Or do I just try to re-compile each time and see what breaks?

---

### Post by airbornespent on 2008-02-20
When you compile a custom kernel and follow the steps on that page, it is set as the default in grub. When a new kernel is released, and the kernel sources, you'd need to recompile it with the hdaps patch. Usually though, there is no big reason to switch to the newest kernel if the one you compiled is working fine and has all the features you need. Recompile and upgrade if you find out a newer kernel has something compelling enough to switch for.

---

### Post by EarloftheWest on 2008-05-02
airbornespent,

Have you gotten it working under Hardy?

I'm going to give this another try. It was the hdapsd that was giving me trouble.

How many times have you done this with success?

---

### Post by chchandler on 2008-05-12
So, if I understand correctly, the 8.04 includes HDAP installed but not turned on, and it just monitors acceleration.  The drive parking isn't yet available without re-compiling the kernel?

[http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS](http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS)

seems to say this.  Will these be folded into a later release of HH or are they forever destined to be the province of daring kernel kompilers?

---

### Post by shanepardue on 2008-07-18
I'm also interested in this, but it looks like kernel modding is the only answer. bleh

---

