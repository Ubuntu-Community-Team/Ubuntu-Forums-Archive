---
title: "Disappointed/frustrated"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Coelocanth on 2006-02-15
Is there any guide to Linux/Ubuntu commands (and what they actually mean) for the absolute - and mean *absolute* - beginner?

I've been reading these forums, looking at guides and tutorials, and doing as much research as I can over the last couple weeks and I'm still completely in the dark.

I managed to get Ubuntu Breezy installed on my computer and immediately ran into display problems. Got that solved to the point where I can at least access (and see) the desktop, but I'm unable to set my resolution to 1280x1024 (it's stuck at 1024x768 ). I've searched for how to update the nVidia drivers, but I honestly don't understand the directions I found.

I've had people advise me to do procedure X, and that's all well and good, but I don't generally learn things very well by being told to just *do* something; I need an explanation of *why* I'm doing it as well.

Now, I don't mind a steep learning curve, but running into a vertical wall is another thing altogether. I didn't think I was stupid, but I'm beginning to doubt my intelligence at this point and I'm almost ready to throw in the towel and just surrender to Bill Gates (much as I loathe that thought).

For an idea of some of the frustrations I'm experiencing, try [This Thread](http://www.ubuntuforums.org/showthread.php?t=131014). Much of what he's experiencing is similar. I'm getting nothing but warnings and errors whenever I try to do anything.

*sigh* Can anyone provide a little guidance, for starters, on how to get my video resolution up to my monitor's native res? It's a Samsung LCD 940B 19 inch monitor which supports a native res of 1280x1024. The graphics card is an eVGA GeForce 6800 GS PCIe.

Any links or suggestions on guides to commands would be highly appreciated as well.

Many thanks.

---

### Post by bluevoodoo1 on 2006-02-15
Here are a few command sites:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

there are lots more of course. You can searching these forums for them or google, you're bound to find lots of information.

---

### Post by Vengeful Cynic on 2006-02-15
Wow... that's a tall order.  I can't answer the whole thing, however I can give you the resource which you seek.

The command 'man' (short for manual) will give you resources on just about any command in the unix system.  All you have to do is (from terminal) type "man ls" if you want to learn more about the "ls" or "list" function.  Oh... and to quit out of man, type ':q'... I know that threw me for a loop the first time I used man.

Unfortunately, there's a relatively large gap between those who are new to using command-line and those who aren't... and those of us who aren't have a very hard time explaining everything that we're doing for those who are new to the whole command-line thing.  That said, if you want a blow-by-blow, most people who are posting solutions would be more than happy to answer that if you send them a PM and asked.  Oh.. and armed with your new-found information, you can do man-page look-ups on the commands that are being given to you and find out for yourself.

-Vengeful Cynic

---

### Post by bluevoodoo1 on 2006-02-15
[QUOTE=Vengeful Cynic]
The command 'man' (short for manual) will give you resources on just about any command in the unix system.  All you have to do is (from terminal) type "man ls" if you want to learn more about the "ls" or "list" function.  Oh... and to quit out of man, type ':q'... I know that threw me for a loop the first time I used man.[/QUOTE]

Oh yes, that reminds me... you can also use the --help command. Use it following a program like...

firefox --help
nautilus --help
xmms --help

and so on...

to learn about the different commands associated with each application.

---

### Post by Estariel on 2006-02-15
ok, I'll try to run you through it and explain everything :)

So, usually all configuration on linux is safed in text files.

This is also true for the Xserver configuration. The Xserver is the thing that is resposible for drawing stuff on the screen.

I'll tell you now how to open the Xserver's config file and edit the appropriate options. Note that this is not the only way of configuring the Xserver; there are tools that do it for you, but since you said you had basically tried everything, editing the file manually is a good way to fix it, and you will learn a lot.

Before we start, you will need to find some stuff.
You will need to know the horizontal Sync and vertical refresh rates of your monitor.
These are usually in the handbook of the monitor; if you don't have it, google them up.
These rates usually get detected by ubuntu automatically, but since you are stuck at a low resolution, the probably got detected wrongly.

Once you have found the values, continue below.


The file you will have to edit is called xorg.conf and is located in /etc/X11/, so it's entire path is /etc/X11/xorg.conf

Firstly, let's make a copy of the file (in case we mess things up)
type
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_sich

```
cp means copy, and its first argument is its source, and the second one its destination. sudo means "do the next thing on the command line with superuser rights".

Now open a terminal, and type in
sudo gedit /etc/X11/xorg.conf

gedit is a text editor, and with this command you are making it open the /etc/X11/xorg.conf file. 

Scroll down the text file.

find the monitor section. it should look like this (this is MY monitor section, so don't enter MY values...):
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

```
Enter YOUR HorizSync and VertRefresh rates.

When you got here, post a message, and post your entire /etc/X11/xorg.conf file.

I will continue then...

Estariel

---

### Post by aysiu on 2006-02-15
For a general super-beginner intro to Ubuntu (with explanations), go here:
[http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)

I wrote it with you in mind, specifically.

To fix your monitor problem. Do this:
1. Press control-alt-F1
2. Log in.
3. Type ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. If you don't know the answer, just go with the default. Be sure to mark 1280 x 1024 as one of the available resolutions, though.
4. When that's all finished, type ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```
5. Find the monitor section of the xorg file and make sure these two lines are in there (add them if they don't exist; modify them if they do): ```
HorizSync 30-81
VertRefresh 56-75
``` I'm basing those ranges on [this page from the Samsung website](http://www.samsung.com/uk/products/monitors/lcd/digital/ls19habtsqedc.asp?page=Specifications).
6. Save (control-x), confirm (y), and exit (Enter).
7. Type ```
sudo /etc/init.d/gdm restart
```

---

### Post by Coelocanth on 2006-02-15
First of all - thanks to all for the help. I really appreciate it.

Bluevoodoo: thanks for the links. I'll check them out.

Vengeful: thanks for your reply as well. Every little bit helps.

aysiu: Okay, I tried that and if I chose the nv option, I got garbled desktop. If I choose the vesa option, I get at least a desktop I can use. However, I'm still stuck at 1024x768 resolution and 76 Hz refresh rate. Can't raise or lower either one.

Estariel: that's *exactly* the kind of reply I like. I understand or had guessed at much of what you told me, but it's nice to have it laid out. I find for me it really helps to form a good visualization in my head (which leads to me understanding things much better) if I get a little explanation of what the commands are actually doing. Anyhow, as noted to aysiu, I'm still stuck in the same resolution. Here's the /etc/X11/xorg.conf file:

> 
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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV41 [GeForce 6800?]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Samsung 940B"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV41 [GeForce 6800?]"
	Monitor		"Samsung 940B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
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

I did not have to change any values, as the vert and hori were correct in the file.

Incidentally: I noticed when I booted up that I now have two options for booting into Ubuntu:

kernel 2.6.12.10 (386) as well as the recovery for that option

and

kernel 2.6.12.9 (386) as well as the recovery for that one.

My Windows XP is also available as an option. Any ideas why I have 2 bootable Linux kernels? I think maybe I've fubared this entire thing and may need to reinstall...

---

### Post by veritas366 on 2006-02-15
Coelocanth, glad you aren't extinct.

In any event, this is exactly the sort of "generation gap" that I hope ubuntu will learn to fill.  Old timers are so familiar with the terminal it is second nature but those of us brought up on Windows don't understand why on earth anyone would prefer a terminal (i.e. "booting into Dos") unless some serious hacking is going on, as gamers will do for example.  

If nothing else, when typing commands and file names, typos get introduced...or you use a capital when you shouldn't.  Nevermind learning the new commands.

I am fascinated that so many programs still get released with a separate "x" version with GUI.  I was confused about his with SANE...you  mean there are people who INTENTIONALLY want a nongraphical way to scan documents?  

Slowly I think that those who want Linux to break out mainstream are realizing that typing in commands by hand is simply not appealing except to the types who are already disposed to try Linux in the first place.  It should absolutely NOT have to be necessary for basic functions that an average user would want.

Setting resolutions is one of them and I ran into the same issue.  I assume that detecting h and v sync rates is tricky as I'm not the only one who's had this issue.  

I eventually got it working though I was real nervous as I kept reading warnings about blowing up my monitor if I got it wrong. I think the warnings turned out to be overblown, but it was intimidating.

---

### Post by aysiu on 2006-02-15
[QUOTE=Coelocanth]Here's the /etc/X11/xorg.conf file: ```
Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV41 [GeForce 6800?]"
Monitor "Samsung 940B"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
[b]Depth 24
Modes "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480"[/b]
EndSubSection
EndSection
```[/quote] I noticed you actually don't have 1280x1024 listed here. Maybe add that in and reboot (or restart the X server by hitting control-alt-backspace).

You may also, since you appear to be using an NVidia graphics card want to check out install the NVidia driver:
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

> 
Incidentally: I noticed when I booted up that I now have two options for booting into Ubuntu:

kernel 2.6.12.10 (386) as well as the recovery for that option

and

kernel 2.6.12.9 (386) as well as the recovery for that one. Yes 2.6.12-10 is the updated kernel. If that works for you, you can either remove the 2.6.12-9 one or uninstall it completely (search for the word *image* in Synaptic--you'll spot it pretty easily).

---

### Post by Estariel on 2006-02-15
hi again!

firstly, I see that you are not using the nvidia driver, so we will need to install it (in case you haven't already done that).

You can either start up synaptic, search for the package     nvidia-glx and install it, or you use the command line:

```

sudo apt-get install nvidia-glx

```

apt-get is aptitudes frontend for installing/removing packages, "install" is the option that triggers an installation, and nvidia-glx is the package we want to install.
if you want to search all available packages from the command line, you would use apt-cache (which is aptitudes frontend for searching).
For example "sudo apt-cache search nvidia" would list all entries which have something todo with the keyword nvidia.

Once you have the driver installed, we need to tell the xserver, that we want to use it.

find the section device (in the xorg.conf file)
mine looks like this:
```

Section "Device"
        Identifier      "NVIDIA Corporation NV40M? [GeForce Go 6200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "RenderAccel" "true"
        Option "AllowGLXWithComposite" "true"
EndSection

```
and change the driver to "nvidia" (the way i have it). Don't worry about my other options, for now you do not need them.

Now, as aysiu has pointed out, the xorg.conf file must have all resolutions that you want to be able to use listed.

in your screens section, get rid of all resolutions you do not want, and only keep those that you need (and add, what is missing).

e.g. one line reads:
```
Modes "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1024x768" "800x600" "640x480" 
```

I would probably change it to
```
Modes "1280x1024 "1024x768" "800x600" "640x480" 
```
(unless you know your monitor can handle higher resolutions, then also add the higher ones).
Again, do this for all these lines. Each one is for a different color depth, but who knows when you might want to use them.

Then save the file and restart the X server (log out of gnome, in GDM hit ctrl+alt+backspace)

If it does not work (or if it works ;)) please let me know.

Estariel

---

### Post by Coelocanth on 2006-02-15
Estaria:

Here's what I get when I try to install the nvidia drivers:

> 
Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

Any thoughts?

---

### Post by Coelocanth on 2006-02-15
aysiu:

When I start Synaptic, I get this message:

> 
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

The only entry I can see that has 'image' in it is imagmagick, and it does not have a green-filled square beside it.

Just want to thank you guys again for the guidance. :-D

---

### Post by aysiu on 2006-02-15
The local mirrors aren't that consistent.
Don't use ca.archive or us.archive or gb.archive or it.archive.
Use just archive.
See the first link of my signature for more details.

---

### Post by Coelocanth on 2006-02-15
Success!

aysiu, Estariel (I keep getting you name wrong - apologies): thanks so much for the help. I've got things up and running now with my monitor problems fixed. You're the best! \\:D/

Veritas: thanks - I'm not extinct yet (juat as my namesake - I'm still alive and well), and thanks to the help on this thread, I hope to avoid that fate!

---

