---
title: "aircrack-ng on 2.6.25-ARCH w/ b43"
date: 2008-06-21
forum: Arch and derivatives
---

### Post by crimesaucer on 2008-06-21
Hello, I'm trying to learn about aircrack-ng and what I need to do to get it patched onto my kernel.


I have downloaded/installed this from the AUR: [http://aur.archlinux.org/packages.php?ID=14693](http://aur.archlinux.org/packages.php?ID=14693)


and I already have the newest b43 driver installed and configured to work correctly on the latest kernel.


My question is this: I'm not sure if I still need to add this patch onto my kernel: [http://www.aircrack-ng.org/doku.php?id=b43](http://www.aircrack-ng.org/doku.php?id=b43)


... and if so, I've never patched a kernel before so I'm not sure on the exact details (specifically for Archlinux), and the only guides I've found are for Ubuntu and Suse. 


I also ran this code from the page with no luck (the patch was still in my download folder because I did not know if I should have put it in a specific directory):

```
patch -p1 -i b43-injection-2.6.25-6-1.patch
```

as well as like this (probably wrong):

```
patch -p1 -i b43-injection-2.6.25-ARCH.patch
```



Any help is appreciated, thanks,
 -c

---

### Post by shearn89 on 2008-06-22
I managed to do this, with the same drivers (my card uses some b43 or something similar). It was, however, a complete pain. You do indeed need to patch the drivers and then rebuild the kernel.

I think I followed one of the howtos in the arch wiki, but I did the kernel building manually, not via ABS. I also forgot to add in the nvidia modules, so i have to test my wifi in full console mode!


Basically, what i did was:

mkdir /var/abs/local/mykernel

then download the kernel sources as described in the arch wiki. [link]("http://wiki.archlinux.org/index.php/Kernel_Compilation_From_Source#What_about_.2Fusr.2Fsrc.2F_.3F").
And I actually just followed that howto, but with a few slight changes:

1. I used a diff kernel version (maybe 2.6.24?)
2. Before you start the config stage, follow the steps on the aircrack website you linked to, up to "recompile your modules".
3. Go back to the arch wiki, and follow on until you get to make clean, make, etc.
4. I think i then made the modules themselves, as in the aircrack info, and then did make modules_install.
5. Continue with arch wiki.



If this is confusing, i have a pkg.tar.gz with the kernel i built, that works fine on my acer laptop (except no X). I have unfortunately deleted all the source files and the pkgbuild, which is a bit rubbish, but it works and puts my card into monitor mode, and i can test my security. Plus you look way more l33t with the console!

---

### Post by crimesaucer on 2008-06-22
Thank you for the info, I'm going to do a bit more research before I start.

thanks again.

---

### Post by crimesaucer on 2008-06-23
I did some more research and I ran into problems with the main.c file and the patch...

if you feel like checking out the details, here is my Arch thread: [http://bbs.archlinux.org/viewtopic.php?pid=384941#p384941](http://bbs.archlinux.org/viewtopic.php?pid=384941#p384941)

---

### Post by shearn89 on 2008-06-23
yeah, i've been reading through that while trying to make a decent pkgbuild for a new kernel. I've ended up doing it manually, and just copying the file into the /drivers/net/wireless/b43 directory during the pkgbuild. Not sure if it will work or not though. I'll let you know once its finished compiling...

---

### Post by crimesaucer on 2008-06-23
> **shearn89 said:**
> yeah, i've been reading through that while trying to make a decent pkgbuild for a new kernel. I've ended up doing it manually, and just copying the file into the /drivers/net/wireless/b43 directory during the pkgbuild. Not sure if it will work or not though. I'll let you know once its finished compiling...

Yeah, I was able to patch the xmit.c for the b43, and both the main.c and xmit.c for the b43leagay driver, but the patch is written incorrectly for the b43's main.c driver... so I stopped there until someone can help me manually write the correct patch to the b43 main.c...


And I spent a whole day searching google for any info on the b43 main.c and the injection patch, and it seems that most of the info on the web is for older kernel versions, and usually written for ubuntu...

---

### Post by crimesaucer on 2008-06-24
I'm getting nowhere with this. Here are my 2 other threads:

Arch forum: [http://bbs.archlinux.org/viewtopic.php?id=50678](http://bbs.archlinux.org/viewtopic.php?id=50678)
aircrack-ng forum: [http://tinyshell.be/aircrackng/forum/index.php?topic=3744.0](http://tinyshell.be/aircrackng/forum/index.php?topic=3744.0)

---

### Post by shearn89 on 2008-06-25
Yeah - everytime i try to tweak the patch, it says it's malformed. I think the last time i did it, i just let it fail, and then it worked, although i'm not sure how... I was building manually (without a pkgbuild) though, so i could continue with the other steps after.

i have to say, every time i've gone to the Arch forums for help, my posts just get ignored, or someone points me to something i've alread read 3 times on google.

---

### Post by crimesaucer on 2008-06-25
> **shearn89 said:**
> Yeah - everytime i try to tweak the patch, it says it's malformed. I think the last time i did it, i just let it fail, and then it worked, although i'm not sure how... I was building manually (without a pkgbuild) though, so i could continue with the other steps after.

i have to say, every time i've gone to the Arch forums for help, my posts just get ignored, or someone points me to something i've alread read 3 times on google.

Yeah, there aren't as many people in the Arch forums as there are on the Ubuntu forums. I find that the Arch forums are good for searching common problems with recent upgrades and configurations, but posting problems like the one I have usually don't get answered.

---

### Post by shearn89 on 2008-06-26
I solved it! it seems to work fine even if you don't patch main.c!

I let it fail, then just removed the main.c section from the patch file. Then I ran the makepkg, installed, built initramfs, and booted, and poof! it works! The only thing that doesn't seem to work is the airmon-ng, but you can use "iwconfig wlan0 mode monitor" instead, and it works fine...

Now i just need to get fbsplash working... gargh...

---

### Post by crimesaucer on 2008-06-26
> **shearn89 said:**
> I solved it! it seems to work fine even if you don't patch main.c!

I let it fail, then just removed the main.c section from the patch file. Then I ran the makepkg, installed, built initramfs, and booted, and poof! it works! The only thing that doesn't seem to work is the airmon-ng, but you can use "iwconfig wlan0 mode monitor" instead, and it works fine...

Now i just need to get fbsplash working... gargh...

Cool, I'm going to start over, and what I'm going to try is to edit the main.c part of the 2.6.25 patch, with the main.c part of the 2.6.24 patch and then I'll try to recompile the modules that way. I'll let you know how it turns out.

---

### Post by crimesaucer on 2008-06-27
I did it! I successfully patched and recompiled the kernel.


I downloaded the 2.6.25 kernel source, unpacked it, and then ran the b43-injection-2.6.25-wl.patch in the ~/build/linux-2.6.25 directory, and it will patch 3 out 4 drivers (xmit.c, b43legacy main.c, and b43legacy xmit.c) and then all you have to do is a manual patch for your b43 main.c file. (located at ~/build/linux-2.6.25/drivers/net/wireless/b43/main.c

I made mine just like this and it works, this is from line 2584 to 2608:

```

static int b43_op_tx(struct ieee80211_hw *hw,
		     struct sk_buff *skb,
		     struct ieee80211_tx_control *ctl)
{
	struct b43_wl *wl = hw_to_b43_wl(hw);
	struct b43_wldev *dev = wl->current_dev;
	int err = -ENODEV;

	if (unlikely(!dev))
		goto out;
	if (unlikely(b43_status(dev) < B43_STAT_STARTED))
		goto out;
	if (ctl->type == IEEE80211_IF_TYPE_MNTR) {
		ctl->flags |= IEEE80211_TXCTL_NO_ACK;
	}

	/* DMA-TX is done without a global lock. */
	err = b43_dma_tx(dev, skb, ctl);
out:
	if (unlikely(err))
		return NETDEV_TX_BUSY;
	return NETDEV_TX_OK;
}

static int b43_op_conf_tx(struct ieee80211_hw *hw,

```


... then (while still in your /build/linux-2.6.25 directory) you can run this command to get your .config file:

```
 zcat /proc/config.gz > .config

``` 

then you can do this code:

```
make oldconfig
```

and then this for your newly patched drivers:

```
make drivers/net/wireless/b43/b43.ko drivers/net/wireless/b43legacy/b43legacy.ko
```


...and then you copy and edit these two files from this wiki page: [http://wiki.archlinux.org/index.php/Kernel_Compilation_From_Source#2._With_makepkg_and_pacman_.28Recommended.29](http://wiki.archlinux.org/index.php/Kernel_Compilation_From_Source#2._With_makepkg_and_pacman_.28Recommended.29)

and place them both into your ~/build/linux-2.6.25 directory and then run:

```
makepkg -s
```

...and that will compile your new kernel with your new b43 drivers patched..,


then in root, just do:

```
pacman -U kernel26-my-2.6.25-1-i686.pkg.tar.gz
```

and you will have your new kernel installed... you might have to erase some conflicting files in /lib/modules/2.6.25-ARCH (I did, I was uploading all of the exact same files in my new kernel package anyway)


So, to anybody, I'm not sure if I did this the "real" correct and fast way, but I did get it working on my system (and learned a bit about patching kernels), so all I have to do now is actually learn what to do with airodump-ng and the rest of the tools.

---

### Post by shearn89 on 2008-06-28
awesome! If I can work out how patch files work, i'll try and re-write the patch...

As for how to use it, [this howto]("http://ubuntuforums.org/showthread.php?t=528276") was really useful. I just replaced the 1st step with 
```

ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

```
and it all works fine.

---

### Post by crimesaucer on 2008-06-28
> **shearn89 said:**
> awesome! If I can work out how patch files work, i'll try and re-write the patch...

As for how to use it, [this howto]("http://ubuntuforums.org/showthread.php?t=528276") was really useful. I just replaced the 1st step with 
```

ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

```
and it all works fine.



Hey shearn89, I found out why the patch was not working for the main.c....


I realize that I had been working with the wrong kernel26 source!!!!

I was using the 2.6.25 kernel source WHEN I SHOULD HAVE BEEN USING THE 2.6.25.6 kerenl source (that patched all 4 hunks with ease).


I'm in the middle of recompiling another new kernel... I realized I had done something wrong with my last one because I lost the ability to automatically mount cdrom cd's and dvd's and I also could not burn a data disk with my brasero app...


So, I started reading up on kerenels some more, and I realized that I had downloaded with this command:

```
 wget -c ftp://ftp.us.kernel.org/pub/linux/kernel/v2.6/linux-2.6.26.tar.bz2
```


when I should have downloaded with this command:

```
 wget -c ftp://ftp.us.kernel.org/pub/linux/kernel/v2.6/linux-2.6.26.6.tar.bz2
```


Sorry to everyone about that mistake...

All you need to do now, is download the 2.6.25.6, unpack it to a build directory, run the patch with no errors, add your old .config, run make oldconfig, run the make drivers command from my thread above, add the PKGBUILD and kernel26.install with the new version of 2.6.25.6 edited in, then use makepkg -c to clean old directories, and then install with pacman -U....


basically everything except the need to patch... and I used makepkg -c to clean things up a bit because it doesn't need "-s" (fake root) for and dependencies.



You also need to download the iw: [http://trac.aircrack-ng.org/browser/branch/iw?rev=1040](http://trac.aircrack-ng.org/browser/branch/iw?rev=1040)
.. (at least I had to do this), unpack it and then run make and make install... Now you get a mon0 to monitor from so you can still be using wlan0 for Internet.

---

### Post by shearn89 on 2008-06-29
ah! its so simple when you realise! dammit.. i feel like such a fool. The iw thing is handy too, as before i couldn't do anything at all when monitoring...

I'm in windows atm, but i'll let you know how my efforts go when i reboot.

EDIT: updatedb my pkgbuild, but its 1am here. I'm off to bed. will post info in morning!

---

### Post by crimesaucer on 2008-06-30
> **shearn89 said:**
> ah! its so simple when you realise! dammit.. i feel like such a fool. The iw thing is handy too, as before i couldn't do anything at all when monitoring...

I'm in windows atm, but i'll let you know how my efforts go when i reboot.

EDIT: updatedb my pkgbuild, but its 1am here. I'm off to bed. will post info in morning!

Be careful, I think I did something wrong when I installed the new kernel and the new modules... since it was my first time, I'm all most sure I did something wrong because I lost my cdrom's auto load, and burning ability...

Then I went and tried to change some modules by hand and totally ruined my Archlinux install... so I had to re-install!!!


Now I'm going for it again, and I just basically did the same way except after the patch, I made my first recompile command this:

```
make mrproper

``` 

then I went with:

```
 $ zcat /proc/config.gz > .config

```

```
$ make oldconfig   
```

```
make drivers/net/wireless/b43/b43.ko drivers/net/wireless/b43legacy/b43legacy.ko
```

... but now I'm not sure of what to do so that I don't ruin my cdrom and anything else in the process???


seriously, be careful if you don't want to lose your data... I lost my Archlinux of 30GB's and then my grub wouldn't let me into my 30GB's of Windows Xp where I stored all of my music... then I tried to repair it with my Windows repair disk, and then I ended up ruining that partition also... and now my HP laptop wont even boot into my Windows Xp cdrom... 


so now I only have linux, I guess I had to get rid of the Windows one of these days anyway... or learn how to use vmware.

---

### Post by shearn89 on 2008-07-01
okay... Well i'm still good - i read the warning before compiling. I'm going to spend some time seeing if I can get a pkgbuild working with the arch patches, the b43patch, and perhaps i'll search for some others. It would be cool to have a totally custom kernel.

---

### Post by Joker5bb on 2008-07-01
guys try out the wireless testing kernel.

latest is 2.6.26-rc8-wl

```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/linville/wireless-testing.git
```

and compile the kernel 

and use these patches

[http://patches.aircrack-ng.org/b43-injection-2.6.26-rc8-wl.patch](http://patches.aircrack-ng.org/b43-injection-2.6.26-rc8-wl.patch)
[http://patches.aircrack-ng.org/mac80211_2.6.26-rc8-wl_frag.patch](http://patches.aircrack-ng.org/mac80211_2.6.26-rc8-wl_frag.patch)

---

### Post by shearn89 on 2008-07-01
thanks man. Looking at it, it makes sense to use the -wl kernel for the 2.6.25-**wl** patch doesn't it?

---

