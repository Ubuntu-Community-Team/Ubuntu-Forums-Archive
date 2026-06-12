---
title: "Dual boot Vista &amp; 7.10 MBR"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by jinnman on 2007-10-24
Greetings all.  My first post.
I probably wouldn't even consider Linux without a helpful forum like this.

I have Vista installed on my laptop and want to dual boot Ubuntu 7.10 Gutsy Gibbon 64-bit.  I've already shrinked my partition to give Ubuntu 15GB of installation space.

My question:
 Should I let GRUB or whatever the default boot loader is write to my MBR or have it install in my linux partition as some of the older posts suggest?  

I ask since this may not be an issue anymore with the latest version of Ubuntu.  Some report no problems, some say it is the only way to boot into Vista by using EasyBSD or something to add it to Vista's MBR.

---

### Post by Sturmeh on 2007-10-24
I think you want to install Vista second, as it depends on it's bootloader ( althrough grub CAN boot vista with some tweaking. )

Check up on guides.

[http://ubuntuforums.org/showthread.php?t=220452](http://ubuntuforums.org/showthread.php?t=220452)

You can skip the "XP part" on that tripple boot guide. xD ( It says to install ubuntu last! )

---

### Post by orthorim on 2007-10-24
I am triple booting Vista, XP and Ubuntu. Grub automatically configures itself so that the Vista bootloader is chained off of grub.

So I get the Grub screen which has boot options for ubuntu and for "Windows".

When I select "Windows" the Vista boot loader starts up and I can choose between Vista and XP. Vista has, sadly,replaced the boot.ini file with a binary database, meaning if you ever want to change options in the Vista boot you need to use the rather complicated command line tool (bootedit or something). This is a huge pain,

The only complaint I have with grub is that it stores its menu.1st boot menu config file on the linux partition. Meaning, in order to change anything about it, you have to boot into ubuntu, you can't do it from Windows as Windows can't read the linux partition.

There is supposedly a way to move the menu.1st file to another location but in the end I didn't try it because I could not figure out whether or not I could just place it on a NTFS partition. And my guess would be not since by the time Grub starts from the MBR, nothing is loaded, hence NTFS drivers wouldn't be loaded either.

---

### Post by louieb on 2007-10-24
> **orthorim said:**
> ...as Windows can't read the linux partition.,,,
Not a problem [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")

---

### Post by jinnman on 2007-10-28
@Sturmeh

The link you provide deals with 6.06.  Is it identical to the experience when dual booting with 7.10?

---

### Post by jinnman on 2007-10-28
Let me re-phrase my question.

Windows Vista was already installed when I bought my laptop, and I want to install Gutsy 7.10 in a dual boot configuration.  Will the installation of Ubuntu automatically detect everything or will I have to take additional steps to get things working?

The reason I ask is some people are having issues of being able to boot into one OS and not the other.  Is this still an issue with 7.10 or has it been rectified?
Thanks.

---

### Post by ohmycar on 2007-10-28
I had vista installed on my hard-drive first, I used the partition manager on the 7.10 live cd to re-size the drive to give ubuntu 30gb of free space. After installation, when I tried to reboot back into vista, it asked me to put in the original vista cd to repair a boot file. I did and now I can easily boot to both OS's through Grub. So if you have the vista cd, give it a try, if not, then I am not really sure. Hope that kind of helped, I am still pretty new to ubuntu.

---

### Post by jinnman on 2007-10-28
Thanks ohmycar

I don't have the original vista cd.  Acer has the installation on a hidden partition.  It allows you to make a factory default installation DVD which I have.  I guess that should help.  It seems some users get dual boot working out of the box, and some have to make additional tweaks; and that's what I'm scared of.  Otherwise Ubuntu rocks! :guitar:  I'm using the LiveDVD right now. :)

---

### Post by strabes on 2007-10-28
> **jinnman said:**
> Let me re-phrase my question.

Windows Vista was already installed when I bought my laptop, and I want to install Gutsy 7.10 in a dual boot configuration.  Will the installation of Ubuntu automatically detect everything or will I have to take additional steps to get things working?

The reason I ask is some people are having issues of being able to boot into one OS and not the other.  Is this still an issue with 7.10 or has it been rectified?
Thanks.

GRUB will install onto your MBR, detect vista, and enable you to boot into both operating systems. Go for it. Be careful when choosing which partition to install ubuntu onto. You don't want to accidentally erase your vista install.

---

### Post by justsomedude on 2007-10-28
I also have a Laptop that came with a pre-installed Vista, no problems here. I didn't even resize manually, I let the installer resize the partition. Worked fine, though some people reported different experiences. 

> You don't want to accidentally erase your vista install.

Well, judging from using this horrible OS occasionally during the last 5 weeks I'd say this is not the worst scenario that could happen... :)

The guys who port avisynth to Linux should hurry up, I want to delete Vista for good...
I'm on a triple boot now (Vista, Gutsy & Feisty), no problems here.

---

### Post by jinnman on 2007-10-30
Thanks for everyone's advice.  I think I'm ready to go.  May install tonight.  Wish me luck!

---

### Post by Mondoman on 2007-11-02
j - please let us know how your install worked out!
(another vista user waiting to take the laptop 7.10 plunge)

---

### Post by rudeboyskunk on 2007-11-02
And for the love of god, backup your personal data!!!!

---

