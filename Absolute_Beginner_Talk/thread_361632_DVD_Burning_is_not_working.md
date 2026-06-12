---
title: "DVD Burning is not working"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by %hMa@?b&lt;C on 2007-02-14
every dvd that I try to burn is a failed burn.  I can burn cds but not dvds.
I put on DMA using hdparm, and I even tried upgrading to growisofs 7 from source, but I still cannot burn.
the burner is a Pioneer DVR111-D

---

### Post by %hMa@?b&lt;C on 2007-02-14
bump, I really dont want any more coasters

---

### Post by RomeReactor on 2007-02-14
Hi. How old is your burner? is the last thing you burned to DVD an ISO? I'm asking this because i'm in a somewhat similar situation: I bought a Lite-On dual layer dvd burner some 6 months ago, and since then it had been a true workhorse; however, a couple of months ago, after burning (incorrectly) an [Elive]("http://www.elivecd.org/") ISO, it refuses to even detect cd's, though i can read and write DVD's just fine. In my case, i suppose it's hardware failure, but a friend of mine suggested it might have something to do with the burner firmware (!). Sorry i can't offer any help, just offering my opinion...

---

### Post by %hMa@?b&lt;C on 2007-02-14
> **RomeReactor said:**
> Hi. How old is your burner? is the last thing you burned to DVD an ISO? I'm asking this because i'm in a somewhat similar situation: I bought a Lite-On dual layer dvd burner some 6 months ago, and since then it had been a true workhorse; however, a couple of months ago, after burning (incorrectly) an [Elive]("http://www.elivecd.org/") ISO, it refuses to even detect cd's, though i can read and write DVD's just fine. In my case, i suppose it's hardware failure, but a friend of mine suggested it might have something to do with the burner firmware (!). Sorry i can't offer any help, just offering my opinion...

the last thing I burned was an iso, but it is a very new burner (got it early january) I would be pissed if it is a hardware failure

---

### Post by %hMa@?b&lt;C on 2007-02-15
bump

---

### Post by RomeReactor on 2007-02-15
Try installing

```
sudo apt-get install dvd+rw-tools
```

in case you don't have it. Also, some DVD burners have problems with a few brands of DVD's, so make sure you have at least 3 or 4 different ones to try. What program are you using to burn DVD's? Or are you burning from the command line?

---

### Post by Cardmaster91 on 2007-02-15
DVD burners can last a lifetime, and can last a few months. It depends on how hard and often you use them. Like, if you constantly use the burner at max speed, it will wear out very fast. And if you write cd's in it, then you might as well take a sledgehammer to it. Ur best bet if what he said don't work, is get a nice one, and use it moderatly. P.s. Never use cd's in a dvd burner/reader

---

### Post by %hMa@?b&lt;C on 2007-02-15
> **Cardmaster91 said:**
> DVD burners can last a lifetime, and can last a few months. It depends on how hard and often you use them. Like, if you constantly use the burner at max speed, it will wear out very fast. And if you write cd's in it, then you might as well take a sledgehammer to it. Ur best bet if what he said don't work, is get a nice one, and use it moderatly. P.s. Never use cd's in a dvd burner/reader

why not? just asking why, I never had problems in my old NEC one that I burned hundreds of CDs

---

### Post by %hMa@?b&lt;C on 2007-02-15
> **RomeReactor said:**
> Try installing

```
sudo apt-get install dvd+rw-tools
```

in case you don't have it. Also, some DVD burners have problems with a few brands of DVD's, so make sure you have at least 3 or 4 different ones to try. What program are you using to burn DVD's? Or are you burning from the command line?

I am trying both with growisofs K3b NeroLinux trial and GnomeBaker, I get the "flushing cache" errors.

---

### Post by RomeReactor on 2007-02-15
Perhaps HDPARM didn't keep the settings. In the terminal try

```
hdparm /dev/hdc
```

where hdc is your DVD burner; change accordingly. The output **must** say

```
using_dma    =  1 (on)
```

If it doesn't, try

```
sudo hdparm -d1 -k1 /dev/hdc
```

---

### Post by %hMa@?b&lt;C on 2007-02-17
from gnomebaker
```

Executing 'builtin_dd if=/home/crowell/Desktop/hdd/mkdd-ntsc.iso of=/dev/hda obs=32k seek=0'
/dev/hda: "Current Write Speed" is 4.1x1385KBps.
:-[ WRITE@LBA=5e0h failed with SK=4h/ASC=08h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/hda: flushing cache
/dev/hda: updating RMA
/dev/hda: closing disc
```

---

### Post by %hMa@?b&lt;C on 2007-02-17
also, burning works fine in windows, same burner, same box.

---

### Post by %hMa@?b&lt;C on 2007-02-17
Installed wine, tried ImgBurn, still did not work. Tried multiple brands of DVD, + and -

---

### Post by %hMa@?b&lt;C on 2007-02-18
bump

---

### Post by pdiki on 2007-02-21
Hi jeffc313,

Im having exactly the same problems, did you manage to find a fix?

Thanks,
Paul

---

### Post by %hMa@?b&lt;C on 2007-02-21
> **pdiki said:**
> Hi jeffc313,

Im having exactly the same problems, did you manage to find a fix?

Thanks,
Paul

nope, still no fix :( 
I will let you know if I ever do, though.  I did have the burner working when I first got it.  I think I was using Kubuntu either dapper or edgy, but I am not sure if it was AMD64 or x86

---

### Post by PapaWiskas on 2007-02-27
WRITE@LBA=0h failed with SK=4h/ASC=08h/ACQ=03h

I have the same error as you....any luck yet?

Everything worked in Breezy, then Dapper, but since Edgy its flaked.  I know burner is good because it works in XP just fine.

My burner used to be /dev/hdc but ever since my Uberyl install it has been /dev/scd0....something just doesnt seem right with the settings and I cant put my finger on it.

---

### Post by bonzodog on 2007-02-27
um..yeah. 
Are you by chance running the 2.6.20 kernel?

If so, the device name nodes have been altered, and it's possible that gnomebaker does not line up with the DVD-RW any more.

Over here on Zenwalk Linux, we have had to change /etc/fstab and lilo to tell zenwalk where to look for the drives. They have gone from being hd*x* devices to sd*x* devices.

---

### Post by PapaWiskas on 2007-02-27
Actually I am using the 2.6.17-11-generic.

Can anyone advise as to what the fstab entry should look like and how do I tell GRUB what to do since I dont use Lilo.

---

### Post by PapaWiskas on 2007-02-28
bump

---

### Post by PapaWiskas on 2007-03-01
bump

---

### Post by dannyboy79 on 2007-03-01
well I had a cheap i/o magic dvd burner that just would not work for the life of me! i even installed the newest dvd+rw-tools (see below) and that still didn't work.

sudo aptitude show dvd+rw-tools
Password:
Package: dvd+rw-tools
State: installed
Automatically installed: no
Version: 6.1-2
Priority: optional
Section: utils
Maintainer: Daniel Baumann <daniel.baumann@panthera-systems.net>
Uncompressed Size: 434k
Depends: libc6 (>= 2.3.5-1), libgcc1 (>= 1:4.0.2), libstdc++6 (>= 4.0.2-4),
         mkisofs
Conflicts: dvdplusrw (<= 20020220.1)
Replaces: dvdplusrw
Description: DVD+-RW/R tools
 dvd+rw-tools makes it possible to burn DVD images created by dvdauthor or
 mkisofs to DVD+R, DVD+RW, DVD-R, and DVD-RW disks, replacing cdrecord-proDVD in
 many cases.

 The package contains:

 * growisofs to burn DVD images or create a data DVD on the fly
 * dvd+rw-format to format a DVD+RW
 * dvd+rw-mediainfo to give details about DVD disks

 and some programs to control the write speed and obtain information from
 DVD-RAM.

I even purchased the most expensive best dvd+r and dvd-r's I could find, tyio udin or whatever and all those wierd japanese brands that people in the cd-freaks forums swear by but to no avail. oh yeah, the burner working fine in winxp pro

so then I had enough of making coasters and spent $39.99 and got the hda: Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive
[17179583.668000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66) and all was well!!!! Yeah!!! the thing can even burn dvd-ram! the only other thing I can suggest is trying other firmware. hell now it's down to $28.99 from tigerdirect.com. [http://www.pricegrabber.com/p__NEC_AD_7170A_Dual_Layer_DVD_RW_Writer,__27671171](http://www.pricegrabber.com/p__NEC_AD_7170A_Dual_Layer_DVD_RW_Writer,__27671171)

---

### Post by PapaWiskas on 2007-03-01
This drive is in my laptop, and it works fine in breezy, and dapper, but something is different in Edgy (Uberyl) release.  I am in the process of burning Feisty now to see if it solves my issue.

---

### Post by dannyboy79 on 2007-03-01
did you try to download the latest dvd+rw-tools? i believe it includes a custom version of growisofs although I can't say for sure. hope fiesty works for ya. i have to ask, if it worked in dapper what's the reason you went to edgy?

---

### Post by odzx on 2007-03-01
i dont know if my problem is the same as yours. but after i tried every suggestion on this forum and still could'nt burn anything with either k3b or gnomebaker, i've installed brasero. for reasons i do not understand, it burns anything i through at it.
again. dont know if it has anything to do with your problem, but hell, i gave it a shot.
good luck!

---

### Post by dannyboy79 on 2007-03-01
[http://sourceforge.net/projects/bonfire/](http://sourceforge.net/projects/bonfire/)

see what's weird is that it simply is a gui for these backends: cdrtools, growisofs, libburn.pykix.org ([http://libburn.pykix.org](http://libburn.pykix.org)) (optional). 

there is an important point though on their website:
Note: compiling against libburn is _not_enough. You need to activate the backend through GConf editor at "/apps/brasero/config/libburn_burn and /apps/brasero/config/libburn_iso"

so maybe you just have a library missing or something. hope this works for ya as I just gave up and bought a new drive so it obviously was hardware or firmware in my case.

whats also weird is that it depends on nautilus-cd-burner

Requirements 
- gnome 2.14.x (gnome-vfs, nautilus-cd-burner)
- gstreamer (>= 0.10.6)
- libxml2
- a kernel 2.6.13 at least (for inotify, optional) 
- beagle (>= 0.2.5) (optional)
- totem (>= 2.14) (optional)

---

### Post by PapaWiskas on 2007-03-02
> **dannyboy79 said:**
> did you try to download the latest dvd+rw-tools? i believe it includes a custom version of growisofs although I can't say for sure. hope fiesty works for ya. i have to ask, if it worked in dapper what's the reason you went to edgy?


I wanted to see if my pc could run Beryl, and Uberyl was a logical choice for, and it is based on Edgy.

Feisty really did not work, I had even more issues.

---

### Post by %hMa@?b&lt;C on 2007-03-04
yeah... I am using edgy, and I do think that dapper did work with it. I will have to try using Fiesty, *begins download*

---

### Post by PapaWiskas on 2007-03-06
Well, this is really discouraging.  I feel like I have learned nothing.

Everything now works after doing yet another fresh install of Uberyl.  I am burning now as we speak after ripping a DVD using Ripit4Me in wine.

I did a test run with Tovid using some .avi I had, did the makexml, and used makedvd via command line, and it all works.

I just dont understand what was wrong before and why it works now.  Great it's working, but it sucks I didn't figure out the problem.:confused:

---

### Post by ramjet_1953 on 2007-03-07
> **Cardmaster91 said:**
> DVD burners can last a lifetime, and can last a few months. It depends on how hard and often you use them. Like, if you constantly use the burner at max speed, it will wear out very fast. And if you write cd's in it, then you might as well take a sledgehammer to it. Ur best bet if what he said don't work, is get a nice one, and use it moderatly. P.s. Never use cd's in a dvd burner/reader

Is this anecdotal, or do you have some hard facts?

As far as I know, a burner is a burner, is a burner. It makes no difference whether you burn, CD's DVD's or toast in it!

Regards,
Roger :cool:

---

### Post by PapaWiskas on 2007-03-07
> **Cardmaster91 said:**
> DVD burners can last a lifetime, and can last a few months. It depends on how hard and often you use them. Like, if you constantly use the burner at max speed, it will wear out very fast. And if you write cd's in it, then you might as well take a sledgehammer to it. Ur best bet if what he said don't work, is get a nice one, and use it moderatly. P.s. Never use cd's in a dvd burner/reader

I disagree with what you are saying.  We use DVD burners at work and make both CDs and DVDs and we have 2 burners that are over 2 years old.  These get used EVERY day, both types of media.  Probably make about 20 discs per day, each drive if not more on some days.

I have never heard that you should not burn CDs in a DVD burner, they are made to do both.

---

### Post by wildkarde on 2007-03-18
I'm also experiencing the same.  This sucks.
Here we go reinstall.

This makes no sense.

---

### Post by PapaWiskas on 2007-03-19
> **wildkarde said:**
> I'm also experiencing the same.  This sucks.
Here we go reinstall.

This makes no sense.

Let us know if your reinstall fixed the problem.

I would really like to know what happened in my case, but nothing I did to try and fix it worked.

---

### Post by wildkarde on 2007-03-27
Ok, not so much.

It's still not working so this is deff a hardware issue now.
I can't even reinstall at this point.  It gets to 71% and it freezes.

Damn hardware!!!

---

