---
title: "How Do I Back Up The Mac Before The Switch?"
date: 2007-08-07
forum: Apple PPC Users
---

### Post by I922sParkCir on 2007-08-07
How Do I Back Up The Mac Before The Switch? 

I finally convinced my girlfriend to switch to Ubuntu, but I need to completely back up her HFS+ disk image for a possible recovery if she changes her mind. I don't know dd that well, but is it possible to do that off of an Ubuntu Live CD? I would like to image her computer onto an external disk drive.

Thank you guy's for you help. 

- Jai

---

### Post by aysiu on 2007-08-07
Hm. Support for HFS by PartImage is still in beta:
[http://www.partimage.org/Supported-Filesystems](http://www.partimage.org/Supported-Filesystems)

If she's at the point where she's "convinced" but may still "change her mind," I wouldn't install Ubuntu just yet. Any reason you want her using Ubuntu instead of OS X?

---

### Post by Auria on 2007-08-07
Utilities like [http://www.bombich.com/software/ccc.html](http://www.bombich.com/software/ccc.html) can ease backup (haven't tried myself but heard it's good, there's likely others)

but aysiu is right, as changing of system is a huge move, if not done properly it will be just trouble... just make sure you know the specifics of the PPC version too if your own computer is not a PPC, as some people don't do that and discover as a shock flash does not work after they installed it on their friend's computer

---

### Post by stmiller on 2007-08-07
Make sure you read over the PowerPC FAQs. There is no Skype for PowerPC Linux, and no Adobe Flash (but Gnash works for youtube). Pages like myspace (crap space?) and other flash intensive pages are somewhat problematic, if that matters.

Other than that, it's great.

---

### Post by I922sParkCir on 2007-08-08
I totally forgot about the Flash thing, that might be a deal breaker. I'm a huge geek (been hacking with Ubuntu for years) and have got everything working on her iBook via the live cd. How good is Gnash? Thank you.

-Jai

---

### Post by 3rdalbum on 2007-08-08
What operating system is she running? OS 9 or OS X?

On Mac OS 9, you can use the Disk Copy program that's already on the system to create a disk image straight onto your external hard disk. If you need to restore from it, then you can erase the hard disk with Drive Setup (run from the OS 9 install CD). Install a basic Mac OS system onto the hard disk, which will set the disk as bootable. Erase the new System Folder and all the Apple bloatware, double-click the image file from your external drive to mount the image, and then drag across everything from the disk image to the real hard disk.

Finally, in the Startup Disk control panel, select the hard disk as the boot device.

Unlike PCs, Macintoshes aren't fussy about what they boot from. If it's got a System Folder and a boot block, the Mac will boot from it.

---

### Post by Auria on 2007-08-08
> **I922sParkCir said:**
> How good is Gnash?


it's a great project... but they're not quite there right now. the latest version plays youtube approximately correctly for most people (but not everyone got youtube working, there seems to be a lot of bugs still)

for me, it's sad to say, but in my everyday use the only things i saw that worked correctly in gnash were ads (other people that use different websites may have better experiences)

in short: it's a nice project but don't rely on it too much, an environment that needs reliable flash for all websites just cannot use gnash.

---

### Post by aysiu on 2007-08-08
I wouldn't put anyone on PPC Linux unless I knew that person wasn't intending to visit Flash websites.

---

### Post by stmiller on 2007-08-08
Well Gnash is getting better. It is 100% compatible with all Flash 7 content, with added fixes from Flash 9. The problem is that webpages today aren't 100% Flash 7, so there are issues.  Some flash music players don't work (crap-space), and other video elements other than youtube and lulu.tv.

But most any standard/basic flash implementation (non-audio/video) works fine with Gnash, for just navigating a webpage.

There is Gnash 0.8.0 for x86 and X86_64 Ubuntu, so you can apt-get install it after enabling Feisty Backports and check it out on your current machine to test.

---

### Post by oswaldkelso on 2007-08-09
> **Auria said:**
> Utilities like [http://www.bombich.com/software/ccc.html](http://www.bombich.com/software/ccc.html) can ease backup (haven't tried myself but heard it's good, there's likely others)
r

I have used ccc and it'd very good. It will clone your system setting and all. You need a external firewire drive if you want to be able to boot it up again. (I have in the past cloned my G4 onto my 30gb ipod. But booting up from it to often is not recomended as the hard drives are not designed for it)

If you want to dual boot use ccc onto an external HD boot from that drive, format your mac into 2 partitions and clone osx back onto the first partiton.

Then install linux on the free space on the second partition.

Have fun

ps install MOL

---

### Post by EuroCity on 2007-08-10
In Mac OS X, you can also simply use Disk Utility's Restore function, booted from the hard disk or from the install CD/DVD: quite similar to Carbon Copy Cloner.

---

### Post by carlmccall on 2007-08-13
> **I922sParkCir said:**
> How Do I Back Up The Mac Before The Switch? 

I finally convinced my girlfriend to switch to Ubuntu, but I need to completely back up her HFS+ disk image for a possible recovery if she changes her mind. I don't know dd that well, but is it possible to do that off of an Ubuntu Live CD? I would like to image her computer onto an external disk drive.

Thank you guy's for you help. 

- Jai

If she's running Puma, Jaguar, or Panther (10.1 - 10.3) she can make a repair/emergency Boot CD for her computer with this free tool: **[BootCD]("http://www.charlessoft.com/")**

(Put Disc Utility / Disk Warrior / TechTool Pro 4 on it) 
 
Use it to start up her system and back it up using these instructions for [Mac OS X: How to back up and restore your files]("http://docs.info.apple.com/article.html?artnum=106941")

[B]C. Manual backup

(I have a "PowerMac7,3" model with two internal SATA hard drives: one for Ubuntu / One for Tiger. yaboot works OK for me. )

I'm sorry to hear Flash isn't supported on PowerPC Macs :(
[/B]

---

