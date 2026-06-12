---
title: "Help -- A fool rushed into xorg"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-03-22
I bought a new monitor, tried to get screen resolution to read 
1280x1024, followed some directions and added stuff

The short story is, I cannot boot.  I need to reinstall but there
are two Open Office  odt files I would like to save because these are my
wife's files, and I don't know how to do it.

By the way, I tried the dpkg-reconfigure  thing and it doesn't help

I am a mess.

Michael

---

### Post by Arby on 2007-03-22
OK first things first, keep calm. Everybody hoses a system sooner or later and it's always a bit scary if you're not used to it, lets see if it can be recovered. It probably can. It's seems odd that a broken xorg should prevent you from booting at all. Prevent you from getting a graphical desktop maybe but the system should still boot.

What do you actually see on screen when you try to boot the system? Is it literally a blank screen or do you get some text displayed? If you've got text post what it is showing you here. Especially if there are error messages of some kind. 

Something else to try would be booting in recovery mode. When you first boot, press 'esc' this should show you the grub menu with a set of options, one of them will be labelled 'recovery mode' (or possibly single user mode). Select that and try booting the machine. Tell us what happens, if you get messages from the system post them as well.

Regarding recovering your files, if we can't fix the primary problem then we can always boot from a liveCD, mount your filesystem, and get at your files that way.

Stick with it and we'll fix this.
Arby

---

### Post by sad_iq on 2007-03-22
However what do you mean by **sudo dpkg-reconfigure xserver-xorg** not working?
 What happened(errors or what)? 
If it really doesn't work try booting in recovery mode(press ESC when Grub starts)...that should get you to a root prompt then you could just copy the files (**cp /path/to/file/file.odt /path/to/put/file/file.odt**)

Darn...Arby beat me to it :)

---

### Post by Michl on 2007-03-22
I booted in recovery mode and reconfigured with dpkg-reconfigure, with
various options, but I would always get that basic rough screen
that says something is wrong with the xserver and would I like
to look at these files to diagnose what is wrong.

After hours of this, it occurred to me just to boot from a live cd,
set-up the network and printer and print those damn documents.
SO that's what I am doing now and reinstalling.

I guess for all bloody newbies like me,  be careful with xorg,

Michl

---

### Post by sad_iq on 2007-03-22
Before you reinstall why not just do a simple **sudo apt-get install --reinstall xserver-xorg  **...maybe that helps!!!

---

### Post by Arby on 2007-03-22
Yes Xorg can be a strange and wonderful beast and should only be approached with caution. However it is good to learn how to cope with it. Most people who attempt to edit xorg.conf break it sooner or later. I know I have. So my first rule of editing xorg.conf would be: ALWAYS ALWAYS back up your existing working xorg.conf file first. Then if it goes wrong you can easily get back to where you started.

---

### Post by Michl on 2007-03-22
> **Arby said:**
> Yes Xorg can be a strange and wonderful beast and should only be approached with caution. However it is good to learn how to cope with it. Most people who attempt to edit xorg.conf break it sooner or later. I know I have. So my first rule of editing xorg.conf would be: ALWAYS ALWAYS back up your existing working xorg.conf file first. Then if it goes wrong you can easily get back to where you started.

With emphasis on "ALWAYS ALWAYS" because you can get sloppy especially when it is after midnight.   The other rule I follow in woodworking but haven't (until now) transferred to computers: Don't rush into 'just one more thing' when you are tired.  And finally, don't try to improve your wife's computer when she likes it as it is.

I did two things.  
First, I just ran 
sudo dpkg-reconfigure xserver-xorg
thinking it was easy magic.  I don't know what I was doing except entering the defaults that I was given, although I couldn;t put a star in front of the resolution I wanted and so changed nothing there.  I worry that some of the defaults were not what I needed.

So then I decided to follow another suggestion i dug up, which is  "just add" the resolution I wanted to to Section "Screen" in /etc/X11/xorg.conf.  So for each Depth I added "1280x1024" that my wife's  Viewsonic 710b supports in W2k.  So to

Depth 1
Modes "1024x768" "800x600" "720x400" "640x480"
EndSubSection

I added in "1280x1024" like this

Depth 1
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection

For each depth up to 24.

Then I rebooted into chaos -- it was about 3am and I am a 54 year old idiot who hasn't pulled allnighters since graduate school.  So I went into recovery mode and edited the xorg conf file back to what it was, but that didn't help.

My hypothesis, for what it is worth, is that I made the mess when running dpkg-reconfigure xserver-xorg.  If that is so, then I don;t know what I should have backed-up first. 

I reinstalled everything.  The problem now is that Ubuntu starts with 1280x1024 in the login window, but there are distorting vertical line about an inch apart.  Once my wife logs in, though, it goes back to the lower one.  I wish I could get rid of that because it doesn't inspire confidence about Ubuntu in my wife.

Thanks for quick moral support!!  The livecd saved the files.

Michael

---

### Post by Arby on 2007-03-22
Hope you didn't think I was being sarcastic, I certainly didn't mean to be. I just recognise that sinking feeling when you reboot and things don't come back as expected.

Those mode lines you set look OK to me. I think you're probably right about having a problem with the 'dpkg-reconfigure xserver-xorg' command. Basically when you run this command it rewrites /etc/X11/xorg.conf. When you go through entering options you are essentially telling the X server what hardware you have and what parameters to use. the dpkg-reconfigure program then writes xorg.conf accordingly. The trouble with this is you need to know what the correct values to enter are. I'm not a huge fan of it since I generally don't know what the right values are. But it has it's uses.

The only thing you need to back up is /etc/X11/xorg.conf. Before messing around I usually run something like this at the commandline ```
sudo cp /etc/X11/xorg.conf /home/me/xorg.conf_backup
``` That will copy xorg.conf to your home directory. Then if you get in a knot you can just copy it back and restart X to get back were you were. Make sure you rename it to something other than xorg.conf. When the X server starts one of the places it looks for config files is your home directory. I've made that mistake and then wondered why the changes I was making in /etc/X11/xorg.conf weren't having any effect.

However that's enough pontificating. Back to the problem at hand. If your observing lines on the screen that's often caused by one of refresh rate, horizontal sync or vertical sync. We need to match up what your graphics card supports with what the monitor supports. What graphics card do you have? 

I'm at the limits of my understanding I'm afraid but if you post the contents of /etc/X11/xorg.conf here maybe someone with more clue can help

---

### Post by Michl on 2007-03-23
Here are the contents of xorg:

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
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"VE710b-2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"VE710b-2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

---

### Post by sad_iq on 2007-03-24
Ok...here goes:
 first take a look here... [http://www.viewsonic.com/support/desktopdisplays/lcddisplays/e2series/ve710b/#specs](http://www.viewsonic.com/support/desktopdisplays/lcddisplays/e2series/ve710b/#specs) make sure this is your monitor!!!!!...if not find the one that's yours !!!
 second...find a section that says "**VIDEO INPUT**" and take a note about "**fh:**"(horizontal frequency) and "**fv:**" (vertical frequency)
 third...**backup xorg.conf** as Arby sugested
 fourth...unfortunately...**sudo dpkg-reconfigure xserver-xorg**...and when it asks about the monitor select **Advanced** to manually enter the frequency !!!(first try to see if you can do it in Gnome and skip the reconfigure part...I have kde...and I can't change the frequency's or I don't know how :confused:  )

---

### Post by freebird54 on 2007-03-24
Carefully editing /etc/X11/xorg.conf to specify your frequencies does not require a dpkg-reconfigure... well usually :D

here is my Monitor section from xorg.conf - modify yours to match YOUR monitor should be enough.  
100
```
Section "Monitor"
        Identifier   "Samsung_900iFT"
        HorizSync    30.0 - 96.0
        VertRefresh  50.0 -160.0
        Option      "DPMS"
EndSection

```

That shows the format - now you just need the numbers - from your monitor spec sheet, or the web as available...

Good Luck!

---

### Post by Michl on 2007-03-24
That's the monitor and I see there's nothing about frequencies in the .xorg.

So would I change this in .xorg:
```
Section "Monitor"
          Identifier "VE710b-2"
          Option "DPMS"
EndSection
```
to this:

```
Section "Monitor"
        Identifier   "VE710b-2"
        HorizSync    30.0 - 80
        VertRefresh  50.0 -85
        Option      "DPMS"
EndSection
```


The values are just the ranges from the Viewsonic info on this monitor.

Can I do this by hand?  I think I would prefer to do that than use dpkg.

Michael

---

### Post by Arby on 2007-03-24
Yes you can edit xorg.conf by hand. The change you propose to make looks right to me. Here's one way to do it ```
sudo nano -w /etc/X11/xorg.conf
``` this willl open your xorg.conf using the nano text editor in write mode (that's the -w). As I said previously, backup xorg.conf before you start. 

Then just use the arrow keys to navigate through the file and make the changes you want to make. Press ctrl-X to save the changes and exit nano. If you restart that should implement your changes. If you have problems you can always replace the edited xorg.conf file with the backed up version to get back to where you are now

---

### Post by Michl on 2007-03-24
Well, I'm going to try this, but only when my wife leaves
for a conference next week for a couple of days just in
case I mess-up, get lost and have to reinstall again.
M

---

### Post by Michl on 2007-03-30
> **Michl said:**
> That's the monitor and I see there's nothing about frequencies in the .xorg.

So would I change this in .xorg:
```
Section "Monitor"
          Identifier "VE710b-2"
          Option "DPMS"
EndSection
```
to this:

```
Section "Monitor"
        Identifier   "VE710b-2"
        HorizSync    30.0-80
        VertRefresh  50.0-85
        Option      "DPMS"
EndSection
```



I edited the .xorg.config file as above, adding the HorizSync and VertRefresh lines. But I still get veritcal distortion lines about 2 inches apart at the login window and when screen resolution is set at 1280x1024, which is the optimal setting for this monitor.  The lines vanish at 1152x864.
Michl

---

### Post by cowlip on 2007-03-30
sudo dpkg-reconfigure -phigh xserver-xorg

will let you generate a default file, without any prompts.

---

### Post by GSF1200S on 2007-03-31
> **cowlip said:**
> sudo dpkg-reconfigure -phigh xserver-xorg

will let you generate a default file, without any prompts.

Yeah, I crashed my Xorg.conf file, causing Xwindow not to load. I didnt know what to do- one of the suggestions was this exact command, and it seems to have worked. I just put this in, selected my drivers and my resolution and it worked great.

Cowlip, I have a question then. I selected the medium option because I knew what the resolution was... Is that going to mess anything up? I didnt know about frequency, but if memory serves me correctly, windows said 1680x 1050 @ 60Hz, and I selected 1680x 1050 @75Hz (only option listed for this resolution). Is this too high a frequency for my monitor or what (laptop)? Haha, I thought I had it all straightened out until I read this thread.

But yeah, Mich, the above worked for me- you and I pretty much traveled the same route with the rest of what we tried. I would definitely try this and then reinstall if it doesnt fix things.  Good luck...

---

### Post by Michl on 2007-03-31
Well, I crashed this computer with
sudo dpkg-reconfigure xserver-xorg

After I crashed it, I searched frantically on my other
computer and did find this command:

sudo dpkg-reconfigure -phigh xserver-xorg

and ran it, but nothing changed. I just reinstalled and
don't want to reinstall again.  It's funny, you think
reinstalling with the new monitor should take care of
everything, after all it detected the right monitor, but stil
there's a little glitch. 

In any case, I'm aftaid of dpkg.

Michael

---

### Post by Michl on 2007-03-31
> **cowlip said:**
> sudo dpkg-reconfigure -phigh xserver-xorg

will let you generate a default file, without any prompts.

Ok, not wanting to be a wimp.  I just did this.

First, there are prompts... not many, but you still need to know what
your driver is and what resolutions are supported.  (I now realize what
my mistake first time around was.  I chose VESA, not realizing you can
scroll up or down to find other choices, like my i810.)

BUT more importantly and negatively, it reconfigured xorg.conf for a 
generic monitor with a refresh rate no better than 60.  Whereas before it 
was for my VE710 etc.  Moreover, the lines were sill there.

Fortunately, following Arby I save copies like crazy (and dpkg also makes a copy)
so I have the original xorg back.  My wife will be happy with 1024x768 with
the 85 refresh rate and that when rebooting she logs on to this odd screen
is (for her) just par for the course of all my pursuits of perfection that always come
with little quirks, errors.  Tube amps, linux ....  Fortunately she loves me...

Michl

---

### Post by Michl on 2007-03-31
I think I have a hypothesis:
The highest refresh rate I get for 1280x1024 is 75, but
for all the other resolutions, I have a choice of 85.  To get
rid of the distortion at 1280x1024 I would also need a rate
of 85.  (No distortion at 1152x864 at 85)

But I don;'t dare to change the refresh rate ranges published
on the VIewsonic site or?  There they have
fh 30~80
fv 50~85
and those are the values I now have in xorg.

---

### Post by freebird54 on 2007-04-01
I am sure that the values they give on your monitor are for a reason!  I have found that if the magic blue smoke ever escapes from an electronic item,  it never works the same again... :D

As for logging on to an 'odd' screen - There may well be a fix for that as well.  Exactly which screen are you referring to :

Grub screen:     choose OS to boot
Splash screen:  shows a progress bar
Login screen:    prompts for name/password

As all of these can have different settings/backgrounds etc

Maybe the system is TOO configurable?  nah....

---

### Post by Michl on 2007-04-02
> **freebird54 said:**
> I am sure that the values they give on your monitor are for a reason!  I have found that if the magic blue smoke ever escapes from an electronic item,  it never works the same again... :D

As for logging on to an 'odd' screen - There may well be a fix for that as well.  Exactly which screen are you referring to :

Grub screen:     choose OS to boot
Splash screen:  shows a progress bar
Login screen:    prompts for name/password

As all of these can have different settings/backgrounds etc

Maybe the system is TOO configurable?  nah....

That's why I'm sticking to the xorg that was defined when I reinstalled Feisty with this monitor.  The only thing I changed was adding the
frequencies as defined on the viewsonic site. 

It's the Login screen.  Basically, when it boots Feisty selects the  best resolution for this  monitor at login, but this resolution (1280x1024) at the refresh rate
avail;able at that resolution (75) has those distortions.  All lower resolutions are fine.  So it is acceptable, just not A+

---

### Post by freebird54 on 2007-04-02
There are a couple of things that can be done about a login screen.  The first one to try is to set the vga mode to an acceptable value in your bootup.  Here is a table of the values that can be put in:

```
Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?
```

and this is HOW they are put in

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backupyymmdd
gksudo gedit /boot/grub/menu.lst

```

the yy=year, mm=month, dd=day - just a suggestion for identifying your backup in case of difficulties!  Anyway look for a line like this bolded one:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,3)
**kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hde4 ro quiet splash **
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```
and turn it into this by adding '**vga=791**'

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,3)
**kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hde4 ro quiet splash *vga=791***
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

Don't change anything else for now - just save and reboot.  It *should* give you a better look on your login.  Try other values if you like - but 791 should help!

Good luck!

---

### Post by arbulus on 2007-04-03
I had a distortion problem on my login screen when I got a new monitor as well.  What I discovered was that X was trying to use a resolution that my monitor didn't like.  So I pulled out the manual for my monitor and found in it a list of all the resolutions that the monitor is capable of using (800X600, 1024x768, 1280x1020, etc). Then, I checked the xorg.conf file and looked at the resolutions listed there. There were about 3 resoltuions listed that my monitor couldn't use.  I changed the list to only show resolutions that were listed in the monitor's manual, and then when I restarted X, everything what just fine and the distortion was gone.

---

### Post by Michl on 2007-04-05
> **arbulus said:**
>  X was trying to use a resolution that my monitor didn't like.  So I pulled out the manual for my monito

Unfortunately, 1280x1024 is supposed to be optimal for this monitor, and x is trying to
run at 1280x1024, but that's where the distortion is at 75 refresh rate.  I wonder if at
85 it would still have the distortion.  But the manual states explicitly 30-80 for horizontal
frequency.

---

### Post by freebird54 on 2007-04-05
From what you posted earlier - 85 is the magic number for your monitor.  The Vertical REFRESH is the one that is selectable from the menus - as it is the one that often makes the difference in the resulting picture.

My monitors favourite setting is 1280 x 1024 @ 85 - and it is quite common for that to be so (though I COULD go 1600 x 1200 @ 70 if I wanted to).

If that is available to you - give it a try.  SHould clear up the problems with distortions, patterns running around etc etc..

---

### Post by Michl on 2007-04-06
Well, that seems interesting.  I do have in xorg the Vertical frequency set at 50-85, according to the Viewsonic specs, but in the screen resolution menu for 1280x1024 I only get 75 although in all the others I get a choice of 85.  I wonder how I could get 85 as a choice for that resolution?

Michl

---

### Post by freebird54 on 2007-04-06
I am not an EE, so I can't be sure - but it may well be out of reach if that is its behaviour.  My monitor claims max Refresh of 160 - but as resolution goes up, possible/recommended refresh rates go down.  Apparently I couldn't run 1600x1200 at more than 70 Mhz....

There MUST be more info out there on the web somewhere on how this really works.  I am only going with experience from the first NEC MultiSync through now - not with actual understanding/knowledge of the concepts involved.

Sorry - can't be more specific!

---

### Post by Michl on 2007-04-06
Thanks!!  Michael

---

