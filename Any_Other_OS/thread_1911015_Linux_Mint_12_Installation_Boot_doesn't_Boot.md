---
title: "Linux Mint 12 Installation Boot doesn't Boot"
date: 2012-01-18
forum: Any Other OS
---

### Post by rickyLOLZ on 2012-01-18
Hello!
I just saw my PC can't boot to the newest Linux distributions but if it was a previous version (like Linux Mint 11 or Ubuntu 10.04) it would work.

Please help me, because i buyed a blank DVD just to burn the Linux Mint 12 iso to the DVD.

(also when i try to boot the newest Linux distribuitons it appears a black screen and does nothing but sit there).

---

### Post by nothingspecial on 2012-01-18
Moved to Other OS/Distro Talk

---

### Post by rickyLOLZ on 2012-01-18
Don't forget to help please!

---

### Post by sudodus on 2012-01-18
> **rickyLOLZ said:**
> Hello!
I just saw my PC can't boot to the newest Linux distributions but if it was a previous version (like Linux Mint 11 or Ubuntu 10.04) it would work.

Please help me, because i buyed a blank DVD just to burn the Linux Mint 12 iso to the DVD.

(also when i try to boot the newest Linux distribuitons it appears a black screen and does nothing but sit there).
I suggest that you test several versions and flavours of linux ***live***, and install the one that you like the best. Sometimes an older version works better with a particular computer. If Linux Mint 11 or Ubuntu 10.04 are OK, why not select (or continue with) one of them? They still have time to go (until end of support). I guess that Ubuntu 12.04, to be release April 2012, will be much better than 11.10 because it will be a long time support (LTS) version, to be supported until April 2017.

---

### Post by WasMeHere on 2012-01-18
Hi again,

So Linux Mint 12 (and Ubuntu 11.10?) don't work for you. It is sad, that something that works in an old version is lost in a new version. I support the suggestion of Sudodus to run what works, and not bother too much to run the latest version. 'Latest is not always the greatest'

May I suggest [KLX]ubuntu 11.04 or Linux Mint 11? Try them out live, and select the best one for you!

Have fun finding out
Olle

---

### Post by rickyLOLZ on 2012-01-18
> **Olle Wiklund said:**
> Hi again,

So Linux Mint 12 (and Ubuntu 11.10?) don't work for you. It is sad, that something that works in an old version is lost in a new version. I support the suggestion of Sudodus to run what works, and not bother too much to run the latest version. 'Latest is not always the greatest'

May I suggest [KLX]ubuntu 11.04 or Linux Mint 11? Try them out live, and select the best one for you!

Have fun finding out
Olle

Ubuntu versions starting to the number 11 don't work, for me.
My computer is a Windows 7, if you need that information.

---

### Post by rickyLOLZ on 2012-01-18
The boot installations for Ubuntu 11.04, Linux Mint 11 and Linux Mint 12 doesn't work with my computer, i don't know why!

My computer is Windows 7.

---

### Post by rickyLOLZ on 2012-01-18
...please read my latest thread.

---

### Post by BC59 on 2012-01-18
You mean that tried to boot with the LiveCD you created by downloading an .iso file and burn it to a CD?

---

### Post by rickyLOLZ on 2012-01-18
> **BC59 said:**
> You mean that tried to boot with the LiveCD you created by downloading an .iso file and burn it to a CD?

Yes.

---

### Post by BC59 on 2012-01-18
Try to change on BIOS the boot sequence. You should put first in the boot list, the option you are using to boot, a CD or a USB pendrive.

---

### Post by rickyLOLZ on 2012-01-18
> **BC59 said:**
> Try to change on BIOS the boot sequence. You should put first in the boot list, the option you are using to boot, a CD or a USB pendrive.

I already choosed from USB or DVD.
I'm saying the installation runs but just appears a black screen.

---

### Post by BC59 on 2012-01-18
In that case looks like you problem belongs to this category:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by mips on 2012-01-18
What hardware are you using? Give us a list, mb, cpu, gfx etc etc

Why not rather write the ISO image to a USB stick using UNetBootin.
Did you check the MD5SUM of the ISO you downloaded to make sure it's good?
You can try holding down the shift key just after the grub menu while booting to see if it boots in cli mode. it might be a gfx card issue.

---

### Post by WasMeHere on 2012-01-18
> **rickyLOLZ said:**
> Hello!
I just saw my PC can't boot to the newest Linux distributions but if it was a previous version ([COLOR="Red"]like Linux Mint 11[/COLOR] or Ubuntu 10.04) it would work.

Please help me, because i buyed a blank DVD just to burn the Linux Mint 12 iso to the DVD.

(also when i try to boot the newest Linux distribuitons it appears a black screen and does nothing but sit there).
> **rickyLOLZ said:**
> Ubuntu versions starting to the number 11 don't work, for me.
My computer is a Windows 7, if you need that information.

I would have thought that if Linux Mint 11 works, also Ubuntu 11.04 works, because they are pretty much the same behind the curtain. Is Linux Mint 11 working with your computer? And I'll search for your latest thread ...

---

### Post by rickyLOLZ on 2012-01-18
> **BC59 said:**
> In that case looks like you problem belongs to this category:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

The installation runs but the installation doesn't give any image or anything, only a black screen.

---

### Post by BC59 on 2012-01-18
You have to read the first post of the thread of @P4man, who explains in detail the different options of this problem. It's no so complicated as looks like. On booting you have to choose from the Grub boot screen, the option to make changes to the Grub file.

---

### Post by WasMeHere on 2012-01-18
> **rickyLOLZ said:**
> The installation runs but the installation doesn't give any image or anything, only a black screen.

Booting from the CD, can you see the menu page with a bar at the bottom with several Function key options at the bottom:

F1, F2 ..... F6

If you press F6 you can select boot options, that might improve the situation. This is trial and error, so try them one by one and if necessary two by two, and see what happens. This is described in the following link.

[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by nothingspecial on 2012-01-18
Threads merged.


> **rickyLOLZ said:**
> ...please read my latest thread.

One thread per issue please.

---

### Post by rickyLOLZ on 2012-01-19
...i'll try some of these.
Thanks, but don't lock the thread yet.

---

### Post by rickyLOLZ on 2012-01-20
Doesn't work.

---

### Post by WasMeHere on 2012-01-20
> **rickyLOLZ said:**
> Doesn't work.
Does any linux work for you? I can not understand from your previous posts, if you have ever run linux before. Did you run Ubuntu 10.04 before?

I suggest that you ***try various different linux versions of different ag***e, for example Ubuntu 10.04, Linux Mint 9 but also some other distro (Fedora, OpenSuse ...) to find out what can co-operate with your computer. Usually it is easier to make it work via the CD than the USB, but make live USB drives with Unetbootin, if you get tired of burning CDs that won't work!

Knoppix is a version with very good recognition of hardware. It is meant to run live (not to be installed), but it can be made persistent.

---

### Post by BC59 on 2012-01-20
If you like to install Ubuntu, there is an option. Download the image of [Ubuntu minimal installation]("https://help.ubuntu.com/community/Installation/MinimalCD").
Then make a bootable USB pendrive, with Netbootin through Windows and try installing it to your computer. If the minimal installation works, then try downloading the full system.

---

### Post by mips on 2012-01-20
nomodeset?

---

### Post by BC59 on 2012-01-20
> **mips said:**
> nomodeset?

I recommended nomodeset in the #13 post. I'm not sure if he followed the instructions.

---

### Post by mips on 2012-01-20
> **BC59 said:**
> I recommended nomodeset in the #13 post. I'm not sure if he followed the instructions.

sorry i did not read the whole thread.

---

### Post by BC59 on 2012-01-20
> **mips said:**
> sorry i did not read the whole thread.

No worries, It looks like nomodeset problem, but I don't know if he followed the instructions of the thread.

---

### Post by rickyLOLZ on 2012-01-21
> **Olle Wiklund said:**
> Does any linux work for you? I can not understand from your previous posts, if you have ever run linux before. Did you run Ubuntu 10.04 before?

I suggest that you ***try various different linux versions of different ag***e, for example Ubuntu 10.04, Linux Mint 9 but also some other distro (Fedora, OpenSuse ...) to find out what can co-operate with your computer. Usually it is easier to make it work via the CD than the USB, but make live USB drives with Unetbootin, if you get tired of burning CDs that won't work!

Knoppix is a version with very good recognition of hardware. It is meant to run live (not to be installed), but it can be made persistent.

Only Ubuntu 10.04 seems to work, but the internet problem is there.

---

### Post by sudodus on 2012-01-21
> **rickyLOLZ said:**
> Only Ubuntu 10.04 seems to work, but the internet problem is there.
Sorry Ricky, we have walked around in a circle. Now we are back where you started to post a thread about this problem. So I repeat what Olle Wiklund wrote at that time and add some tips afterwards.
--
Wired internet works out of the box (almost always). But there are issues with several wireless LAN chips and cards.

Have a look at the following link
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
--
I think the best solution for you is to get a wireless LAN card or adapter that works out of the box according to the 'WifiDocs' link and to continue with Ubuntu 10.04 LTS.

Just an example: I have a Zyxel G-202 wireless USB adapter, and it works out of the box for me with Ubuntu 10.04. However, in order to make it work at full speed, I had to do some tweaking, that I found in a text describing how to make a system run well with ndiswrapper. Maybe the spooler make the difference.

---

### Post by WasMeHere on 2012-01-21
> **BC59 said:**
> No worries, It looks like nomodeset problem, but I don't know if he followed the instructions of the thread.

Ricky, did you try the ***nomodeset*** option? If not, try it before resorting to 10.04 LTS + a separate wireless LAN adapter.

---

