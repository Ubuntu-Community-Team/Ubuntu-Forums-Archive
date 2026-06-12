---
title: "G4 Mac Mini - issues with X on livecd"
date: 2008-01-21
forum: Apple PPC Users
---

### Post by scruff on 2008-01-21
I can't seem to get X to load using the latest Gutsy livecd. This bix has a Radeon 9200 in it. During boot, I get stuck on "running local boot scripts...", but if I alt+F2 to get a new term and type startx, I get the "screens found but no usable modes" error. I've edited xorg.conf to KNOWN modes for this card and my monitor (1280x1024, 1024x768, 800x600) but I get the same error. 

Any suggestions? I also tried the video=ofonly at the yaboot prompt. Crazy that this CD doesn't boot on such a common machine...

---

### Post by scruff on 2008-01-21
I also tried 'radeon' as a alternative driver, no dice. 

I'm downloading 6.10 right now to see what happens. This box is mainly for the wife and kid to play on so the version isn't all that important. I run Gusty on my Thinkpad and Gentoo on my server so might as well add another to the mix...

---

### Post by BladeMelbourne on 2008-01-21
Hey scruff,

I have had no luck running Ubuntu live CDs on my G4 Mini, although I have only tried a few times.

I know for a fact that the ATI Radeon driver included with both Gutsy and Hardy do not work on the G4 Mac Mini.

This won't work with Hardy, however it does for Gutsy. This is for installing Xubuntu/Ubuntu/Kubuntu 7.10 to hard disk, not live CD operation.

1) Search for and download "xserver-xorg-video-ati_6.6.3-2_powerpc.deb" to a USB thumb drive.

2) Download and burn the alternate CD. Install to a partition on your hard disk.

3) On first boot, when asked to select which Linux kernel you want to boot with (the default option is usually 'Linux'), type 'Linux single text' and press enter. (Note: I don't think 'text' is a valid option, but it doesn't hurt)

4) When the root prompt appears, mount the USB thumb drive ('mkdir /media/disk' then 'mount /dev/sda1 /media/disk') , change to the mount point directory ('cd /media/disk'), and type 'dpkg -i xserver-xorg-video-ati_6.6.3-2_powerpc.deb' and press enter.

5) Then run 'telinit 6' to reboot and hopefully X will be working. 

If this is too complicated for you, I suggest using Feisty - which does have working drivers.

Regardless of Gutsy or Feisty installation, when using Synaptic to update your packages, never select and update the xserver-xorg-video-ati driver to a newer version.

If you get it working, I should be able to provide you with an xorg.conf with decent OpenGL performance. Don't expect to run compiz-fusion at 1280x1024 at 24 bit colour - there is not enough video RAM on the 9200. You can do 1280x1024 at 16 bit colour, or 1024x768 at 24 bit colour.

HTH

---

### Post by scruff on 2008-01-21
Thanks HTH. I can't find my thumb drive so I'll just give Feisty a shot. I don't plan to run compiz-fusion. I hear enough complaints about slowness from these two :)

---

### Post by microft on 2008-02-19
Hi, I'm considering turning my Mac mini over to Ubuntu, as my work-machine/thin-client.
However, I can't get a definite answer on what resolution it's possible to get with the linux drivers.

So... can any of you clarify my doubt?

Thanks, your posts helped me alot!!

---

### Post by BladeMelbourne on 2008-02-19
You should be able to get the same resolutions available under OS X.

I can't recall whether the mini supports 1920 x 1200, but it wouldn't go higher than that.

My mini is outputting 1280x1024 to my 19" screen.

---

### Post by microft on 2008-02-21
On [everymac.com]("http://www.everymac.com/systems/apple/mac_mini/stats/mac_mini_g4_1.5.html") it says that the ppc mac mini supports 1900x1200 (using DVI).
That's my target resolution, since it's my new (future) monitor's native resolution. If I can get that resolution under Linux, even better! I can stop using Mac OS X.

---

### Post by BladeMelbourne on 2008-02-21
I was pretty sure it was capable of a resolution that size.

I am fairly confident that the open source ATI radeon driver will get you 1900x1200. The only caveat is compiz (3D/rendered desktop effects). At 24 bit colour, a display adapter with 32 MB RAM at 24 bit colour can only manage 1024x1024 at the most.

Thus I (at 1280x1024), and you if you proceed, will not have fancy rotating cubes, snow flakes or wobbling windows. OpenGL rendering works fine, and movies playback fine with this driver.

These days I'm running Hardy on my Mini - with the radeon driver from git source. It was the only way I could get pure DVI to work. If you stick with feisty, or gutsy with the feisty driver, you might be fine.

My advice... don't get rid of OS X. I keep it on a 6 GB partition. I can boot it on startup, or load it under Mac On Linux once X windows has loaded. It's good for things like Skype and web pages containing Flash.

Let us know if you have any troubles.

---

### Post by /home on 2008-02-21
But can't flash run on the mac mini???
It's an intel mac

---

### Post by BladeMelbourne on 2008-02-21
You're in the wrong forum. This forum is for PPC users.

Intel Mac users should go here:
[http://www.ubuntuforums.org/forumdisplay.php?f=211](http://www.ubuntuforums.org/forumdisplay.php?f=211)

You don't have an ATI radeon card, you probably have 64 MB of video memory (twice that which PPC minis have). You can also run Skype and Flash.

Lucky *******! :p

---

### Post by iler on 2008-03-06
Thanks for BladeMelbourne for providing this tip. Installing was really easy and I also set the following to prevent updating the xorg ati package:
```
echo "xserver-xorg-video-ati hold" | dpkg --set-selections
```
Now I have a working Ubuntu 7.10 and G4 Mac Mini setup :)

---

### Post by microft on 2008-03-08
> **BladeMelbourne said:**
> I was pretty sure it was capable of a resolution that size.

I am fairly confident that the open source ATI radeon driver will get you 1900x1200. The only caveat is compiz (3D/rendered desktop effects). At 24 bit colour, a display adapter with 32 MB RAM at 24 bit colour can only manage 1024x1024 at the most.

Thus I (at 1280x1024), and you if you proceed, will not have fancy rotating cubes, snow flakes or wobbling windows. OpenGL rendering works fine, and movies playback fine with this driver.

These days I'm running Hardy on my Mini - with the radeon driver from git source. It was the only way I could get pure DVI to work. If you stick with feisty, or gutsy with the feisty driver, you might be fine.

My advice... don't get rid of OS X. I keep it on a 6 GB partition. I can boot it on startup, or load it under Mac On Linux once X windows has loaded. It's good for things like Skype and web pages containing Flash.

Let us know if you have any troubles.


This is what I intend to do:

(As soon as I can get OSX running under VMWARE server on my bigger machine)

Install Ubuntu (maybe xubuntu) on my mac mini using the full internal HDD.
Keep Tiger on an external firewire HDD (just in case I need it sometime).
Not have compiz or any window efects (keep it light on the graphics card), at 1920x1200.
Use NFS to mount some filesystem parts off the bigger machine.

---

### Post by microft on 2008-03-22
It's up and running!
I'm writting this post on my Mac Mini G4 running xubuntu.
For the most part the instalation was very easy, and didn't take me long.

Remarks:
-The "proprietary driver manager" that comes with ubuntu took care of the wireless card configuration.
-The graphics card driver issue was solved just like BladeMelbourne posted: Thanks! (and it works fine at 1920x1200@60Hz)


Stuff still to do:
- Try to get the wireless card to use some sort of encryption (I'd like to use WPA+PSK)
- Try to tweak the xorg.conf, to run a little more smoothly.



Thanks for all your help.

---

### Post by slacka-vt on 2008-03-22
Hey Scruff,

I had no problems loading the Dapper 6.06 live-cd on a PPC with a Radeon 9200.

Worth a shot,

btw, I have also had no problems using the most recent Hardy live-cd on the same machine
with a Radeon 9200.

the proper non compiz driver was simply called "ati"

~s

---

