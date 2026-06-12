---
title: "B&amp;W PowerMac G3 &amp; ATI Radeon 7000"
date: 2007-05-11
forum: Apple PPC Users
---

### Post by odelay on 2007-05-11
Well I've spent the last couple of days trying to get Ubuntu Feisty (Server) up and running on my Yosemite Rev1 Blue & White PowerMac G3 with 768 MB RAM [gasps for air].  

Before getting started with my main problem, I wanted to outline what I did, in order to hopefully save some other B&W users some time and frustration.  Feel free to skip this paragraph.  If you were unlucky enough to get a Rev1 model like I was, recall that Apple shipped them with a [problematic IDE Controller]("http://en.wikipedia.org/wiki/Blue_and_white_Power_Macintosh_G3").  Basically, you either had to use the special IDE drive (probably around 6 GB) or you had to get a Sonnet ATA PCI Card to allow you to use larger/newer drives.  I had 40 & 60 GB drives hooked up to the PCI card, and working fine in Tiger.  I don't know about anyone else, but I was unable to install Ubuntu on either of these drives.  My solution was to first take out the 2 drives, then dig up and install the old 6 GB IDE drive.  I was able to install Feisty Server fine without the annoying yaboot error.  I then added the 60 GB ATA to the PCI card, put the install CD back in, and reformatted the drive, setting the mount point as "/media/sda2".  So I basically now have a 6 GB root partition and a 60 GB storage partition.  Nice.

OK...now to the problem.  While I am using the server install disk, this wasn't intended to be a "pure" server...more of a test machine and file server.  That said, no need to debate why I'm trying to put a GUI on a server.

After installing gnome-core, gdm, xorg, and the like I tried starting X.  No luck.  I tried running the xserver reconfig tool.  No luck.  I tried manually editing xorg.conf, particularly disabling DRI, trying the ati and radeon drivers, enabling/disabling fbdev, and more.  Still no luck.  When I go to start X or gdm the screen either goes blank (gdm) or spits back some errors (startx).  Since I'm typing this on a different computer, I don't have the exact errors, but they seemed to be tied to the PCI ATI 7000 (it's xserver...duh).

Has *anyone* gotten the PCI ATI Radeon 7000 working on B&W G3?  I've scoured the forums, and it seems like some people must have it working.  I may also have the original Rage128 lying around somewhere...would that be a better bet?  I don't know the model of monitor I'm using, other than that it's a 17" PowerComputing (there's a flash from the past)...could that be part of the problem?

There are just so many variables here...so I can't be sure if the root of the problem lies solely in the 9700.

Thanks in advance!

---

### Post by odelay on 2007-05-12
OK...here's the error output I get after entering "startx".  Since I couldn't find a way to copy/paste the output, I had to manually write it down from another computer (there has to be a better way?!)--as a result I left out a few of the backtraces...but you should be able to get a good idea of what's going on.  Once again, thanks for any help!

```
(WW) ****INVALID IO ALLOCATION**** b: 0xfe004000 e: 0xfe0040ff correcting
(EE) end of block range 0xfdfffffff < begin 0xfe000000
(**) RADEON(0): RADEONPreInit

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x94) [0x10090c04]
1: [0x100344]
2: /usr/lib/xorg/modules//libint10.so(LockLegacyVGA+0x50) [0xf845a50]
...
6: /usr/lib/xorg/modules/drivers/radeon_drv.so(RADEONProbeDDC+0x48) [0xf80c558]
...
10: /usr/bin/X11/X(InitOutput+0xb08) [0x1006b4e8]
...
13: /lib/libc.so.6 [0xfc5af98]


Fatal server error:
Caught signal 7.  Server aborting

XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.
```

---

### Post by didg on 2007-05-12
Hi,

The Rage 128 should work 'out of the box', at least it does on a B&W I have, not a rev1 though.

X Error log are in /var/log/Xorg.0.log

If you can copy it to an USB stick and then post it'd help but you can already try to add

Option          "NoINT10" "true"

In the section "Device" of your /etc/X11/xorg.conf

---

### Post by odelay on 2007-05-12
Also, here's my ATI section for "lspci -v":

```
00:10.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc XVR-100 (supplied by Sun)
        Flags: bus master, stepping, 66MHz, medium devsel, latency 16, IRQ 22
        Memory at 88000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 4000 [size=256]
        Memory at 80b00000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at 80000000 [size=128K]
        Capabilities: <access denied>
```

---

### Post by odelay on 2007-05-12
> **didg said:**
> If you can copy it to an USB stick and then post it'd help but you can already try to add

Option          "NoINT10" "true"

In the section "Device" of your /etc/X11/xorg.conf

Ahh!!  Thanks so much.  I'm not positive if it was this option or setting fbdev to "false" (which I had tried before, but with a different monitor) that helped, but now xserver seems to "start."

The problem is it only loads a grey, speckled background & a functional mouse.  There is no gdm or anything.  I'm going to try messing around with it some more, and post back my findings.

Once again, thanks for the tip!

p.s.  BTW, what exactly did adding that option do?  I like have at least a surface understanding of whatever I'm doing.

---

### Post by odelay on 2007-05-12
Great news!!  I update the "gnome-core" package, and now I have gnome up and running.  Granted, the resolution isn't spot on...but this is great.  Thanks again **didg**.

---

### Post by didg on 2007-05-12
Use gdm rather than startx

---

### Post by Bikerbob on 2007-10-10
I am having this exact problem.

I used the Fiesty alt. install and I could get to the point of starting the X server and then nothing.

The error is the same as in this thread.

I do have 16mb Rage adaptors lying around.. so I installed one and rebooted.. YAHOO I am in .. and it works fine.


But I do dual boot this machine and I run a couple of games on the OS X side.. SO I would prefer to have the Radeon 7000.. and not to mention its the better card.


SO can someone walk me through what I need to change to get this working? and are we talking just functional? or with acceleration and open-gl support??

Thanks

James

---

### Post by Bikerbob on 2007-10-12
Hmmm.. I hoped there would be someone still out there that could help.

Can anyone suggest a PCI video or AGP.. as I might be getting a G4 DA soon.. that works with Ubuntu well?

I have a Rage 128 16mb working now.. I was able to install using the liveCD.. but the Radeon.. no go.. at least with the 7000.. Do others work better with Ubuntu?


Hope someone can contribute.

James

---

### Post by lucid42day on 2007-10-19
> **Bikerbob said:**
> Hmmm.. I hoped there would be someone still out there that could help.

Can anyone suggest a PCI video or AGP.. as I might be getting a G4 DA soon.. that works with Ubuntu well?

I have a Rage 128 16mb working now.. I was able to install using the liveCD.. but the Radeon.. no go.. at least with the 7000.. Do others work better with Ubuntu?


Hope someone can contribute.

James

I was having the very same problem with Ubuntu FF.  I flashed a Radeon AGP 7000 to work with a Mac.  I have a "Sawtooth" G4, I believe.  Adding the Option line "NoINT10"/"true" as specified above did solve my problem.  From the xorg.conf manual page, it appears this switch "true" stops the xorg server from initializing the graphics card in the normal way.

---

### Post by Phaldor on 2007-10-25
Well, as it happens, I updated to Gibbon today at work, with a Dell Precision 650 built from spare parts that had a Radeon 7000/VE dual head in it.  Sure enough, it didn't want to start the GDM after reboot, so I went to work trying to figure it out.  I had a lot of time invested in this from the upgrade to Fiesty several months ago, and had the xorg.conf tricked out to the max when it came to the card and monitors.  After following this thread, it still wasn't working.

I tinkered around some more, going through the detailed report (oh, I should mention that I was getting an error 11, not a 7, but otherwise, this is the same thing), and I happend to hit upon the solution.  Seems I had left Xinemera on when I had the system hooked up to dual monitors.  Fiesty didn't have an issue with this, but apparently, Gibbon does.  The long and the short of this is that all I had to do is comment out this option and I was back in business!  Not an easy thing to find though, so those of you with dual monitors, looks like DRI has a problem with Xinemera turned on in Gibbon.

---

