---
title: "Help:Screen resolution"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by rogue6 on 2005-10-01
Hi

        I am as green as it gets when it comes to Linux.I have been using Mac Os for around 7 years so i am somewhat computer literate.
Here's my problem i installed ubuntu on a G3iBook 700mhz all went well except my screen resolution it's at 640X480 so i found the screen resolution preference and 640x480 is my only choice.How can i fix this.


:confused:

---

### Post by Qrk on 2005-10-02
open a terminal and type

sudo dpkg-reconfigure xserver-xorg

It will ask you a series of questions about your monitor and hardware. Answer them as best you can

---

### Post by phen on 2005-10-02
also, try to search the forums, the wiki (wiki.ubuntu.com) and the net ([www.tuxmobile.org](www.tuxmobile.org)) for installation tips for you hardware. if there are any unanswered questions, just ask!

---

### Post by tseliot on 2005-10-02
How about this guide?

[http://ubuntuforums.org/showthread.php?t=21984&highlight=resolution]("http://ubuntuforums.org/showthread.php?t=21984&highlight=resolution")

---

### Post by rogue6 on 2005-10-02
Ok i did what Qrk said and restarted no it says xerver is configured incorrectly and will not start .Yeaaaaaaaaaaahhhhhhhh
So I am just goona reinstall and try the other posts.

    Thanx for the replys

---

### Post by tseliot on 2005-10-02
[QUOTE=rogue6]Ok i did what Qrk said and restarted no it says xerver is configured incorrectly and will not start .Yeaaaaaaaaaaahhhhhhhh
So I am just goona reinstall and try the other posts.

    Thanx for the replys[/QUOTE]
There's no need to reinstall.

Boot in recovery mode (you can choose it from GRUB)

and type:

sudo nano /etc/X11/xorg.conf

scroll the file down (you have to use your keyboard) until you find the line with section Device and make sure the word I put in red is &#8220;vesa&#8221;:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR="Red"]nv[/COLOR]"
BusID "PCI:1:0:0"


CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

Restart your computer

---

### Post by rogue6 on 2005-10-02
Ok


      I reinstalled Before i saw your reply so i'm up again i followed your link n instructions to open my xorg.conf file n found "Section Screen" 
Now 2 things (1)Depth 1-24 only has 1 mode "1024x768" (2)File is read only how do make it write.


        Thanx again for the Help

---

### Post by tseliot on 2005-10-02
[QUOTE=rogue6]Ok
I reinstalled Before i saw your reply so i'm up again i followed your link n instructions to open my xorg.conf file n found "Section Screen" 
Now 2 things (1)Depth 1-24 only has 1 mode "1024x768" (2)File is read only how do make it write.
Thanx again for the Help[/QUOTE]
1) you can add more modes manually according to the examples in the guide
2) Open Terminal or Konsole and type:

sudo gedit /etc/X11/xorg.conf (if you use GNOME)

or

sudo kate /etc/X11/xorg.conf (if you use KDE)

or

sudo nano /etc/X11/xorg.conf (if you don't use the graphical interface or you prefer nano)

it will ask you your password. Then you can modify your xorg.conf (and save)

---

### Post by rogue6 on 2005-10-02
I followed the instructions and rebooted and the same thing happened like before Xerver will not start 

so how do i boot into recovery mode

---

### Post by tseliot on 2005-10-02
Turn your computer on and when you see the word GRUB keep on pressing ESC until it gets you to the GRUB MENU. Then you can select Recovery mode (it won't start xorg and the graphical interface in this way).

---

### Post by rogue6 on 2005-10-02
ok i never see the word grub it goes through the boot process and then i get the error xerver is disabled  then i can log in without the ghraphical interface




I really appreciate the help Thanx

---

### Post by tseliot on 2005-10-02
Ok, turn on the computer and start pressing (tapping continously) the ESC button until you see the grub menu

---

### Post by rogue6 on 2005-10-02
ok i got into the config file and changed the nv to vesa and when i re booted i got the same blue screen with


I cannot start the X server.It is likeley that it is not set up Correctly would you like to view the Xserver output to diagnose the problem

---

### Post by tseliot on 2005-10-02
[QUOTE=rogue6]ok i got into the config file and changed the nv to vesa and when i re booted i got the same blue screen with
I cannot start the X server.It is likeley that it is not set up Correctly would you like to view the Xserver output to diagnose the problem[/QUOTE]
Can you post your /etc/X11/xorg.conf ? (copy and past the content here)

You can use a livecd to access the file

---

### Post by rogue6 on 2005-10-02
thats beyond me at the moment but post wich set of section you want to see  i will type em out

---

### Post by tseliot on 2005-10-02
Ok, I'll post my xorg and you can try to tell me how it is different from yours:
I'm using nvidia proprietary drivers now.


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"AL1715"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"AL1715"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by rogue6 on 2005-10-02
Ok your gonna laugh now i found the problem at the beggining of my screen resolutions there was no (")
640x480" "800x600" "1024x768


So i added the (")to the beginning and end of the resolutions and saved rebooted and got the same x server error so i opened my xorg.conf file again and to my stupidity it was blank i must have deleted the text somehow



So i'm reinstalling again this way i will also be able to post my xorg.conf file from the ibook  before i alter it again. I feel like such a Dork





Thanx again for your help i really appreciate It I will post my xorg.conf file as soon as the reinstall is done

---

### Post by tseliot on 2005-10-02
If you knew how many times I have screwed my system up you would be the one laughing now ;)

---

### Post by wishyjr on 2005-10-03
hiya, im trying to get more resloutions for my system. The Hardware can handle it (ive got a 6000GT and a spankin new Sony Monitor) but running through the sudo dpkg-reconfigure xserver xconf (or what ever its called on the last page of this thread) didnt really help, and to be honest i thought it was a bit long winded - didnt really want to go through my keyboard and mouse settings again. 

But after reading the last few posts i was wondering - can i add the resolutions into the xorg.conf file manually? similar to the post above? or will that just mess everything up? i have a backup of the file (which i did last night updating to the nvidia drivers with the help of tseliot's HOWTO -thanks) so i think i can replace the file if it all goes bad.

Also, running the dpkg-reconfigure command took the # away from the 'dri' line in the module section, am i ok to put it back? im still using the nvidia driver and everything sems fine.

thanks

---

### Post by tseliot on 2005-10-03
[QUOTE=wishyjr]But after reading the last few posts i was wondering - can i add the resolutions into the xorg.conf file manually? similar to the post above? or will that just mess everything up? i have a backup of the file (which i did last night updating to the nvidia drivers with the help of tseliot's HOWTO -thanks) so i think i can replace the file if it all goes bad.[/QUOTE]
It has never damaged my system. However if it doesn't work you won't see any new resolution in the screen resolution selector (and you should keep your current configuration). If you made a backup it's even better.

[QUOTE=wishyjr]Also, running the dpkg-reconfigure command took the # away from the 'dri' line in the module section, am i ok to put it back? im still using the nvidia driver and everything sems fine.
thanks[/QUOTE]
You can put it back manually

---

### Post by wishyjr on 2005-10-03
cool. well, you were right -it didnt crash but it didnt add any new resolution modes either :) bummer. So do i have to go through the dpkg-reconfigure thingy again then do do it properly? is there not a way to cut out all the other config questions (i.e. about the keyboard and mouse)?

---

### Post by tseliot on 2005-10-03
[QUOTE=wishyjr]cool. well, you were right -it didnt crash but it didnt add any new resolution modes either :) bummer. So do i have to go through the dpkg-reconfigure thingy again then do do it properly? is there not a way to cut out all the other config questions (i.e. about the keyboard and mouse)?[/QUOTE]
Usually the suggested answer is the right one (so just press ENTER if it is)

---

### Post by wishyjr on 2005-10-03
ok, i'll run through it again -just a quick one though, how do i actually enable antoher resolution when i get to the list? last time i pressed enter and it just went on to the next screen. Also, is there a way to back throught the config sequence?

thanks mate, you're sortin me right out! :)

---

### Post by tseliot on 2005-10-03
[QUOTE=wishyjr]ok, i'll run through it again -just a quick one though, how do i actually enable antoher resolution when i get to the list? last time i pressed enter and it just went on to the next screen. Also, is there a way to back throught the config sequence?
thanks mate, you're sortin me right out! :)[/QUOTE]
You have to press the spacebar if you want to select the resolution you want (I pressed enter the first time I tried it too ;) )

---

### Post by wishyjr on 2005-10-03
yeah, i noticed you were offline so i worked it out myself (not hard really is it!) thanks alot though -its all sorted and it looks mint!!

---

### Post by tseliot on 2005-10-03
I'm happy that you solved your problem in the end :)

---

### Post by rogue6 on 2005-10-03
Just wanted to say i'm back and my screen resolution is 1024x768
Woohooooooo:p 


Thanx again for the help

---

### Post by Animus on 2005-10-04
Is there anyway to get a screen resolution above 1024x768?  I was running Ubuntu from the Live CD, and ran sudo dpkg-reconfigure xserver xconf, and it properly detected my X800 XL, and I assigned my monitor as a generic monitor (Its a 17 inch dell CRT).  I properly marked my preferred resolutions to add, and finished the config, but when I went to change the resolution, non of the resolutions I'd checked were on the list.  I prefer to run 1280x1024, I find 1024x768 doesn't leave me enough room...

Maybe I should leave these questions until breezy comes out and I do a full install...

---

