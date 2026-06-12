---
title: "unable to change resolution and no modem on pbook 550"
date: 2005-04-20
forum: Apple PPC Users
---

### Post by muzza on 2005-04-20
I've been using Warty on my PC for a few weeks now and have found it easy to tweak things to get them working with help from searching various forums.

I've just got Hoary ppc and installed it on my titanium G4 550mhz powerbook and I'm getting frustrated now.

I couldn't get it to dual boot, it kept sending me back to the partitioner to fix whatever problem there was, but being (still) a newbie, I thought the easiest option was to just install Ubuntu for now.

So, now it's installed.

Only got a screen resolution of 640x480, 60Hz,  no other options.

Did a search and found that someone fixed a similar problem by typing;
sudo dpkg-reconfigure xserver-xorg

the terminal said this;

debconf: Unable to initialize frontend: Gnome
debconf: (Unable to load Gnome - -  is libgnome2-perl installed?)
debconf: falling back to frontend: Dialog

Then it took me through a number of configuration screens, most of which I just accepted the default as I'm still a newbie, chose the default resolution of 1152x768 and when it finished the tenminal said;

expr: non-numeric argument

I went back to the resolution control panel and it still wouldn't let me change.


Searched the forums again and found another similar problem [here](http://ubuntuforums.org/showthread.php?t=26420) but I didn't understand the solution.

I typed in;
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
$sudo gedit /etc/X11/xorg.conf

and here the details the helper wanted; (I can't cut and paste as the modem isn't working yet.  Have to type in manually)

Section "Monitor"
          Identifier          "Color LCD"
          Option              "DPMS"
EndSection

Section "Screen" 
          Identifier         "Default Screen"
          Device             "ATI Technologies, Inc. Radion Mobility 9000 (M6 LY)
          Monitor            "Color LCD"
          DefaultDepth   "24
          Subsection "Display"
                           Depth         1
                           Modes         "1152x768"
*This SubSection was repeated with subsequent depths of 4,8,15,16 and 24*
           EndSubSection
EndSection

I think this section may be important too.

Section "Device"
        Identifier       "ATI Technologies, Inc. Radion Mobility 9000 (M6 LY)
        Driver            "ati"
        BusID             "PCI:0:16:0"
        Option            "UseFBDev"
EndSection

The helper asked to type the following too:

$sudo zresprobe ati
id: Color LCD
res: 1152x768
freq:
diptype: lcd/lvds

That's all I've done so far and I can't use a computer with 640x480 resolution.

I haven't even tried to get the modem going yet.  Too tired.  I'll try later.

BTW, when its booting up, I noticed this on one of the second line of the boot screen, I don't know if it means anything.

radeonfb (0000:00:10.0): invalid ROM signature 8080 should be0xaa55

---

### Post by Vache on 2005-04-20
> **muzza]I've been using Warty on my PC for a few weeks now and have found it easy to tweak things to get them working with help from searching various forums.

I've just got Hoary ppc and installed it on my titanium G4 550mhz powerbook and I'm getting frustrated now.

I couldn't get it to dual boot, it kept sending me back to the partitioner to fix whatever problem there was, but being (still) a newbie, I thought the easiest option was to just install Ubuntu for now.

So, now it's installed.

Only got a screen resolution of 640x480, 60Hz,  no other options.

Did a search and found that someone fixed a similar problem by typing said:**
> here[/URL] but I didn't understand the solution.

I typed in;
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
$sudo gedit /etc/X11/xorg.conf

and here the details the helper wanted; (I can't cut and paste as the modem isn't working yet.  Have to type in manually)

Section "Monitor"
          Identifier          "Color LCD"
          Option              "DPMS"
EndSection

Section "Screen" 
          Identifier         "Default Screen"
          Device             "ATI Technologies, Inc. Radion Mobility 9000 (M6 LY)
          Monitor            "Color LCD"
          DefaultDepth   "24
          Subsection "Display"
                           Depth         1
                           Modes         "1152x768"
*This SubSection was repeated with subsequent depths of 4,8,15,16 and 24*
           EndSubSection
EndSection

I think this section may be important too.

Section "Device"
        Identifier       "ATI Technologies, Inc. Radion Mobility 9000 (M6 LY)
        Driver            "ati"
        BusID             "PCI:0:16:0"
        Option            "UseFBDev"
EndSection

The helper asked to type the following too:

$sudo zresprobe ati
id: Color LCD
res: 1152x768
freq:
diptype: lcd/lvds

That's all I've done so far and I can't use a computer with 640x480 resolution.

I haven't even tried to get the modem going yet.  Too tired.  I'll try later.

BTW, when its booting up, I noticed this on one of the second line of the boot screen, I don't know if it means anything.

radeonfb (0000:00:10.0): invalid ROM signature 8080 should be0xaa55
 A weak effort is made to detect your monitor/screen's h and v sync - You'll have to Google for them and manually add them in. This is how I fixed the issue with my monitor (Dell 1905FP, 1280x1024@76Hz)

---

### Post by muzza on 2005-04-20
OK, I've sorted out the resolution, even though I'm not sure how.

I've been on the 'net most of today and I eventually guessed at the closest vert/horiz refresh stuff (HorizSync 30-70 VertRefresh 50-160) and also commented out the UseFBDev line (Why?  Cause the man on the 'net told me too!)

Now it gives me 4 options, 1152x768 being one of them, which is what I was looking for!  

Whatever works, eh?  Yeehaah!

Can't find any info on the modem tho.

Should I start another thread?

---

