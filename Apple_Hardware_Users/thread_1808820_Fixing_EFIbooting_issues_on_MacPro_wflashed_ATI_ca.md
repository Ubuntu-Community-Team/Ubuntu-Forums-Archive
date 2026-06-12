---
title: "Fixing EFI/booting issues on MacPro w/flashed ATI card"
date: 2011-07-20
forum: Apple Hardware Users
---

### Post by ilazria on 2011-07-20
I've been successfully using a flashed ATI 5770, but have recently run into a problem. I ran Onyx on my Mac OSX HD, with the intent to only clear out some cache's, but it seems to have screwed up something vital to loading OSX. Now when I turn on the Mac (Mac Pro 1,1) it autoboots to GRUB. I can boot Ubuntu, but not OSX, which is on a separate HD. OSX (SL, 10.6) shows up on the GRUB screen, but choosing either x32 or x64 gives me these errors-

error: no such device: 6b8b8a7a901e8e5c
error: file not found
error: no xnu kernel loaded

Last night from Ubuntu I was able to access the OSX hard drive and copy over some important files. I noticed that the 5770_vervet_netkas.efi was no longer in the main directory, probably swept away by Onyx. Unfortunately, I couldn't copy it back where it belonged, because I had read only permissions, and could not change them, no matter what I tried. It was getting late, so I figured I'd shut down and try some more today. Well, I must have messed something ELSE up trying to change permissions, because now Ubuntu is showing the OSX HD as having no partitions, and it is now unmountable. The EFI partition was on this HD, and is now apparently not there. Ubuntu's disk Utility basically sees it as a blank HD.

I'd thought maybe doing a reinstall of SL would help, but either the disk isn't loading, or I just can't see anything due to using a flashed PC card (there is no display until OSX loads with these flashed cards.) Is there any way to fix this? Is there a way to install SL from Ubuntu, so I can set the appropriate permissions, and put files where they belong? Or maybe I need to re-flash the card? Or is there some other answer? This is the only Mac I have ready access to. My parents both have the newer Macs where everything is in the monitor, but I don't think I'd be able to use those to do an install on this HD.

---

### Post by nevius on 2011-07-22
In order to write to a HFS+ partition you need to disable journaling on said partition. I believe this can be done from ubuntu. [see here]("http://ubuntuforums.org/showthread.php?t=1420673")


> **ilazria said:**
> I've been successfully using a flashed ATI 5770, but have recently run into a problem. I ran Onyx on my Mac OSX HD, with the intent to only clear out some cache's, but it seems to have screwed up something vital to loading OSX. Now when I turn on the Mac (Mac Pro 1,1) it autoboots to GRUB. I can boot Ubuntu, but not OSX, which is on a separate HD. OSX (SL, 10.6) shows up on the GRUB screen, but choosing either x32 or x64 gives me these errors-

error: no such device: 6b8b8a7a901e8e5c
error: file not found
error: no xnu kernel loaded

Last night from Ubuntu I was able to access the OSX hard drive and copy over some important files. I noticed that the 5770_vervet_netkas.efi was no longer in the main directory, probably swept away by Onyx. Unfortunately, I couldn't copy it back where it belonged, because I had read only permissions, and could not change them, no matter what I tried. It was getting late, so I figured I'd shut down and try some more today. Well, I must have messed something ELSE up trying to change permissions, because now Ubuntu is showing the OSX HD as having no partitions, and it is now unmountable. The EFI partition was on this HD, and is now apparently not there. Ubuntu's disk Utility basically sees it as a blank HD.

I'd thought maybe doing a reinstall of SL would help, but either the disk isn't loading, or I just can't see anything due to using a flashed PC card (there is no display until OSX loads with these flashed cards.) Is there any way to fix this? Is there a way to install SL from Ubuntu, so I can set the appropriate permissions, and put files where they belong? Or maybe I need to re-flash the card? Or is there some other answer? This is the only Mac I have ready access to. My parents both have the newer Macs where everything is in the monitor, but I don't think I'd be able to use those to do an install on this HD.

---

### Post by ilazria on 2011-07-22
I'm feeling quite stuck. My only viable option appears to be to reinstall OSX, but without video output during startup, I can't see anything to perform the install. Is there any way to do a remote install while in Ubuntu?

---

### Post by johnmurrayvi on 2011-07-22
Have you tried booting off the Snow Leopard install disk and using the various utilities, i.e. Terminal and Disk Utility?

---

### Post by ilazria on 2011-07-22
> **johnmurrayvi said:**
> Have you tried booting off the Snow Leopard install disk and using the various utilities, i.e. Terminal and Disk Utility?


That's the thing. Even using the Snow Leopard DVD, I have no picture. When my Mac drive was working, there was no picture until my user account loaded. This is normal for most flashed ATI video cards, as far as I can tell. So far, I haven't found anyone who has a modified EFI to sew to the ROM that allows any of the booting screen to show. 

From what I can see, there is no recovering the old OSX on that hard drive. From Ubuntu, it shows as a blank, un-partitioned hard drive. I'm not sure what happened there, since at first I _could_ see and access that hard drive, just not write to it. I don't think the problem is with the video card, since I have no troubles using it to load Ubuntu. TO me, it seems most likely that somehow the OSX hard drive got messed up somehow, and I now have no Mac operating system on here. I'm pretty sure that if I could just reinstall Snow Leopard I'd be fine. The trouble is, how can I, if there's no picture when I try to boot to the install DVD?

---

### Post by nevius on 2011-07-23
OSX Server supports headless installs via SSH, but I don't think it works for the Desktop version. You can test it by connecting the computer via ethernet cable to your router and booting from your install disc. Test to see if you can SSH into the install session by root@ip-address. Password would be the hardware serial number.

If this doesn't work your best bet may be to borrow a very trusting friend / family member's computer and enabling SSH or some other form of remote administration. Then use [clonezilla]("http://clonezilla.org/downloads.php") to clone the hard drive on the other mac and copy it to your mac.

Once the hard drive is cloned, log into your computer remotely and do perform the hacks you need to get the graphics card properly working.


Note: this will erase your ubuntu partition.

---

