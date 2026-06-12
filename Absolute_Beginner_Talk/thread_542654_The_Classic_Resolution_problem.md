---
title: "The Classic Resolution problem"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Carl_Barks on 2007-09-04
Hello everyone!

I am a new fellow ubuntu user.

Two days now, i've searched the whole ubuntu forums checking similar problems, and at first I was happy when I saw that many people had the same problem, hoping that I wiil eventually fix it.

But ...

Having tried EVERYTHING found here, editing the xorg.conf, even trying the solution listed here [http://ubuntuforums.org/showthread.php?t=527594](http://ubuntuforums.org/showthread.php?t=527594) (after the reboot it returns to 1024x768 ).

So, i have a 19'' LCD screen, my baby :P , and an old prehistoric ATI RADEON 9200 SE. I always used to work on 1280x1024 when I used Windows.
Here in Ubuntu the highest res i can choose is 1024x768. I have edited the xorg.conf and put "1280x1024" on the Screen section, i even put other things too in order to make it work but NOTHING can fix it!!!!

Please help me, cause it's unfair to have such a nice monitor that can show such a crystal view in 1280x1024 and being stuck to 1024x768  T_T

Here... this may help :

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option "BusType" "PCI"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"  "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"        "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection



*Thnx in advance :P

---

### Post by skymera on 2007-09-04
ok i never fiddle woth that..

i done this

sudo dpkg-reconfigure xserver-xorg

and chose my resoltuions, bing, it worked.

try it :D make sure you select thecorrect driver

---

### Post by Carl_Barks on 2007-09-04
> **skymera said:**
> ok i never fiddle woth that..

i done this

sudo dpkg-reconfigure xserver-xorg

and chose my resoltuions, bing, it worked.

try it :D make sure you select thecorrect driver


I have tried this too.
Also, how do I know which is the correct driver?
It is set in vesa right now.
After i hit ok it says to give an identifier for the card, i give ATI Technologies Inc RV280 [Radeon 9200]
and then i have a new screen where i have no choice, i just can read sth and it says OK but I can do nothing there

---

### Post by LongJuanFeng on 2007-09-04
urh, I chose this method too, but the thing is I can't save the file due to restrictions of file writing and I tried the sudo -p command to change the password so I can use it but once again, it won't let me and I'm trying to change my resolution current and I do know the specs for it. Please assist me if you can too, it'd be much appreciated. :)

---

### Post by skymera on 2007-09-04
whats your graphics card?

---

### Post by Carl_Barks on 2007-09-04
I mention it above. 
It's an ATI RADEON 9200 SE

---

### Post by LongJuanFeng on 2007-09-04
if you're talking to me instead, I'm using nvidia geforce4 mx

---

### Post by Carl_Barks on 2007-09-04
[https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI)

Here it says about fixing a bug on Radeon9200. 
The only problem i have is when having to take the step :
"This downloads three files and unpacks the sources into the directory xserver-xorg-driver-ati-version. In this directory is the file src/radeon_bios.c, that we need to edit."
Can you please help me how i will find and edit this file? Thnx.

---

### Post by rustybronco on 2007-09-04
try this,  this is what I do to change resolutions

sudo dpkg-reconfigure xserver-xorg   select ati instead of vesa

log in 

sudo gtf 1280 1024 60

and put the results at the end of the monitor section of your /ect/X11/xorg.conf

restart x... ctrl+alt+backspace

log in

go to screen resolution find your new resolution, select it...

see this thread  [http://ubuntuforums.org/showthread.php?t=370204&highlight=SUDO+GTF](http://ubuntuforums.org/showthread.php?t=370204&highlight=SUDO+GTF) it may help

or search sudo+gtf

---

### Post by Carl_Barks on 2007-09-04
> **rustybronco said:**
> try this,  this is what I do to change resolutions

sudo dpkg-reconfigure xserver-xorg   select ati instead of vesa

log in 

sudo gtf 1280 1024 60

and put the results at the end of the monitor section of your /ect/X11/xorg.conf

restart x... ctrl+alt+backspace

log in

go to screen resolution find your new resolution, select it...

see this thread  [http://ubuntuforums.org/showthread.php?t=370204&highlight=SUDO+GTF](http://ubuntuforums.org/showthread.php?t=370204&highlight=SUDO+GTF) it may help

I get this : 

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync


which part of it i have to add to the Monitor section? All of it as it is ? (copy-paste?)

---

### Post by rustybronco on 2007-09-04
Yes.

---

### Post by Carl_Barks on 2007-09-04
i did it and yet nothing happens. now i am trying sth else. from here [http://ubuntuforums.org/showthread.php?t=370204&highlight=SUDO+GTF&page=2](http://ubuntuforums.org/showthread.php?t=370204&highlight=SUDO+GTF&page=2)

when i type sudo dpkg-reconfigure -phigh xserver-xorg

and when i hit 1280x1024 with "enter" i get this message 

stefanos@ZANGETSU:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070904153922

---

### Post by emjotsh on 2007-09-04
I got the same problem recently.
My video card is a RADEON X1300 and my montor is a 19" monitor Philips 190V.

Result of autodetection was:
       hsync:				 28.00 - 49.00 kHz
       vrefresh:			43.00 - 72.00 Hz
       screen-dimension:      380x300
       DPI to				(68,65).

In the internet I found also following dates for this monitor:
         hsync:				30.00 - 83.00 kHz
	vrefresh:			56.00 - 76.00 Hz
	screen-dimension:	380x300
	DPI to				(85,86).

Therefore I deleted the hsync and vrefresh lines in the xorg.conf. I think for Ubuntu were the ranges of this frequencies too small for a resolution of 1280x1024.
Warning: Wrong hsync and vrefresh lines can damage the monitor! Please, first consider the technical dates in the monitor manual.

This is a detail from my xorg.conf:
[FONT="Courier New"]Section "Device"
	Identifier	"ATI RADEON X1300"
	Driver		"vesa"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Philips 190V"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X1300"
	Monitor		"Philips 190V"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection[/FONT]

---

### Post by rustybronco on 2007-09-04
make sure you have 1280x1024 listed in the screen section of xorg.conf
Another thing you may try is select ALSO a higher resolution  in dpkg-reconfigure... plus 1280x1024  then after restarting, select your 1280x1024 in screen resolutions. 

the mode line has worked for me with a radeon 7000 ve and a nvidia geforce fx5900

---

### Post by bearyblue on 2007-09-04
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV280 [Radeon 9200]"
Monitor "Generic Monitor"[B]
DefaultDepth 24[/B]

change to:

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV280 [Radeon 9200]"
Monitor "Generic Monitor"
**DefaultColorDepth 24**

That's what is in my xorg.conf. Just try it. BTW, don't forget to make backups of the original xorg.conf.

---

### Post by Carl_Barks on 2007-09-04
Nothing .... nothing ... nothing ....

It seems I am cursed to be stuck at 1024x768 

Just a question, pleeeaaaaaaase answer.

When i type sudo dpkg-reconfigure -phigh xserver-xorg

and hit "enter" in the selected resolution I get this message on my terminal 

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070904164157


How do I solve this so that I can choose the resolution through dpkg ? (not that it's going to work but, i am willing to give it a try)

---

### Post by LongJuanFeng on 2007-09-04
having the same problem still and view all the help files. and also, I opened up the xorg.conf file and added the mods and when I try to save, it wont let me even though I already executed this command in terminal $sudo passwd root. some one please help.

---

### Post by rustybronco on 2007-09-04
> **Carl_Barks said:**
> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070904164157
Warning overwriting POSSIBLY-customised...  I see the message all the time.

---

### Post by rustybronco on 2007-09-04
> **LongJuanFeng said:**
> having the same problem still and view all the help files. and also, I opened up the xorg.conf file and added the mods and when I try to save, it wont let me even though I already executed this command in terminal $sudo passwd root. some one please help. sudo gedit, enter password, then go to ect>X11>xorg.conf, edit as necessary save and close.

---

### Post by bearyblue on 2007-09-04
It just says that it will overwrite your current xorg.conf after backing it up to /etc/X11/xorg.conf.20070904164157.

---

### Post by LongJuanFeng on 2007-09-04
> **rustybronco said:**
> sudo gedit, enter password, then go to ect>X11>xorg.conf, edit as necessary save and close.

do I restart after I save?  umm..soo update, I restarted and it gave me a deathly error message. I popped in the ubuntu disc and restarted in safe graphics mode (which ironically has a better resolution of 1020, though my original settings on xp was 1210.) Any guidance on what I should do? Thanks.

---

### Post by rustybronco on 2007-09-04
Yes restart x, ctrl+alt+backspace, login.

---

### Post by rustybronco on 2007-09-04
> **LongJuanFeng said:**
> I restarted and it gave me a deathly error message. I popped in the ubuntu disc and restarted in safe graphics mode (which ironically has a better resolution of 1020, though my original settings on xp was 1210.) Any guidance on what I should do? Thanks.
deathly error message, what was that?

---

### Post by LongJuanFeng on 2007-09-04
umm. a blue screen telling me something along the lines of not being able to find screen resolution and some error message that I had to login. Damn, I should have written down the details. should I restart without the disc again and write it down?

---

### Post by rustybronco on 2007-09-04
when you get to the login screen.
login...
password...
sudo dpkg-reconfigure xserver-xorg 
you will be given choices, about keyboard ect. THINK while entering them, select your video card and resolutions (select them with the space bar) and restart.

I'm learning also, be kind!

---

### Post by LongJuanFeng on 2007-09-04
> **rustybronco said:**
> when you get to the login screen.
login...
password...
sudo dpkg-reconfigure xserver-xorg 
you will be given choices, about keyboard ect. THINK while entering them, select your video card and resolutions (select them with the space bar) and restart.

I'm learning also, be kind!

what is nvidia listed under? I'm asked to select my x server driver. (graphical interface)

btw, will this still help if I"m functioning under safe graphics mode on the disc?

and I'm trying to upload some pictures I took of the error screens and crap. and I'm trying to get back all my book marks and files before this error occurred with the restarting which is currently on the normal OS ubuntu that isn't functioning.

---

### Post by rustybronco on 2007-09-04
> **LongJuanFeng said:**
> what is nvidia listed under?  NV...

---

### Post by LongJuanFeng on 2007-09-04
how do I figure out the pci/vidcards bus identifier?

---

### Post by rustybronco on 2007-09-04
If you don't know the answer use the defaults. 0.0.0? I think is the default.

---

### Post by LongJuanFeng on 2007-09-04
okay, it's telling me incorrect format dude.

---

### Post by bearyblue on 2007-09-04
> **LongJuanFeng said:**
> how do I figure out the pci/vidcards bus identifier?

Use the command "lspci" for that. But I'm really not familiar with that. I didn't have to edit that line in xorg.conf.

---

### Post by LongJuanFeng on 2007-09-04
it lists 2 pci "bridges"

and here's what they all look like. 


00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:08.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

### Post by rustybronco on 2007-09-04
pci bus identifier "whatever it lists" "yes"

---

### Post by rustybronco on 2007-09-04
To the OP, positive results yet?

---

### Post by Carl_Barks on 2007-09-04
my problem is solved. 
I solved through sudo dpkg-reconfigure -phigh xserver-xorg
The thing i did wrong all this time was ... I WASN'T PRESSING SPACE BAR BUT ENTER!!!

thnx a bunch to the holy man that mentioned that we make the choices with the space bar!

---

### Post by rustybronco on 2007-09-04
You know your on you way to linux addiction, when your wife asks what are you doing now?  and the answer is... " I'm going to see if I can crash X again" just for the sake of fixing it.

ubuntu user since 2007-10-06 and never looked back.

---

### Post by Carl_Barks on 2007-09-04
I am just curious if there is actually a bug or not. I haven't installed Beryl yet so i can't be sure if everything is fine with my card. So I want help with this :

[https://help.ubuntu.com/community/Ra...280%29_and_DVI](https://help.ubuntu.com/community/Ra...280%29_and_DVI)

Here it says about fixing a bug on Radeon9200.
The only problem i have is when having to take the step :
"This downloads three files and unpacks the sources into the directory xserver-xorg-driver-ati-version. In this directory is the file src/radeon_bios.c, that we need to edit."
Can you please help me how i will find and edit this file? Thnx.

---

### Post by rustybronco on 2007-09-04
I suspect sudo gedit, password, then path/to/file   (xserver-xorg-driver-ati-version) will get you there though I've never tried it, what's the worst you can do? learn?

---

### Post by rustybronco on 2007-09-04
reading material...
[http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml](http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml)

---

