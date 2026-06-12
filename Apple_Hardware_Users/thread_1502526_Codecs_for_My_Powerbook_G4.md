---
title: "Codecs for My Powerbook G4"
date: 2010-06-05
forum: Apple Hardware Users
---

### Post by shawnhcorey on 2010-06-05
I have installed Xubuntu 10.04 and I want to know the best way to install the DVD codecs.  I have look at the various pages at Ubuntu and elsewhere but they're all for the PC.  Does anyone know where there are instructions for the PowerMacs?

---

### Post by conal on 2010-06-05
Have you tried my method for installing the codecs?

Looks like it has worked for someone else running lucid;-

[http://ubuntuforums.org/showthread.php?t=1385579&highlight=conal](http://ubuntuforums.org/showthread.php?t=1385579&highlight=conal)

cheers

Conal

---

### Post by rjcalifornia on 2010-06-05
> **shawnhcorey said:**
> I have installed Xubuntu 10.04 and I want to know the best way to install the DVD codecs.  I have look at the various pages at Ubuntu and elsewhere but they're all for the PC.  Does anyone know where there are instructions for the PowerMacs?

take a look at this:

[http://ubuntuforums.org/showthread.php?t=1265921](http://ubuntuforums.org/showthread.php?t=1265921)

cheers!:popcorn:

---

### Post by sha.goyjo on 2010-06-06
Okay, this isn't so complicated that we need to be pushing kubuntu on somebody. The tutorial Conal linked to will work just fine. I don't think we should advocate installing completely new desktop environments just for the sake of a codec or two.

Not to say that Kubuntu isn't a well respected DE, but I don't think that this is a situation appropriate piece of advice. I think you can appreciate that.

---

### Post by shawnhcorey on 2010-06-12
Sigh.  I can't get it to work.

I followed [conal]("http://art.ubuntuforums.org/member.php?u=198579") advice and downloaded and installed:
[LIST]
[*]libstdc++5_3.3.6-18_powerpc.deb
[*]ppc-codecs_20071007-0medibuntu1_powerpc.deb
[*]libdvdcss2_1.2.10-0.2medibuntu1_powerpc.deb
[/LIST]

That didn't work, so I installed gxine.  That plays some DVDs but the resolution is tiny, something like 320x180.  When I go full screen, it's pixelated.

Then I tried installing some gstreamer codecs as advised on the [Multimedia Codecs]("https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html").  Now when Totem starts, it no longer wants to search for plugins but goes straight to the error message.  gxine has no change.

Anyone have any suggestions?

PS: I have added the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") but still no luck.

---

### Post by rjcalifornia on 2010-06-12
> **sha.goyjo said:**
> Okay, this isn't so complicated that we need to be pushing kubuntu on somebody. The tutorial Conal linked to will work just fine. I don't think we should advocate installing completely new desktop environments just for the sake of a codec or two.

Not to say that Kubuntu isn't a well respected DE, but I don't think that this is a situation appropriate piece of advice. I think you can appreciate that.

ooops my bad... In my post, go to the Xine section, follow the instruction and done.

---

### Post by shawnhcorey on 2010-06-14
Well, after some playing around, I decided that what it's doing is swapping the odd and even pixel columns.

I loaded the VLC video viewer and used it to take a snapshot of the DVD when it was playing.  The picture came out correct even though the image on screen was still wrong.  It tried using the Application->Accessories->Snapshot, which captured the window frame and controls, but not the DVD image.  The strange thing is that when I viewed the image using the image viewer and VLC was running underneath, the image appeared but its location was determine by VLC.  If I moved VLC and brought the viewer back on top, the DVD image within the picture moved to align with the VLC one.  Strange.  There must be some sort of magic pixel value to allow this.

Since this swapped columns problem appears in VLC, gxine, and xine-ui (I couldn't get totem to work), I beginning to think it has something to do with my video modes.  The question is what.

---

### Post by linuxopjemac on 2010-06-16
Shawncorey: Can you post your xorg.conf file? Tell me what PowerBook you are using. Maybe your xorg file can be improved to support video better. Just my 2 cents to this problem.

---

### Post by shawnhcorey on 2010-06-16
> **linuxopjemac said:**
> Shawncorey: Can you post your xorg.conf file? Tell me what PowerBook you are using. Maybe your xorg file can be improved to support video better. Just my 2 cents to this problem.

I have a PowerBook G4 Titanium running Xubuntu 10.04.  There is no xorg.conf:
```
$ sudo find / -iname xorg.conf
$

```

Geek Goodies:
```
$ uname -a
Linux mungo 2.6.32-22-powerpc #36-Ubuntu Thu Jun 3 23:00:32 UTC 2010 ppc GNU/Linux
$ cat /proc/cpuinfo
processor	: 0
cpu		: 7455, altivec supported
clock		: 800.000000MHz
revision	: 2.1 (pvr 8001 0201)
bogomips	: 79.95
timebase	: 33331668
platform	: PowerMac
model		: PowerBook3,4
machine		: PowerBook3,4
motherboard	: PowerBook3,4 MacRISC2 MacRISC Power Macintosh
detected as	: 73 (PowerBook Titanium III)
pmac flags	: 0000001b
L2 cache	: 256K unified
pmac-generation	: NewWorld
Memory		: 512 MB

```

---

### Post by linuxopjemac on 2010-06-16
G4 with 15 inch screen max resolution 1280 by 854 and an ATI Mobility Radeon 7500 card.

I will try to find a nice xorg.conf for this one.

---

### Post by linuxopjemac on 2010-06-16
can you give me the output of:

```
cvt 1280 854
```

---

