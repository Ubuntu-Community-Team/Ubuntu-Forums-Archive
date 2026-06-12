---
title: "Beautiful Desktops"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2006-09-26
I'm not that far into my linux books yet =X And through some theme searching I found a bunch of very cool themes.  The only problem is I am still getting familiar with terminal commands and if possible any nooby installations would be best until I could get more reading done.

Is there any program for linux that is easy to install and allows for great desktop presentation and customization like some of the great layouts I have seen on the ubuntu gallery?

And one last question, why can't I set my resolution higher in Ubuntu?  I am currently on a windows system so I can't check off hand but as I recall my only resolution options were 800x600 and 1024x768.

---

### Post by bodhi.zazen on 2006-09-26
Depends on what you want. KDE, Gnome, XFCE, Fluxbox, Openbox, IceWM, Enlightenment all have fairly unique look and feel.

Eyecandy varies from icons to elaborate monitors of you box.

And then there are backgrounds.

I suggest you look at KDE, Gnome, XFCE, and Fluxbox.

Then look at rox, it is fairly easy to integrate and start adding to the desktop, drag and drop technology in fact.

Then look here:

[Eyecandy](http://ubuntuforums.org/showthread.php?t=77694)

As far as your resolution, start with this:
Open a terminal, enter the following command:
```
sudo dpkg -reconfigure -phigh xserver-xorg
```

If you still have resolution problems, videocard? Monitor??

---

### Post by Perfect Storm on 2006-09-26
Might check this for eyecandy: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694) 
Sorry that there aren't any pictures, the place that host my pictures is down at the moment.



Monitor problem:
Find you monitor manual, look for 
Horizontal scan range 
Vertical scan range  

When found open the terminal and write:
```
sudo nano etc/X11/xorg.conf
```
find the Section "Monitor"
and add the write number from the manual to here:
HorizSync 
VertRefresh

save and exit <ctrl> + <o> | <ctrl> + <x>
restart X (Ctrl-Alt-Backspace)



eg. mine looks like this for Dell p992:
HorizSync 30 - 107
VertRefresh 48 - 170

---

### Post by The Tronyx on 2006-09-26
Horizontal Freq. (kHz)30 - 58kHz
Vertical Freq. (Hz)50 - 160Hz 

Is that what I'm looking for?

---

### Post by Perfect Storm on 2006-09-26
aye. Then put these numbers into 

HorizSync
VertRefresh

so it says

HorizSync 30 - 58
VertRefresh 50 - 160

if HorizSync and VertRefresh isn't displayed under monitor section in your xorg.conf you can just add them, eg: Here's mine:
```
Section "Monitor"
Identifier "Generic Monitor"
HorizSync 30 - 107
VertRefresh 48 - 170
Option "DPMS"
EndSection
```

---

### Post by bodhi.zazen on 2006-09-26
He is talking about entering the information manually. You need to know these numbers. google search you monitor to find them.

This is the second step of what I was thinking, I would start with:

sudo dpkg -reconfigure -phigh xserver-xorg

first. If it works it will be easier.

---

### Post by The Tronyx on 2006-09-26
Thanks a lot!  If I didn't have class in 5 hours I would start playing around right now, maybe after. =p

One last note, I looked up my monitor and the numbers I entered were for a different model, the specs for mine are 
30-70 kHz (horizontal)
50-160 Hz (vertical)

Does that affect anything?

---

### Post by coolbian57 on 2006-09-26
My cousin uses Blackbox and loves it. ( but if I were you i wouldn't take my advice.  :-X )

---

### Post by Perfect Storm on 2006-09-26
It's best if you use the exact number that is shown in your monitor manual, because if it's wrong you could damage your monitor.

---

### Post by The Tronyx on 2006-09-26
When I enter 

sudo dpkg -reconfigure -phigh xserver-xorg

I am presented with...

brooks@brooks-desktop:~$ sudo dpkg -reconfigure -phigh xserver-xorg
dpkg: conflicting actions --control and --remove

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
brooks@brooks-desktop:~$


I'm not quite sure where to go from there.

Just prior to that I ran the command sudo apt-get install xorg-driver-fglrx without any problems.  Any connection?  I feel like a complete idiot, I don't even know if my graphics card is installed correctly, when it was installed on Windows, I had lots of resolution options.

And when I use the sudo nano etc/X11/xorg.conf line, I am presented with

  GNU nano 1.3.10           File: etc/X11/xorg.conf                   Modified




















                                  [ New File ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell


P.S.  Sorry for this wall of text, I'm working on figuring out how to implement scroll on forums. >.>

---

### Post by xhaan on 2006-09-26
> **2point0 said:**
> When I enter 

sudo dpkg -reconfigure -phigh xserver-xorg

I am presented with...

brooks@brooks-desktop:~$ sudo dpkg -reconfigure -phigh xserver-xorg
dpkg: conflicting actions --control and --remove

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
brooks@brooks-desktop:~$


I'm not quite sure where to go from there.

Just prior to that I ran the command sudo apt-get install xorg-driver-fglrx without any problems.  Any connection?  I feel like a complete idiot, I don't even know if my graphics card is installed correctly, when it was installed on Windows, I had lots of resolution options.


there should be no space between dpkg and -reconfigure
do:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by The Tronyx on 2006-09-26
OK I ran it without the space and the configurer(er)(is that a word?) opened just fine selected , I then selected the resolutions I wanted to support and selected ok.  After that I get

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20060927033924
brooks@brooks-desktop:~$


I then go to system>preferences>screen resolution, but I don't see any new options.  I went back into the config menu and none of the ones I opted to support, remained selected.

---

### Post by Perfect Storm on 2006-09-26
You have to restart X: ctrl+alt+backspace

---

### Post by Anonii on 2006-09-26
> **Artificial Intelligence said:**
> Might check this for eyecandy: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694) 
Sorry that there aren't any pictures, the place that host my pictures is down at the moment.



Monitor problem:
Find you monitor manual, look for 
Horizontal scan range 
Vertical scan range  

When found open the terminal and write:
```
sudo nano etc/X11/xorg.conf
```
find the Section "Monitor"
and add the write number from the manual to here:
HorizSync 
VertRefresh

save and exit <ctrl> + <o> | <ctrl> + <x>
restart X (Ctrl-Alt-Backspace)



eg. mine looks like this for Dell p992:
HorizSync 30 - 107
VertRefresh 48 - 170
My monitor is 8years old, and I've lost the manual, is it possible to find the rates in the internet, or on the the monitor or something? :/

---

### Post by Perfect Storm on 2006-09-26
It should be possible, a google should do it.

---

### Post by The Tronyx on 2006-09-26
Ok, something got messed up, after ctrl-alt-backspace, I go back to my Ubuntu login screen, which is in higher resolution, and I enter my login and password.  After that, my screen clicks, but kicks me to command only.  Again it asks for my login and pass, I enter it, and back to the ubuntu GUI log in, this goes back and forth, not every time verbatim, but the same routine.  Eventually I find myself at the command screen only viewing 

brooks@brooks-desktop:~$ 

and a blinking cursor, I don't know what I did or how to get back to my desktop.

Would it have anything to do with my other thread

[http://www.ubuntuforums.org/showthread.php?t=265483](http://www.ubuntuforums.org/showthread.php?t=265483)

---

### Post by xhaan on 2006-09-26
> **2point0 said:**
> Ok, something got messed up, after ctrl-alt-backspace, I go back to my Ubuntu login screen, which is in higher resolution, and I enter my login and password.  After that, my screen clicks, but kicks me to command only.  Again it asks for my login and pass, I enter it, and back to the ubuntu GUI log in, this goes back and forth, not every time verbatim, but the same routine.  Eventually I find myself at the command screen only viewing 

brooks@brooks-desktop:~$ 

and a blinking cursor, I don't know what I did or how to get back to my desktop.

Ok, it seems the xorg.conf got messed up by dpkg-reconfigure
When you get that command prompt again, do this
```
sudo killall gdm
```
then do
```
sudo cp /etc/X11/xorg.conf.20060927033924 /etc/X11/xorg.conf
```
and then
```
sudo gdm
```
to get back where you were before.

You could then try to edit your xorg.conf manually if you don't want to try dpkg-reconfigure over again.

---

### Post by xpod on 2006-09-26
Seems i`ve landed myself in the same boat.Had all my refresh rates done fine on my last install but it`s all went pearshaped this time.Glx gears used to whizz round now it dont:rolleyes: 

I got all my monitor details of google again and done the job of entering the refresh rates and i rebooted and all seemed fine till i went to look at the xorg.conf.....If i open it either with nano or gedit i get shown a blank page

I can go look at the file via a file browser and i even ended up restoring the backup....or so i thought.

Sorry to impose but ive been following this to try right myself....
Just making it worse i fear.:-?

---

### Post by Perfect Storm on 2006-09-26
Are you sure you spell it correctly? Like big X in X11 etc. The case sensitive.

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by xpod on 2006-09-26
I copied the commands  so i would`nt have typed nothing wrong.
I started out elsewhere though so not even sure where i started out now:rolleyes: .

I have a few backups now it seems and i used another which seems to have done the trick but....i dont know why but the glxgears seem to have speeded up which i take as an indication that "something"was done????..It must have been as my keyboard seems had changed to the USA layout....lol

Only have onboard graphics so i was`nt trying to push the realms of possibility but i just wanted to get what i know the thing to be capable of.
I had higher than 1024x728 on that "other" thing so was trying to put the higher res in the xorg.conf when i come across the "vert/horz" stuff and put that in too.....seems i got the refresh rates but not the res....lol

I`ll get there in the end....

---

### Post by bodhi.zazen on 2006-09-26
> **xhaan said:**
> 
When you get that command prompt again, do this
```
sudo killall gdm
sudo cp /etc/X11/xorg.conf.20060927033924 /etc/X11/xorg.conf
sudo gdm
```

Nice post.

_2point0_: This will restore your xorg.conf.

The only thing I would add is:```
cp /etc/X11.xorg.conf /etc/X11/xorg.conf.bak
```

It is a good idea to ALWAYS back up your working copy of xorg.conf b4 you start and after u finish configuration of any new upgrade.

Post your xorg.conf and lets take a look. After all we have the attention of a few experts and at least 1 pseudoexpert. :)

---

### Post by xpod on 2006-09-26
Soon be "sudo".....:-k

---

### Post by xhaan on 2006-09-26
> After all we have the attention of a few experts and at least 1 pseudoexpert.

I'm the pseudoexpert! :oops: 
*hides*

---

### Post by bodhi.zazen on 2006-09-26
=; Now now, you will all have to take turns playing pseudoexpert. :p

---

### Post by BackInTimeMan on 2006-09-26
> **Anonii said:**
> My monitor is 8years old, and I've lost the manual, is it possible to find the rates in the internet, or on the the monitor or something? :/

I found my old Compaq monitor specs here:

[www.monitorworld.com](www.monitorworld.com)

---

### Post by The Tronyx on 2006-09-26
Eh I have no clue, even on my monitor settings it says it supports 1280x1024@60hz, but everytime I try and set it I have to restore my old xorg.conf file because of the log in kick loop I described before.  Anyone else have ideas?

---

### Post by bodhi.zazen on 2006-09-26
Monitor?

---

### Post by The Tronyx on 2006-09-26
[http://www.computingondemand.com/reviews/monitors-KDSxf-70/KDSxf-70.shtml](http://www.computingondemand.com/reviews/monitors-KDSxf-70/KDSxf-70.shtml)

---

### Post by bodhi.zazen on 2006-09-26
Try this:

Note: Restart X = Ctrl-Alt-Backspace

Add (or modify) these lines to Section "Monitor":
```
	VendorName	"KDS"
	ModelName	"KDS XF-70"
	HorizSync	30-70
	VertRefresh	50-160
```

And re-try (restart X).

If that fails, in the Section "Screen" reduce you color depth:
```
   DefaultDepth 16

.....

    Subsection "Display"
        Depth       16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
```
Make sure the Modes lists your desired resolution.


And re-try (restart X).

If that fails, post your xorg.conf.

---

### Post by The Tronyx on 2006-09-27
Ok, trying now, but I believe I selected 1280x1024, let me give it a shot, and if that fails, i'll post xorg.conf

BTW, to save me another post, and you another view of this thread, how can I open the xorg.conf file to show it here.

---

### Post by bodhi.zazen on 2006-09-27
> **2point0 said:**
> Ok, trying now, but I believe I selected 1280x1024, let me give it a shot, and if that fails, i'll post xorg.conf

BTW, to save me another post, and you another view of this thread, how can I open the xorg.conf file to show it here.

The location, as you know, is /etc/X11/xorg.conf

You can either ```
gedit /etc/X11/xorg.conf
```
Cut-n-Paste

Or

Look down as you post, down, see "Manage Attachments"
Click on "Manage Attachments" and send xorg.conf as an attachment.

This is my preferred method...

---

### Post by The Tronyx on 2006-09-27
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

BTW, from any of that can you tell if my video card is correctly installed?

---

### Post by bodhi.zazen on 2006-09-27
Assuming you changed the Monitor sectin to this:
> Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync	30-70
VertRefresh	50-160
EndSection

and failed....

Try these likns:

[[color=blue]ATI[/color]](http://ubuntuforums.org/showpost.php?p=423584)

[[color=blue]How to install ATI drivers[/color]](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

