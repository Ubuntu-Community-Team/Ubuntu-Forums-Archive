---
title: "Which method is best--dist-upgrade or fresh install?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-04-13
Hello, everyone.

I was doing some thinking, and I would really be grateful for some input on this.

Each time (since the release fo Breezy (v5.10)) a new release of Ubuntu comes out, I typically download the ISO, burn it to a CD, and perform a fresh install.  When I get a new computer, I plan to solely use Ubuntu (my wife, no matter how much I try, still is under M$ Mind Control :) ), and when I do so I am not sure fo which is the better way to upgrade (as I am one to be close to teh "cutting edge", but still a safe distance away from it. (e.g. when the final release of Feisty arrives, I want it!).  I eventually want to help with beta testing, but I still do not have the skill to fix problems that arise (i.e. kernel panics and such).

Which is the best method?

I have my Linux system set up on its own HDD (hdb)--my / (root) directory and my /home directory on two separate partitions and a FAT32 partition set up for Windows/Linux backups and my soon-to-be Thunderbird mail directory (as I use Thunderbird on both systems).

Would it be best to perform a dist-upgrade or should I just download the ISO, burn it to a CD (I will do that, anyway...just to have it), and do a fresh install?

I've read both good and bad about dist-upgrade, but I have never really done one.

What would you recommend?

Thanks for the input.

Take care.

---

### Post by houstonbofh on 2007-04-13
Such a loaded question...  Let me ask you some.

How many 3rd party repositories do you have?
How many compiled applications?
How many non-standard file systems?
Have you enabled backports?
Have you used repositories for other distributions? (Dapper on Edgy, or Debian on Ubuntu)
Are you using binary drivers for graphics or WiFi?

A lot of yeses above mean more chances for upgrade issues.

---

### Post by RKCole on 2007-04-13
Hello, houstonbofh.

Here are teh answers, to the best of my ability:

**How many 3rd party repositories do you have?**
I only have the ones that you can enable via Synaptic (I think only Universe and Multiverse).  I just did a fresh install of Edgy this afternoon.

**How many compiled applications?**
Two compilations: 1) gnome-mag (the GNOME magnifier) and 2) a compiled RaLink RT73 LInux driver for my Wireless USB dongle.

**How many non-standard file systems?**
My Primary HDD has Windows XP on it (formatted with NTFS) and nothing more.  My Secondary HDD has Ubuntu (with separate / and /home partitions and a swap partition) formatted with ext3 and a FAT32 partition at the end of the drive.

**Have you enabled backports?**
Please forgive my ignornace...but what do you mean by backports?  I think the answer may be no on this one. :)  I just installed the latest updates, and the only applications I have from third-party repos are XMMS, streamtuner, mplayer, and all of the multimedia codecs.

**Have you used repositories for other distributions? (Dapper on Edgy, or Debian on Ubuntu)**
No.  Just the repositories made available in Edgy.

**Are you using binary drivers for graphics or WiFi?**
As far as my graphics card (nVidia GeForce FX 5500), I used envy to install the graphics driver.  For my WiFi device I used a driver which was compiled from source for Linux.

Hope this information helps some, and if you need to know anything further, please let me know.

Since Feisty is due out in around a week, I may just do a fresh install as I just reinstalled Edgy today (I'm getting a lot of good practice), and so I do not have a lot of data stored in my /home directory.  But I wanted to see which method would be easiest and which would be best for keeping settings/data intact.

Take care.

---

### Post by TheMono on 2007-04-13
OK, you will have to recompile your driver for your wireless if you dist-upgrade, and also reinstall your graphics driver (I do suggest that you use the one from the ubuntu repositories though, nvidia-glx) Other than that you are a prime candidate for a dist-upgrade. If you download the alternate install disc for Feisty, you can insert that into your edgy computer and it will allow you to dist-upgrade from the disc, so if something does go wrong, you don't have to download everything twice in order to do the full install.

Having said that, the laptop I am writing on has dist-upgraded from Breezy to Dapper to Edgy and now Feisty and is still going strong.

---

### Post by RKCole on 2007-04-13
Hello.

Sounds like a plan.  I usually always use the Alternate Install CDs as I can't do much on the Live CDs due to my vision.

So, for the nvidia-glx driver, (just guessing here) would I do:
```

sudo apt-get install nvidia-glx

```?

And I know this is off-topic, but does this driver apply to specific nVidia cards, or is it universal?

Thanks for the input.

Take care.

---

### Post by houstonbofh on 2007-04-13
Good answers.  I will line by line them...
> **RKCole said:**
> Hello, houstonbofh.

Here are teh answers, to the best of my ability:

**How many 3rd party repositories do you have?**
I only have the ones that you can enable via Synaptic (I think only Universe and Multiverse).  I just did a fresh install of Edgy this afternoon.

Good answer, but it doesn not agree with you later.  Did you use medibuntu or plf for codecs and other non-free?  The common ones I find are plf or mdeibuntu and Wine.
> **RKCole said:**
> 
**How many compiled applications?**
Two compilations: 1) gnome-mag (the GNOME magnifier) and 2) a compiled RaLink RT73 LInux driver for my Wireless USB dongle.

The upgrade will break your WiFI.  However, WiFi support is better in Feisty, so you may not need it.  I would remove the compiled driver, and upgrade from lan.  Then see if it is needed again.
> **RKCole said:**
> 
**How many non-standard file systems?**
My Primary HDD has Windows XP on it (formatted with NTFS) and nothing more.  My Secondary HDD has Ubuntu (with separate / and /home partitions and a swap partition) formatted with ext3 and a FAT32 partition at the end of the drive.

Good.
> **RKCole said:**
> 
**Have you enabled backports?**
Please forgive my ignornace...but what do you mean by backports?  I think the answer may be no on this one. :)  I just installed the latest updates, and the only applications I have from third-party repos are XMMS, streamtuner, mplayer, and all of the multimedia codecs.

Backports are under the "Internet updates" section.  These are ports of newer versions of software from later versions of Ubuntu.  For example, I have a Feisty backport of FileZilla on my Edgy system.  This may give me problems later, but probably not.
> **RKCole said:**
> 
**Have you used repositories for other distributions? (Dapper on Edgy, or Debian on Ubuntu)**
No.  Just the repositories made available in Edgy.

Where did the codecs and other non-free stuff come from?
> **RKCole said:**
> 
**Are you using binary drivers for graphics or WiFi?**
As far as my graphics card (nVidia GeForce FX 5500), I used envy to install the graphics driver.  For my WiFi device I used a driver which was compiled from source for Linux.

This will also break.  I would pull it out, and use the 'nv' driver during the upgrade.  Then select "Linux-image-generic" before "nvidia-glx" and you will keep the better kernel.

Good luck!

---

