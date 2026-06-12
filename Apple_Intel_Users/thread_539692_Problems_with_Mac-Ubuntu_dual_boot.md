---
title: "Problems with Mac-Ubuntu dual boot"
date: 2007-08-31
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-08-31
I've just bought my first Mac (13" Macbook, 1GB RAM, 2.16GHz Core 2 Duo, 160 GB HDD) and I have no prior Mac experience whatsoever.
I am, however, an ardent Linux user and have experience with quite a few distros.
For this reason, I want to set up a dual boot system here and am following this [guide]("https://wiki.ubuntu.com/MacBookProFeisty").
However, this is not going smoothly. 
So far, I have:
1) Installed BootCamp
2) Reduced the MacOS partition size to 125 GB (from about 150GB)
3) Downloaded and installed rEFIt
4) Downloaded and burnt to CD the recommended Alternate Ubuntu Install ISO
5) Then I booted to this ISO and got the install menu

But that's as far as I got. I am unable to scroll down through the menu and hitting return on the Install in Text Mode menu item does nothing.
Only the On-Off switch responds on the computer and I need to use this to get out of this dead end.
I'd appreciate some help as to where this might be coming unstuck
Thanks
Paul

---

### Post by cyberdork33 on 2007-08-31
> **PaulFXH said:**
> I've just bought my first Mac (13" Macbook, 1GB RAM, 2.16GHz Core 2 Duo, 160 GB HDD) and I have no prior Mac experience whatsoever.
I am, however, an ardent Linux user and have experience with quite a few distros.
For this reason, I want to set up a dual boot system here and am following this [guide]("https://wiki.ubuntu.com/MacBookProFeisty").
However, this is not going smoothly. 
So far, I have:
1) Installed BootCamp
2) Reduced the MacOS partition size to 125 GB (from about 150GB)
3) Downloaded and installed rEFIt
4) Downloaded and burnt to CD the recommended Alternate Ubuntu Install ISO
5) Then I booted to this ISO and got the install menu

But that's as far as I got. I am unable to scroll down through the menu and hitting return on the Install in Text Mode menu item does nothing.
Only the On-Off switch responds on the computer and I need to use this to get out of this dead end.
I'd appreciate some help as to where this might be coming unstuck
Thanks
Paul
There is a bug in the Apple firmware that causes the keyboard not to work in the bootloaders. If you let the timer run out the default selection will load, and the keyboard will then become available.

Also, note that you are following the MacBook Pro documentation. There are hardware differences in the Macbook and Macbook Pro. You may like to follow this instead: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) Everything you have done so far sounds fine. You are well on your way to Ubuntu on your Mac.

---

### Post by PaulFXH on 2007-08-31
OK, thanks for the explanation.
I'll try again.
Paul

---

### Post by guidop on 2007-08-31
You might also try inserting the install CD, then holding down the "C" key while you reboot.  If your machine works like my Oct '06 Macbook Pro, this should bypass the rEFIt bootloader, and let you use the keyboard to select options on the alternate install CD.

---

### Post by cyberdork33 on 2007-08-31
> **guidop said:**
> You might also try inserting the install CD, then holding down the "C" key while you reboot.  If your machine works like my Oct '06 Macbook Pro, this should bypass the rEFIt bootloader, and let you use the keyboard to select options on the alternate install CD.
Hmmm... Interesting new information. Doesn't really help after your system is installed though and you don't want the default in grub...

---

### Post by PaulFXH on 2007-08-31
OK, I tried what was suggested but it looks like the Gods are angry with me today as I've made no progress.
1) I moved to the Macbook-specific guide (the only difference, up to as far as I've gone, being the use of Bootcamp to create a "Windows" partition prior to the install)
2) I left the Install menu sit untouched with the Install in Text Mode option highlighted for several minutes but it never timed out.

So, once agaion, nothing happened.

Any more tricks up the sleeve?
Thanks
Paul

---

### Post by cyberdork33 on 2007-08-31
> **PaulFXH said:**
> I left the Install menu sit untouched with the Install in Text Mode option highlighted for several minutes but it never timed out.

I may be confused. There is only a timeout in grub after installing... You can try holding 'c' as suggested to bypass refit. The only other way I could figure is (how I do it) plug in a usb keyboard after the menu comes up (Of course I am not on a portable). or you can just try booting a few times as it seems to sometimes work and sometimes not.

There is not much needed change in the how to until you start configuring hardware after it is installed.

EDIT: Here is the bug report on the issue. There are a few suggestions included.
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/79172)

---

### Post by PaulFXH on 2007-08-31
OK, thank you. The usb-keyboard did the trick and I'm in the process of installing now.
Paul

---

### Post by viciouslime on 2007-08-31
I realise you've solved it now by use of an external keyboard, but it is worth pointing out that the desktop version of ubuntu will install fine and that DOES time out after 30 seconds :)

---

### Post by PaulFXH on 2007-08-31
OK, I've got Ubuntu running on my Macbook now (still need to fix the wireless connection) but the rEFIt bootloader seems to have been demoted as there is no sign of it anymore.
When I boot up, grub starts but no menu at all is presented and, even if it were, /boot/grub/menu.lst has no mention whatsoever of Mac OS X.

During the boot, a brief message appears on the screen asking for the ESC key to be pressed if a menu is required. However, once again, the laptop keyboard does nothing when the ESC key is pressed.

So, how do I get OS X back?

Just in reference to another point that was brought up earlier by guidop, I did actually boot with the 'C' key depressed quite a number of times, but this never gave me a functioning keyboard.

---

### Post by ronocdh on 2007-08-31
> **PaulFXH said:**
> I left the Install menu sit untouched with the Install in Text Mode option highlighted for several minutes but it never timed out.
I just wanted to toss in that the time-out occurs only on the live CD. The alternate (text-based) CD does not have a time-out, which is very unfortunate for those of us experiencing this keyboard issue. Plugging in an external USB keyboard is indeed the most reliable way to get around this, although several hard reboots might land you with a responsive laptop keyboard, too.

I've actually used my bluetooth keyboard on the installer screen! :confused:    \\:D/

---

### Post by cyberdork33 on 2007-08-31
> **PaulFXH said:**
> OK, I've got Ubuntu running on my Macbook now (still need to fix the wireless connection) but the rEFIt bootloader seems to have been demoted as there is no sign of it anymore.
When I boot up, grub starts but no menu at all is presented and, even if it were, /boot/grub/menu.lst has no mention whatsoever of Mac OS X.

During the boot, a brief message appears on the screen asking for the ESC key to be pressed if a menu is required. However, once again, the laptop keyboard does nothing when the ESC key is pressed.

So, how do I get OS X back?
Unfortunately this does not sound good. Are you positive that you did not overwrite your OSX partition? If you are booting directly into grub, without seeing refit or OSX, that is not a good sign. if you can burn a live cd you can check the drive partitions...

---

### Post by pxwpxw on 2007-09-01
> **PaulFXH said:**
> OK, I've got Ubuntu running on my Macbook now (still need to fix the wireless connection) but the rEFIt bootloader seems to have been demoted as there is no sign of it anymore.
When I boot up, grub starts but no menu at all is presented and, even if it were, /boot/grub/menu.lst has no mention whatsoever of Mac OS X.

During the boot, a brief message appears on the screen asking for the ESC key to be pressed if a menu is required. However, once again, the laptop keyboard does nothing when the ESC key is pressed.

So, how do I get OS X back?


See also **cyberdork33** post above.

Another possibility:

The installer possibly defaulted to installing grub stage1 to the MBR, and setting that as the default startuo (without any damage to Macosx). I don't think that is a problem unless triple booting with windows. However, it is not possible to boot macosx from the grub menu.

2 possible fixes, easily tried:

Hold the Option key down at startup to get the Apple Graphical chooser, hopefully 2 icons, windows and macosx/refit.

Command-Option-P-R at startup to reset the default auto-boot to Macosx/refit.

Then refit should be more helpful.

(triple booting on macbook c2d here)

---

### Post by PaulFXH on 2007-09-01
Thank you for the replies.
Actually, the problem I had with no availability of OS X seems to have miraculously fixed itself.
After 3-4 reboots where ONLY Ubuntu started (no menu at all), suddenly, and certainly without me having conciously done anything, rEFIt started to show up on reboot and displays the following icons:
1) Mac OS X
2) Linux from HD
3) EFI Shell
4) Partitioning tool
5) three others showing About EFI, Shutdown and Reboot options

While this is great, I just wish I understood a little more precisely what had happened.

---

### Post by pxwpxw on 2007-09-01
> **PaulFXH said:**
> 
While this is great, I just wish I understood a little more precisely what had happened.

Welcome to the club.:)

---

### Post by cyberdork33 on 2007-09-01
> **pxwpxw said:**
> Welcome to the club.:)
Yea I am at a loss as well. I didn't think it was possible for the machine to default to the MBR unless the disk was changed to a legacy MBR format (without the GPT)

---

