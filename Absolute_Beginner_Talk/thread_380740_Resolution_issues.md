---
title: "Resolution issues"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Cilionelle on 2007-03-10
Like lonelynoob (I feel ya, man!), I am also stuck at 640-480 (or so...).  Fortunately, I have internet connectivity, to a degree, and unfortunately, I am unable to get a "lock" on /var/cache/apt/archives/lock.  How do I adjust my screen size when the only option is the one above?

---

### Post by taurus on 2007-03-10
You just need to install a driver for your graphic card and what is it anyway?

---

### Post by Cilionelle on 2007-03-10
it's an intel integrated graphics card, the Intel 845 set, I think.  65mb integrated.  Something low anyway.

---

### Post by taurus on 2007-03-10
I think you need to use "i810" driver for it so what does your /etc/X11/xorg.conf look like?

```
cat /etc/X11/xorg.conf
```

---

### Post by Cilionelle on 2007-03-10
There's a lot of information in there, but you're right, it is using the i810 driver - it's the 82845G/GL/GE Chipset.

Section "Device"
     Identifier     "Intel Corporation 82845G/GL [Brookdale-G]/GE Chipset Integrated Graphics Device"
     Driver     "i810"
     BusID     "PCI:0:2:0"
EndSection

Section "Monitor"
     Identifier     "Generic Monitor"
     Option     "DPMS"
EndSection

Section "Screen"
     Identifier     "Default Screen"
     Device     "Intel Corporation 82845G/GL [Brookdale-G]/GE Chipset Integrated Graphics Device"
     Monitor     "Generic Monitor"
     Default Depth     16
     Subsection "Display"
          Depth     1
          Modes     "1024x768" "800x600" "650x480"
     EndSubSection
     Subsection "Display"
          Depth     4
          Modes     "1024x768" "800x600" "650x480"
     EndSubSection
     Subsection "Display"
          Depth     8
          Modes     "1024x768" "800x600" "650x480"
     EndSubSection
     Subsection "Display"
          Depth     15
          Modes     "1024x768" "800x600" "650x480"
     EndSubSection
     Subsection "Display"
          Depth     16
          Modes     "1024x768" "800x600" "650x480"
     EndSubSection
     Subsection "Display"
          Depth     24
          Modes     "1024x768" "800x600" "650x480"
     EndSubSection
EndSection

---

### Post by taurus on 2007-03-10
Edit /etc/X11/xorg.conf

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```
and change this line

```
Default Depth 16
```
to this one.

```
Default Depth **24**
```
Save it and press <Ctrl><Alt>Backspace to restart X.  Now, do you get a higher resolution, 1024x768, at all?

---

### Post by Cilionelle on 2007-03-10
Nope.  I got this message:

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

Then there are two buttons, a yes one and a no one.

---

### Post by taurus on 2007-03-10
Press no and it would drop you into a console.  Just copy the original version back again with

```
sudo cp /etc/X11/xorg.conf.bak  /etc/X11/xorg.conf
startx
```
Can you paste the output of this command here?

```
lspci
```

---

### Post by Lonelynoob on 2007-03-10
lonelynoob checking in..   

Hate me if you like, I understand.. I have no idea when or how to use these command lines you're talking about ...  I'm trying to follow along to get my reso working while I give up on the wireless and I can't do that either....

AUGH!  I hate being this clueless...

---

### Post by taurus on 2007-03-10
Open a terminal and enter those commands.

Applications -> Accessories -> Terminal

---

### Post by Lonelynoob on 2007-03-10
It's okay, I'd hate me to:

I still don't know what to type into the terminal.  everything just says "unknown file or directory or "unknown mime type etcetc..."    This is all greek to me.. I'm so sorry.

---

### Post by taurus on 2007-03-10
Try to type this in a terminal and see what's the output would be.

```
lspci
```

---

### Post by Lonelynoob on 2007-03-10
Bear in mind that I don't have the internet on the ubuntu machine  so I'm typing this all in by hand on the xp machine that does...   I'm just reminding myself that some people don't own shoes....  UGH.....

Host bridgeL Toshiba America Info Systems CPU to PCI Bridge
Communication Controller: Agere Systems 56k modem
VGA compatible controller S3 Inc, Virge MX (rev 06)
USB Controller: Nec Corporation USB (rev 02)
IDE Interface: Toshiba America Info Systems EX-IDE Type-B (rev 34)
Communication Controller Toshiba America Info Systems FIR port (rev23)
Cardbus BridgeL T.A.I.S (getting sick of typing it) ToPIC97 (rev 07)
Cardbus Bridge: same as abaove
Ethernet controller: Realtek Semiconductior Co Ltd, RTL8180L 802.11b MAC (rev 20)


ahhhh...


EDIT:   Okay.. anyone have any bright ideas how to get this stuff (as if I knew what to get or how to open it)  actually ONTO my Ubuntu machine?  I don't have other linux based machines to move files from and I can't get it to connect to the internet because the wireless doesn't work...   Someone said that Ubuntu was easy... where the hell did that guy go?   (sorry I'm just getting mad....)

---

### Post by Cilionelle on 2007-03-10
It didn't drop me into the prompt... I got a flashing cursor... and that was all.  Then, ta da!  there it was.  So, the output of that command is:

00:00.0 Host bridge: Intel Corporation 82845G/GL [Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL [Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI Bridge: Intel Corp. 82801 PCI Bridge (rev 82)
00:1f.0 ISA Bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE Interface: Intel Corp. 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia Audio Controller: Intel Corp. 82801DB/DBL/DBM (ICH/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet Controller: Broadcom Corp. BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

Where to now?

@Lonelynoob: Suck it in man!  You're doing great.  I just typed all that out, so you can too!

---

### Post by Lonelynoob on 2007-03-10
@Cilionelle...

I gotta tell ya man, I'm about to lose it..  after decades of using these ol' thinkin' machines of ours, I'VE never worked so long at one or two Tiny Basic concepts and made so LITTLE, if ANY, progress due to things being so wildly unclear.  Usually something would've happened by ACCIDENT by now....

ugh.. it's been almost 10 hours since I started this, maybe I should forget it for a while...

---

### Post by JeffAlbertson on 2007-03-10
Yes!   Step away and regroup.  Take a few minutes/hours/days.   Don't abandon it.  I've been working up the nerve to go Windowless for years, and I know less than you do about Linux.  Just take it in small doses.  If you get frustrated, back away for a while.  There is no reason you shouldn't have fun learning this. 

Just my $0.02.

](*,)

---

### Post by Cilionelle on 2007-03-10
Well, lonelynoob, seems like you're doing better than you think... I've been a member here since June and I'm only where you're at now!

Seriously, though, it's a steep learning curve.  Follow up on some of the links people have given you and have a read.  Stop treating it like some sort of test and just sit back and say, "This is so not Windows!"  Then take some time and eat chocolate or something.  Or shoot something in America's Army or something.

Then come back to it.

Then kick its opensource butt all over your Toshiba!

---

### Post by Cilionelle on 2007-03-10
Hi!  Still here!  Still need some help... please?  Thanks!

---

### Post by Lonelynoob on 2007-03-10
Hey man, still here too.  Thought I'd give it a bump back up to the top.. I'm writing a new post with every question I can think of....

I woke up today and despite my prayers and dreams, the laptop hadn't fixed itself while I slept.
dammit.

---

### Post by Cilionelle on 2007-03-10
lol! mine neither, although my internet (for browsing, not updating) is back up and running, thanks to some help I got this morning.  Still stuck at 640x480, with no way to download extra programs/packages/etc.

---

### Post by dedhead66 on 2007-03-10
> **Cilionelle said:**
> Like lonelynoob (I feel ya, man!), I am also stuck at 640-480 (or so...).  Fortunately, I have internet connectivity, to a degree, and unfortunately, I am unable to get a "lock" on /var/cache/apt/archives/lock.  How do I adjust my screen size when the only option is the one above?

I'm new at this also but I'll try to help you.

Go to:
System
Administration
Synaptic Package Manager

Type in the search box:
ati

4 boxes down you should see 915resolution. Check that box. Mark for Installation. Then APPLY.



"resolution modification tool for Intel graphic chipset
915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient.
There is no risk of permanent modification of the BIOS.
This also means that 915resolution must be run every time the
computer boots in order for its changes to take effect.
If you want to automatically set the resolution on each boot
and before X is launched, see /usr/share/doc/915resolution/README.Debian
for information about configuring the provided initscript.

Web site: http://www.geocities.com/stomljen/"

I'm not sure this will help you but it might be worth a try.

---

### Post by Cilionelle on 2007-03-10
It's a good plan, but for some reason, even though I can browse the Internet, I cannot connect to the update bits to get that programme.  So, I guess I need to fix that problem first!

---

### Post by dedhead66 on 2007-03-11
I wish I could help more. I just installed Ubuntu last week and only Friday got my wireless connection to work so I still have much learning to do.

Best of luck to you.

---

