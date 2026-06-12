---
title: "ATI graphics card problem"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by aleksevich on 2007-09-14
I'm very new to Ubuntu and to Linux in general. Seems like I there were more threads about the same problem that I have but I just don't understand really what to do.
I have a PCI ATI Radeon 9200 graphics card. When I booted from the instalation disk it came to the menu where I could choose if I wanted to install and other options. But when I clicked install  it seemed to start doing something - the progress bar appeared - but that's it, it just froze there in the beginning of the progress bar. I thought that maybe I had to wait longer, so I did. And, no, nothing still was there after three hours.
So, then I pluged the monitor to the on-board video adapter - and it worked just fine. In the hardware list I could even see my ATI card. Then I tried to restart with the monitor oluged to the PCI card - the same again: the progress bar just freezing at the beginning and not going anywhere.
Please, help me, somebody! Ubuntu is such a great system. It works fine like this but I want to be able to use advantages of having the graphics card.

---

### Post by w4ett on 2007-09-14
Question:

Is Ubuntu installed now, or are you running off the live CD?

---

### Post by aleksevich on 2007-09-14
> **w4ett said:**
> Question:

Is Ubuntu installed now, or are you running off the live CD?

It is installed. I'm running it with the on-board graphics. When I use the PCI card I can not even run the live CD.

---

### Post by w4ett on 2007-09-14
> **aleksevich said:**
> It is installed. I'm running it with the on-board graphics. When I use the PCI card I can not even run the live CD.

You will have to disable to on-board GFX chipset in bios, or on your motherboard there might be a jumper to remove to disable this.

---

### Post by aleksevich on 2007-09-14
> **w4ett said:**
> You will have to disable to on-board GFX chipset in bios, or on your motherboard there might be a jumper to remove to disable this.

The motheboard doesn't support jumper disabling but I do disable it in BIOS but it still doesn't work.

---

### Post by w4ett on 2007-09-14
OK.... from the terminal post the results of the command:

```
lspci
```

---

### Post by aleksevich on 2007-09-14
> **w4ett said:**
> OK.... from the terminal post the results of the command:

```
lspci
```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
02:03.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
02:04.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev 10)
02:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)

---

### Post by w4ett on 2007-09-14
We'll try to modify your xorg.conf manually:
```

sudo gedit /etc/X11/xorg.conf
```

in the terminal and scroll to thie section that looks like this:

> Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Boardname       "ati"
        Busid           "PCI:1:0:0"
        Driver          "ati"
        Screen  0
        Option          "MergedFB"      "off"
:
(NOTE: Yours won't look exactly like this one...)

This is the bus ID for your ATI card:

> 02:03.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

edit your driver to read [COLOR="Red"]"ati"[/COLOR]

edit your Busid to read: [COLOR="Red"]02:03.0[/COLOR]

edit your Identifier to read:   [COLOR="Red"] "ATI Technologies Inc RV280 [Radeon 9200 PRO][/COLOR]"

Save your edit.  and do <Ctrl><ALT><Backspace> to restart x........

keep your fingers crossed.  :)

---

### Post by aleksevich on 2007-09-14
> **w4ett said:**
> We'll try to modify your xorg.conf manually:
.......
Save your edit.  and do <Ctrl><ALT><Backspace> to restart x........

keep your fingers crossed.  :)

OK, I'm doing it. (with my fingers crossed, and thinking positively).

---

### Post by aleksevich on 2007-09-14
> **w4ett said:**
> ......
Save your edit.  and do <Ctrl><ALT><Backspace> to restart x........

keep your fingers crossed.  :)

I guess I uncrossed my fingers somewhere during the process. :) It didn't work.
I have a doubt if i did this right. First, you said that I had to change this line 
Busid "PCI:1:0:0" to this
Busid "PCI:02:03.0"
Is that right?
Then, the xorg.conf section "Device" there was only the Intel (integrated) video adapter listed. So I changed the identifier to "ATI Technologies Inc RV280 [Radeon 9200 PRO]". DId I do it right?
Oh, when I rebooted again with the integrated video it couldn't start the X. So I'm working from XP now.
Now, do I have to reinstall Ubuntu again or is there a way to recover the system?
Thanks for your time.

---

### Post by w4ett on 2007-09-14
Boot into recovery mode and type:

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Blue"]"intel"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This shouldl get you to a GUI desktop.

Edit: additional question:   Maybe a silly one  but, does the card work during the post sequence i.e.: can you see the Bios boot sequence and motherboard boot information?

---

### Post by aleksevich on 2007-09-14
Thank you!
I'll do it a bit later. gotta do some stuff.
Do you think I should still try to make my ATI card work with Ubuntu? Are there other ways to fix the problem? I tried the alternate CD too but still the same. It didn't even give me the choice of celecting the primary or secondary display adapter.

---

### Post by w4ett on 2007-09-14
IMHO...I'd start looking at hardware issues.......if this is a brand new card, this is less suspect, but possible.  Like I asked before, do you see the post screen when you are using the card, or just get no display (black screen)?  if so, I'd test the card in another machine to rule out a dead card.....

I have found in the past the 9200/9250 PCI cards can be a pain to get running...sometimes impossible....there are several bugs reported for this series card in Launchpad, and no real fixes.  I.E. they either work or they don't...no in between status (Partially Working)

Let us know how you get on.

Good Luck

---

### Post by aleksevich on 2007-09-14
> **w4ett said:**
> 

Let us know how you get on.

Good Luck

Thanks again.
Well, that's a little disappointing. Anyway, I think Ubuntu is just to nice to give up because of this. I guess I don't need 3d acceleration and stuff so much. Just will have to switch between adapters because I run XP from time to time to play games. Ok, I'll wait till I can buy another card or another computer. :guitar:

---

### Post by steevols on 2007-09-14
POSSIBLE quick fix...

I have a 9250 card, which at least in Windows is the same as a 9200 when it comes to drivers, so my solution may work.

Backup xorg.conf, and the go to the device section. Simply set your driver as "radeon" and remove all extra options. The identifier doesn't matter, really. It's just for reference.

it worked for me, I hope it does for you.

---

### Post by Arsic on 2007-09-14
I also have a 9250 card and all the help posted in this thread doesn't work when you want Compiz Fusion or Beryl/Compiz effects.

I read somewhere (forgot where), but the drivers for ATI's older cards, 9300 and under, had thier support dropped. It could be another reason to why it's so hard to get those cards working (I don't think I've seen anyone with the 9300 and under say they had them working anyway).

Oh and choosing vesa when you run *sudo dpkg-reconfigure xserver-xorg* also gets your card working (it does for mine anyway).

---

