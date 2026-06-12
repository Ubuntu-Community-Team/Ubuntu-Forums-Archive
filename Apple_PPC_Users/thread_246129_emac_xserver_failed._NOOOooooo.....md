---
title: "emac: xserver failed. NOOOooooo...."
date: 2006-08-28
forum: Apple PPC Users
---

### Post by dented42 on 2006-08-28
woe is me.

allright, enough of this melodrama.

I have an emac.  and am trying to boot from the live cd.  the xserver failes to load properly or something like that.  I search the forum, and find a thread.  it tells me what I want to know.  so now I just type in "sudo dpkg-reconfigure xserver-xorg"  I do that, but the guy in the thread that I am getting this from has a pc!

so I am trying to discover the xserver configurations for an emac.  if anyone knows them, please tell me.

or if you are running ubuntu on an emac, could you go to the shell, type in "sudo dpkg-reconfigure xserver-xorg" and then where user input is desired, you current setting will be highlighted, so if you press enter a bunch of times, nothing will change, BUT could you please write down what settings you have.

or is there an easier way to do this?:confused:

I really dont know


I apologize in advance that I know so little about my computer.:(

---

### Post by 3rdalbum on 2006-08-29
No need to apologise.

When you get to the command line, type:

```
sudo nano /etc/X11/xorg.conf
```

(That's a capital X in X11)

Now find the section which says Section "Monitor". Replace the HorizSync and VertRefresh lines with these:

```

HorizSync 30-112
VertRefresh 50-160
```

Press Control-X to exit, the Y key to save changes, and Return to confirm.

Now, back at the command line, type "startx". If all goes well, you should be logged in.

---

### Post by dented42 on 2006-08-29
will this work if I am just using the live cd?  what am I saying, of course it will.

ok, just a sec...(rustling of papers) where is tha bucket? (metalic clanging) oh, here it is...
(sound of water being poured on an idiot)  ah. that is much better.

(for the rest of this post water can be heard dripping off my body and onto the floor)

ok, back to sanity.  I do what you say, I save the modified file, and type in startx and....
I see what looks like the start of a program, and then a message saying that the server failed, at 0 something.

it seems that nothing has changed.  now what?

(or did I not follow the instructions carefully?):???:

---

### Post by dented42 on 2006-08-29
maybe the error is bacause of other parameters in the control file?

---

### Post by woopie49 on 2006-08-29
I'm only a NuBee too, but you can't save any files TO the live CD you are booting from - only if you have Ubuntu already installed on your HD.

Even if trying to install from live CD and it does not work, try again and again.

I loaded after 3 attempts, but found Ubuntu too slow to use from the live CD, so I loaded to HD.

If, the CD use are using is faulty, download the Ubuntu ISO file again, burn and try using the new Live CD or load to HD

Ron

---

### Post by 3rdalbum on 2006-08-30
You can "save files to the Live CD". They actually get saved into memory, but are treated as though they are on the CD.

Make sure your xorg.conf file says that it is using the "ati" driver, not the "vesa" driver (you mentioned following directions from an x86 user).

---

### Post by dented42 on 2006-08-31
<pre>yes indeed, one can as you say, save to the CD.  however, I will do what I should have done at the start, (I was hoping not to have to transcribe this but, here I go)  and I will list the parameters in my xorg.conf file(note this might not be complete, but I can't bear to type it in one sitting):

Section "Files"
     FontPath     "/usr/share/X11/fonts/misc"
     FontPath     "/usr/share/X11/fonts/cyrillic"
     FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
     FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
     FontPath     "/usr/share/X11/fonts/Type1"
     FontPath     "/usr/share/X11/fonts/100dpi"
     FontPath     "/usr/share/X11/fonts/75dpi"
     # path to defoma fonts
     FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
     Load     "bitmap"
     Load     "ddc"
     Load     "dri"
     Load     "extmod"
     Load     "freetype"
     Load     "glx"
     Load     "int10"
     Load     "type1"
     Load     "vbe"
EndSection

Section "InputDevice"
     Identifier     "Generic Keyboard"
     Driver         "kbd"
     Option        "CoreKeyboard"
     Option        "XkbRules"       "xorg"
     Option        "XkbModel"      "pc104"   
     Option        "XkbLayout"     "us"
Endsection
</pre>

---

### Post by 3rdalbum on 2006-09-01
From Section "Monitor" onwards is the crucial bit, you might want to post that when you have time.

---

### Post by bodek on 2006-09-02
Hi, you are not the only one. Yesterday I downloaded copy of 6.0.6.1 and was happy to put the CD in my eMac. Exactly the same. No Xserver.
I was thinking how can one install linux from a live CD which does not boot properly?
But all is now history. I played with the xorg.conf trying to use the auto detection, but it always got it wrong. I think what saved the day was that i used:

*sudo dpkg-reconfigure xserver-xorg*

chose ati (using ATI Radeon 9200)

don't chose autodetect monitor, instead go to advanced and give it horizontal frequency: 70-73
vertical frequency: 70-140

save and sudo startx should work

btw what are the frequences of those monitors? seen different values here?

and it should work.

After installing I downloaded updates (especially xserver-xorg-core and now have a beautiful Ubuntu.

Next problem to solve is keyboard, but that for next time.

---

### Post by dented42 on 2006-09-04
Horay!!!!!
ultra happyness!!!!!
i have hte spelling skills of a forth grader!!!!!!!
FUN:-D :KS

---

### Post by spinz8 on 2006-09-05
Hi I am happy for dented 42.
 Xserver is  now broken on my iBook G4. It all started when i tried to install 3D acceleration (Help Files). Basically i selected all the highlighted (default) indicated on the steps.  Then the horror started. The login screen sinply state "ubuntu login". I managed to get into xorg.conf editor but i d do not know which one to edit. I have looked into xorg.conf file many times before and the saved 3D acceleration files are in there for the first time.
 The horizSync 28-57
 VertRefs 43-60 
Are these settings correct? or do i need to delete this ATI settings since it was never here before?
 Please help  me restore my beloved dapper. 
Thanks.

---

### Post by spinz8 on 2006-09-05
Here's the particular file output of last installed configuration:
Section "module"
Load      "bitmap"
Load      "ddc"
Load       "dri"
Load       "extmod"
Load       "freetype"
Load       "glx"
Load       " int0"
Load       "type1"
Load       "vbe"
EndSection

Section         "Monitor"
Identifiers     "COLOR  LCD"
Option           "DPMS"
HorizSync     "28-51"
VertyRefresh "43-60"
End Section

Section    "Device"
Identifier   "ATI Technologies Inc m11 NV(FireGL Mobilitry T2e]
Driver        "ati"
BusID        "PCI:0:16:0
Option       "UserFBDev"      "true"

Section   "Screen"
Identifier  "Default Screen"
Device     "ATI Technologies Inc m11 NV(FireGL Mobilitry T2e]"
Monitor     "COLOR LCD"
Default depth "24"
SubSection    "Display"
Depth                  1
Modes            "1024 x 768"
EndSubsection
SubSection      "Display"
Depth                    4
Modes               "1024 x 768"
EndSubsection
SubSection         "Display"
Depth                        8
Modes                   "1024 x 768"
EndSection          
SubSection     "Display"
Depth                      15
Modes                 "1024 x 768"
EndSection
SubSection       "Display"
Depth                        16
Modes                "1024 x 768"
EndSubsection
SubSection          "Display"
Depth                           24
Modes                   "1024 x 768"

Section   "DRI"
Mode       0666
End section

Further inputs are greatly appreciated.
Thank you.

---

### Post by bodek on 2006-09-08
Hi to all,
finally managed to get a proper (1280x960) resolution on my eMac.
Just wanted to share with you, maybe someone will find it useful.

The live cd was dying when starting X, so we found the first solution to edit xorg.conf and change the lines in the section monitor to: HorizSync 71-73 and VertRefresh 70-140.

This was giving working X but with resolution 1024x768. So far so good, but it is a really poor resolution with the toolbars taking almost all the space.

The second was to insert modelines for the monitor:
I found two ways: using the [FONT="Courier New"]gtf[/FONT] command something like:
[FONT="Courier New"]
 gtf 1280 960 72

  # 1280x960 @ 72.00 Hz (GTF) hsync: 72.07 kHz; pclk: 124.54 MHz
  Modeline "1280x960_72.00"  124.54  1280 1368 1504 1728  960 961 964 1001  -HSync +Vsync[/FONT]

which gave the modeline for this particular resolution.

After inserting the modelines into xorg.conf (I actually made the modelines for 1280x960, 1152x864, 1024x768) I got X working, but the picture was moved some 2 inches to the left, and even xvidtune couldn't move it into proper place. So I was back to 1024x768.

After looking for another solution I found something else: a little tool called [FONT="Courier New"]read-edid[/FONT] which is in the utilities (univers) section, and when I tried it:

[FONT="Courier New"]sudo parse-edid /proc/device-tree/pci@f0000000/ATY,MerlinParent@10/ATY,Merlin_A@0/EDID

 # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "iMac"
        VendorName "APP"
        ModelName "iMac"
        # Block type: 2:0 3:fd
        HorizSync 71-73
        VertRefresh 70-140
        # Max dot clock (video bandwidth) 130 MHz
        # Block type: 2:0 3:fc
        # DPMS capabilities: Active off:no  Suspend:no  Standby:no

        Mode    "1024x768"      # vfreq 88.995Hz, hfreq 72.086kHz
                DotClock        99.190000
                HTimings        1024 1072 1168 1376
                VTimings        768 769 772 810
                Flags   "+HSync" "+VSync"
        EndMode
        Mode    "1280x960"      # vfreq 71.932Hz, hfreq 72.075kHz
                DotClock        122.240000
                HTimings        1280 1328 1424 1696
                VTimings        960 961 964 1002
                Flags   "+HSync" "+VSync"
        EndMode
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
EndSection[/FONT]

it gave me the modelines to insert into xorg.conf.
[FONT="Courier New"]# 1024x768 @ 89 Hz hsync: 72.086 kHz; pclk: 99.190000 MHz
  Modeline "1024x768_89.00"  99.190000  1024 1072 1168 1376  768 769 772 810 +HSync +VSync
# 1280x960 @ 72 Hz hsync: 72.075 kHz; pclk: 122.240000 MHz
  Modeline "1280x960_72.00" 122.240000  1280 1328 1424 1696  960 961 964 1002 +HSync +VSync[/FONT]

That's it, after restarting I have nice working, perfectly centered desktop. Long live Ubuntu and the forums.

I hope this will be of assistance to others who struggle to get the desktop proper. (Thanks to all who posted these solutions, and whose names I don't remember. Don't even remember where I got it from ](*,) )
bodek

---

### Post by pakk99 on 2006-11-06
Where do you insert these lines in xorg.conf?

---

### Post by stella on 2006-12-21
> **bodek said:**
> After looking for another solution I found something else: a little tool called [FONT="Courier New"]read-edid[/FONT] which is in the utilities (univers) section, 

Would someone mind telling me how to install this read-edid utility? I downloaded it from [here](http://packages.debian.org/stable/utils/read-edid), untarred it, and attempted to follow the instructions in the file called "INSTALL", but the "make" command won't work. I'm having the same problem this poster I quoted had, with the screen being moved about 2 inches to the left after adding a 1280x960 resolution to xorg.conf. Thanks.

---

### Post by linear on 2006-12-21
Add the Universe repository ([instructions]("https://help.ubuntu.com/community/Repositories/Ubuntu")), then use Synaptic or aptitude to install. Much easier than compiling.

---

### Post by stella on 2006-12-21
Perfect, thank you!

---

### Post by dented42 on 2007-02-21
i forgot to mention, the numberpad on my apple keyboard does not work, why?

also, how do I right-click with a one button mouse? in mac-os i press control, but that does not seem to work

---

### Post by dented42 on 2007-02-21
oh, and sometimes the examples and install icons load on my desktop, but sometimes they dont, how to I fix this, or where can i find these files elsewhere?

---

