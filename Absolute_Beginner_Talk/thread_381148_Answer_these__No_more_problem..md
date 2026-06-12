---
title: "Answer these:  No more problem."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Lonelynoob on 2007-03-10
All right, I'll break it down as best as this hopeless clueless person can.  For the first time in many years: I simply no longer care how dumb I sound.

First off, here's the list...:
Host bridgeL Toshiba America Info Systems CPU to PCI Bridge
Communication Controller: Agere Systems 56k modem
VGA compatible controller S3 Inc, Virge MX (rev 06)
USB Controller: Nec Corporation USB (rev 02)
IDE Interface: Toshiba America Info Systems EX-IDE Type-B (rev 34)
Communication Controller Toshiba America Info Systems FIR port (rev23)
Cardbus BridgeL T.A.I.S (getting sick of typing it) ToPIC97 (rev 07)
Cardbus Bridge: same as abaove
Ethernet controller: Realtek Semiconductior Co Ltd, RTL8180L 802.11b MAC (rev 20)


The questions:  First, the Wireless...
1) If need a driver, how do I get it to work on Ubuntu?
2) before you say "ndiswrapper" please explain what the hell that is, where I get it, whether or not I install it, and how the #$% to use it.  
3) How do I actually get it ON my machine? - do I need to save the driver on something other than a regular windows-formatted disk? What's with the jumping through hoops to get the files on the floppy looked at?  Where's the ubuntu equivalent of Windows "Explore'"? (not Explorer, but Explore.)
4) How do I use/load/copy-over and install the driver?
5) All the commands/command lines you told me to use in 2, 3 and 4? - What the hell do they mean?
6) I'm used to the paradigm that I can just "search" for available wireless networks.  Can I do that or do I need all the info about the wireless signal? (I imagine I'll need the wep and all, but whatever).

My resolution:
7) It's stuck at 640x480. There's no other option.  Do I need drivers? Where do I get it?
8) How do I install that?  Painful step-by-step please.
9) What EXACTLY do I need to type and where?    (In another thread I tinkered with some 'xorg.conf' thing in its "default settings" and nothing changed.  I had no idea what I was doing, mind you.)

*If* I had money, which I don't, I'd paypal the first person who can answer all those - with screenshots would be even nicer.  Yes, I need to be held my the hand.  My penis is also small and I don't care anymore.  Wicked.

In my first 24 hour descent in the world of Linux, I find that the biggest weakness is nearly 100% of help files/thread/pages tell people what to do, but hardly anyone explains what they're saying or why it works - which is the single thing completely stupid people like myself need.

---

### Post by Crooksey on 2007-03-10
1) Install ndiswrapper from the ubuntu cd ...

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-25f7f86dc646b1632ab4b82830a7e26dd5cefc2c](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-25f7f86dc646b1632ab4b82830a7e26dd5cefc2c)

Then get the windows inf driver on a data stick and copy it into your home folder.

Now run the command .

```

$ sudo ndiswrapper -i wifidriver.inf

```

See if it worked..

```

$ sudo ndiswrapper -l

driver.inf : hardware present, driver persent
```

Then get it working..

```

$ sudo modprobe ndiswrapper

```

Did it work?

```

$ iwconfig

```

If you get a result, sorted.... lets say your device is eth1, it may be wlan0 or something

```


$ sudo iwconfig eth1 essid "youressid"
$ sudo iwconfig eth1 key YOURNETWORKKEY #leave if open wifi network
$ sudo dhclient eth1

```

Sorted!

--

Resolution....

```


$ sudo gedit /etc/X11/xorg.conf

```

Find the screen section with the other resolutions, change to the resolution you want.

Then save, then press "crtl+alt+backspace" to reload the X server with the new resolutions.

^Its free info, enjoy!

Any trouble post back, ill stay around all night if i have to help you get this working :)

---

### Post by Lonelynoob on 2007-03-10
See how amazing of a person you are?

-- All I hafta do it try all that.    I'll totally get back to you when I get it done.. (I'm tempted to install 6.10 instead of 6.06.. should I do that?)


EDIT:
See that sentence where you say "Copy it into your home folder" ?  Those are those little sentences where I think people think I know how to do that.  (told you I was stupid...)   I can solve a rubik's cube if it makes anyone feel better, I swear.

---

### Post by Crooksey on 2007-03-10
On your desktop there is a folder called "home" or just in the places menu from your panel click "home", then drag and drop the inf driver there.

---

### Post by Cilionelle on 2007-03-10
Crooksey, thanks, but (like my man lonelynoob) I have no idea how to do some of these things, like "choose the resolution you want".  How does that work?  What value in xorg.conf do I need to change?  Last time I changed the "DefaultDepth" setting, X died.

---

### Post by Crooksey on 2007-03-10
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

Just delete all resolutions listed there apart from the ones you want. (This section is found at the bottom of the file)

---

### Post by Lonelynoob on 2007-03-10
Okay.. I installed 6.10... now my wireless card isn't even receiving power anymore...  Edgy doesn't even notice it's there...    So I now have teh problems listed above and no wireless....     --Not that the wireless was working in the first place....

I'm gonna go count to 50.  84 times.

EDIT:  and the xorg.conf "dispslay" editing for the resolution didn't do anything....  I'm still sitting at 640x480

---

