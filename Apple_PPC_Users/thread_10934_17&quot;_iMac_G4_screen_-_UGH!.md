---
title: "17&quot; iMac G4 screen - UGH!"
date: 2005-01-12
forum: Apple PPC Users
---

### Post by wabashprof on 2005-01-12
For the life of me I can't figure out how to get Ubuntu to use all of my 17" screen. I have a G4 iMac, and the best I can do is get an image that's too tall and not wide enough for my display. 

When I try to change things in the Screen Resolution section of System Configuration, there is no option for a 1440x900 screen...but that's what my iMac wants!

Anyone conquered this yet?

Thanks!

Michael

---

### Post by daniels on 2005-01-12
Remove the HorizSync and VertRefresh lines from /etc/X11/XF86Config-4.

---

### Post by chascon on 2005-01-13
[QUOTE=][/QUOTE] 

 you'll have to use xvidtune that comes default to configure to the odd wide screen the 17" is (run it from term [perhaps root, not sure]).  Tell us how it goes.  Give us the info xvidtune tells you as I'd be interested.

---

### Post by wabashprof on 2005-01-13
Thanks for the replies.

I tried removing the HorizSync and VertRefresh lines from /etc/X11/XF86Config-4, and that only resulted in a 640x480 resolution stretched to fit my display. It uses the whole screen, but it looks very bad...not what I'm looking for.

I also tried xvidtune, but changing values doesn't produce any effect on my screen. I tried a number of possibilities, but nothing produced any effect. When I choose "show" in xvidtune I get the following:

"1400x1050"   122.00   1400 1488 1640 1880   1050 1052 1064 1082 +hsync +vsync

All I want is a 1440x900 image. Is this possible?

Thanks again for all the advice. I'm devoted to Linux, but sometimes it can challenge one's patience! ;-)

Michael

---

### Post by Joeb on 2005-01-13
Try changing your XF86Config file to  this (backup your old one first, just in case).  Also, since it is a redhat config file, you should make sure any paths point to your Ubuntu locations.




# XFree86 4 configuration created by redhat-config-xfree86

Section "ServerLayout"
[INDENT]Identifier     "XFree86 Configured"
Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
[/INDENT]
EndSection

Section "Files"

# RgbPath is the location of the RGB database.  Note, this is the name 
of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (they are concatenated together)
# By default, Red Hat 6.0 and later now use a font server independent of
# the X server to render fonts.
	[INDENT]RgbPath      "/usr/X11R6/lib/X11/rgb"
	FontPath     "unix/:7100"[/INDENT]
EndSection

Section "Module"
	[INDENT]Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"
	Load  "glx"
	Load  "record"
	Load  "freetype"
	Load  "type1"
	#Load	"dri"[/INDENT]
EndSection

Section "InputDevice"

# Change "XkbModel" to "macintosh_old" if you are using
# the deprecated adb keycodes.
	[INDENT]Identifier  "Keyboard0"
	Driver      "keyboard"
	Option	    "XkbRules" "xfree86"
	Option	    "XkbModel" "macintosh"
	Option	    "XkbLayout" "us"[/INDENT]
EndSection

Section "InputDevice"
	[INDENT]Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"[/INDENT]
EndSection

Section "Monitor"

	[INDENT]#Option		"DPMS"
	Identifier   "Monitor0"
	ModelName    "Monitor Model"
	HorizSync    30.0 - 130.0
	VertRefresh  50.0 - 160.0
	Option	     "FlatPanel"[/INDENT]
EndSection

Section "Device"
	[INDENT]Identifier  "Card0"
	Driver      "nv"
	BoardName   "Unknown video card"
	Option	    "CrtcNumber" "0"[/INDENT]
EndSection

Section "Screen"
	[INDENT]Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth     16
	SubSection "Display"
		[INDENT]Depth     8
		Modes    "1440x900" 
[/INDENT]
	EndSubSection
	SubSection "Display"
		[INDENT]Depth     16
		Modes    "1440x900"
[/INDENT]
	EndSubSection
	SubSection "Display"
		[INDENT]Depth     24
		Modes    "1440x900"
[/INDENT]
	EndSubSection
[/INDENT]
EndSection

Section "DRI"
	[INDENT]Group        0
	Mode         0666
[/INDENT]
EndSection

---

### Post by chascon on 2005-01-14
Joeb: Where is this config file comming from?
Are you suggesting that you've run X succesfully from a iMac using Redhat?
I find this hard to believe.

I believe the question refers to refining X, the most the config could provide is the horizontal and vertical rates to get a basic X configuration and the user already has that considering that he's complaining that X over renders.

wabashprof: My brother has the same problem and this is why I'm interested to see how your problem is fixed.
I researching the problem for my brother I lerned that you can comprimise:

[http://knoppmythwiki.homelinux.org/index.php?page=HDTVSetupHowTo](http://knoppmythwiki.homelinux.org/index.php?page=HDTVSetupHowTo)

"4. Tune your settings. The biggest problem at this point is usually overscan. Too much of the screen may be clipped off left, right, top, or bottom. If you can tweak your modeline with xvidtune or Powerstrip, you should be able to adjust for overscan a bit.

[this is the bit that might prove useful:]

However, many people just run in a lower resolution within the appropriate timings. The Jarod Watson and htpcnews links found above discuss how to do this: it basically involves leaving the overall timings alone, and just reducing the pixels visible within that timing. For instance, where my 960x540p timing had too much vertical overscan, using the same timing with a 960x480 resolution worked perfectly."

We haven't tried this yet but I assume you want to stick to the figures apple has posted for the lcd screen you have.
[http://docs.info.apple.com/article.html?artnum=75310](http://docs.info.apple.com/article.html?artnum=75310)
only lists 1440x900 for the 17".
I know it can do much more settings at lower values too.  

I would just reboot to OS X, go to system preferences, and write down every set of resolutions.
Reboot into ubuntu-ppc, reinstate your original Xconfig-4 file (delete the redhat values).
Then try 1440x"the next lower value".
Reboot or kill X and then log in again but rebooting is more graceful for you system.

Update:
I'm assuming that you have the nvidia GeForce 4 MX video card because that is what my brother has in his 17" iMac.  Apple specs for this iMac follow:
Resolutions on Apple Studio Display 17 (LCD)
"640 by 480
800 by 600
1024 by 768
1280 by 1024" (from [http://docs.info.apple.com/article.html?artnum=88346](http://docs.info.apple.com/article.html?artnum=88346))
It doesn't list anthing higher for the 17" LCD
It doesn't seem to be up to date.  Go figure.  Apple keeping their specs hush again (but my brother and you are not running a studio).
-------
My brother's unbuntu installed fine but default is:
-ubuntu-ppc's moniter app says 1400x1050
-while Config-4 says, 1440x900

It still overscans the vertical so 1440x900 will not give you a wide screen res.  In fact I personally doubt that apple's 1440x900 gives a purist rendition (apple also says my ati Rage 128 runs at 24 default depth when it only runs accel at 16).
  
I think the app you're using to id the res is wrong while the Config file is right.  Else, if Config is was wrong you wouldn't get X up at all.  I have read about these sort of problems.
-------------------
These are the OS X system profile possible settings:
640x480
640x480 stretched 
800x500
800x600
800x600 stretched
1024x640
1024x768
1024x768 stretched
1152x720
1440x900


My guess is thart you are running 1440x900 despite what the gui app tells you.  Thus, your only problem is how to compensate for the overscan.
Maybe try replacing all:
1440x720
or
1152x900 
or something like that
experiment
in the config file.

Please report back results.

PS: change default depth to 16 from 32 as it will look better.  I haven't tried this with the above hack but only with the default ubuntu-ppc settings.  So maybe try this last.

Update:
The alterations do not have any visible effect and the moniter app still says that the screen is running at 1100x1050 not matter what resolutions I set in the config file (maybe the monitor app is correctly id'ing the res).
Your best bet is to use xvidtune and tune those modelines from the link below:
"Re: 17" iMac G4 screen - UGH!
finaly you might have to do some reading.
Read: [http://www.tldp.org/HOWTO/XFree86-V...OWTO/index.html](http://www.tldp.org/HOWTO/XFree86-V...OWTO/index.html)

specificaly
[http://www.tldp.org/HOWTO/XFree86-V...xes.html#AEN451](http://www.tldp.org/HOWTO/XFree86-V...xes.html#AEN451)

but the latter will not make sense without reading the entire thing. Therein is more than enough info you'll ever want to know."
 

Can anyone technically knowledgeable provide insight and a sure solution?  Why is Config file resolutions being bypassed?

Update:
I just tried xvidtune and I confirmed that it does not visibly change settings, although the numbers on xvidtune may change.  Any drastic changes were not allowed, understandable.
I hoped that I could fine tune my brother's modelines by first writting the modelines to Xconfig but xvidtune would not write modelines, either by way of "Fetch" and then "apply" or using auto" and then "apply".

Status:
Unable to adjust X to iMac 17" widescreen.  It seems that XConfig-4 id redundant as far as resolutions, and xvidtune is unable write modelines to term

---

### Post by chascon on 2005-01-14
finaly you might have to do some reading.
Read: [http://www.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/index.html](http://www.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/index.html)

specificaly
[http://www.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/fixes.html#AEN451](http://www.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/fixes.html#AEN451)

but the latter will not make sense without reading the entire thing.  Therein is more than enough info you'll ever want to know.

---

### Post by Wilito on 2005-01-14
I myself have the exact same problems regarding my 17" imac.  My screen resolution will not adjust as per chascon's suggestions.

Status:
Unable to adjust X to iMac 17" widescreen. It seems that XConfig-4 id redundant as far as resolutions, and xvidtune is unable write modelines to Config.

I did a search(Bugzilla.ubuntu.com), no results for this bug.  We need to report this bug to [https://Bugzilla.ubuntu.com](https://Bugzilla.ubuntu.com).  Power in numbers.

---

### Post by chascon on 2005-01-14
[QUOTE=][/QUOTE]
 Yes we need to report two bugs:
1) xnidtune doesn't write modelines to term
2) ubuntu-ppc does not config to wide 17" screen 

I'll make this short:
I found these modelines in relation to another bug but it presumably works on the 17" iMac (see bug link below):
Section "Monitor"
        Identifier      "Apple iMac 17 inch"
        HorizSync       20-61
        VertRefresh     60-75
        Option          "DPMS"
        Modeline        "1440x900" 108.84 1440 1472 1880 1912 900 918 927 946
# Generated with [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
        Modeline        "1024x768@75" 85.52 1024 1056 1376 1408 768 782 792 807
        Modeline        "800x600@75" 49.85 800 832 1016 1048 600 611 619 631
        Modeline         "720x450@75" 32.15 720 752 872 904 450 458 464 473
        Modeline        "640x480"   25.20  640 656 752 800  480 490 492 525
-hsync -vsync
        Modeline        "640x480@60" 24.11 640 672 760 792 480 490 495 505
        Modeline        "640x400@60" 19.67 640 672 744 776 400 408 412 421
        Modeline        "1024x640@75" 67.95 1024 1056 1312 1344 640 652 660 673
EndSection

Furthermore, I added a new line to the "Device" section:

        Option          "FPDither"      "1"

This improves the display quality of high-color data (like the Ubuntu
background image) significantly. See "man nv" for a description of
what it does.

... Thanks, I've integrated the modeline; however, I won't include FPDither per
default, because which chipsets it should be enabled on is a total mystery, like
the rest of the nVidia driver.  I'll bug upstream (i.e. nVidia, the only people
who know anything about that driver) to do it by default where default, but I
don't know how much luck I'll have.
[https://bugzilla.ubuntu.com/show_bug.cgi?id=3712](https://bugzilla.ubuntu.com/show_bug.cgi?id=3712)

As I, Chascon wrote earlier, changing depth to 16 solves issues such as the blured ubuntu desktop so "Option          "FPDither"      "1"" is not necessary.

---

### Post by Joeb on 2005-01-15
[QUOTE=chascon]Joeb: Where is this config file comming from?
Are you suggesting that you've run X succesfully from a iMac using Redhat?
I find this hard to believe.

[/QUOTE]

I got the config file from a friend who is running linux on his Mac.  I will ask what distro, although it is most certainly not Redhat (or Ubuntu :(  ).  However, that said, don't many distros use a generic Redhat config as a sample?  


Anyway, he said that's the config he uses.  I'll try and get more info.

Joeb

---

### Post by chascon on 2005-01-15
Can someone try the mode lines posted?
I'll don't have the iMac at hand to try it right now.

If it doesn't work, we know that xvidtune does not adjust the screen.  I thought that pressing "show" (make sure you do this) might at least print out in term a modeline, and that this could be hacked manually as in,
"15.4. The image is too wide (too narrow) horizontally
To fix this, increase (decrease) the horizontal frame length. That is, change the fourth number in the first timing section. To avoid moving the image, also move the sync pulse (second and third numbers) half as far, to keep it in the same relative position.
15.5. The image is too deep (too shallow) vertically
To fix this, increase (decrease) the vertical frame length. That is, change the fourth number in the second timing section. To avoid moving the image, also move the sync pulse (second and third numbers) half as far, to keep it in the same relative position.
Any distortion that can't be handled by combining these techniques is probably evidence of something more basically wrong, like a calculation mistake or a faster dot clock than the monitor can handle.
Finally, remember that increasing either frame length will decrease your refresh rate, and vice-versa.
Occasionally you can fix minor distortions by fiddling with the picture controls on your monitor. The disadvantage is that if you take your controls too far off the neutral (factory) setting to fix graphics-mode problems, you may end up with a wacky image in text mode. It's better to get your modeline right."
[http://www.linux.is/howto/howtoview.php?id=204#AEN396](http://www.linux.is/howto/howtoview.php?id=204#AEN396)

but it seems that lcd bypasses some config file settings.  See:
"One caveat: these procedures are useful for tweaking displays on traditional cathode ray tube (CRT) monitors. The newer liquid crystal display (LCD) monitors have fixed resolutions, and refresh rates don't have any visible effect either.
[but the saving grace should still be xvidtune:]
 Thus, tweaking the settings for LCD monitors is mostly pointless, with one small exception. If an analog LCD monitor consistently brings up your Linux display off-center or slightly too large or too small, you may be able to fix the problem using the xvidtune utility described toward the end of this column."
[http://www.linux-mag.com/2004-06/guru_01.html](http://www.linux-mag.com/2004-06/guru_01.html)

I also thought that xvidtune automatically wrote to XF86Config-4 but apparently it doesn't so just copy and append to monitor section (but before the line "EndSection" of monitor section).

Can someone verify all this by trying to create a modeline, and comparing that to the one from the bugzilla link.  And maybe trying them both?

PS: [http://www.linux.is/howto/howtoview.php?id=204#AEN396](http://www.linux.is/howto/howtoview.php?id=204#AEN396)
mentions that wide screen ratio settings can be created but apparently it is pointless according to [http://www.linux-mag.com/2004-06/guru_01.html](http://www.linux-mag.com/2004-06/guru_01.html)
, xvidtune excepted.  It's too techy too.

I'll try to get a hold of the iMac and report back results

Last note:
"If xvidtune doesn't seem to have any effect when you click Test, you may need to check your XF86Config file for a line that reads Option "DisableVidModeExtension" "yes" and change its value to "no". You'll then need to restart X again. Alternatively, you can enter your new mode into XF86Config "blind" and restart it to test."
[http://www.linux-mag.com/2004-06/guru_01.html](http://www.linux-mag.com/2004-06/guru_01.html)

The above link also describes how to create modelines at  [http://xtiming.sourceforge.net](http://xtiming.sourceforge.net)
That is how the sample modeline was created.

For info on xvidtune read:
[http://www.xfree86.org/3.3.6/QuickStart6.html](http://www.xfree86.org/3.3.6/QuickStart6.html)

---

### Post by chascon on 2005-02-22
After all that reading I find
[http://www.ubuntuforums.org/showthread.php?p=76276#post76276](http://www.ubuntuforums.org/showthread.php?p=76276#post76276)
It works perfect on my brother's iLamp.
Maybe he can post his XF86Config-4 file with the fine tunings .
Essentially throw this in minus the "&quote" and ";" stuff

Section &quot;Device&quot;
	Identifier	&quot;NVIDIA Corporation NV17 [GeForce4 440 Go]&quot;
	Driver		&quot;nv&quot;
	BusID		&quot;PCI:0:16:0&quot;
EndSection

Section &quot;Monitor&quot;
	Identifier	&quot;Generic Monitor&quot;
	HorizSync	28-70
	VertRefresh	43-72
	Option		&quot;DPMS&quot;
	Modeline &quot;1440x900&quot; 100.00 1440 1500 1508 1512 900 916 924 940 -hsync -vsync
EndSection

Section &quot;Screen&quot;
	Identifier	&quot;Default Screen&quot;
	Device		&quot;NVIDIA Corporation NV17 [GeForce4 440 Go]&quot;
	Monitor		&quot;Generic Monitor&quot;
	DefaultDepth	24
	SubSection &quot;Display&quot;
		Depth		24
		Modes		&quot;1440x900&quot;
	EndSubSection
EndSection

Section &quot;DRI&quot;
	Mode	0666

---

