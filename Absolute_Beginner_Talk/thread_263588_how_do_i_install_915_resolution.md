---
title: "how do i install 915 resolution?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by andrewface on 2006-09-23
and is that the only thing i need to get the widescreen going?

---

### Post by davmac on 2006-09-23
It is only of use if you've got either 800 or 900 series Intel graphics chipsets. To install it, start synaptic (System/Administration/Synaptic Package Manager). Right near the top you'll see 915resolution. Select it and then click "Apply".

Once it is installed you need to configure it. Open a terminal window and type "sudo gedit /etc/default/915resolution". You then need to complete the relevant details for XRES and YRES. Save it and restart your system and you should be away.

Dave Mac

---

### Post by Krisz on 2006-10-29
Now the only problem with that is that i can now overwrite the 915resolution file because it is read only, and i don't have access to it. I can not move it delete it or otherwise.](*,) 

It is getting extremely annoying that a simple resolution change takes so much effort and pain to do.

---

### Post by Krisz on 2006-10-29
Not to mention that the max resolution right now my screen is at is 640x480 so even the Ubuntu installation i could not see any of the buttons where i was supposed to click. Right now most of the windows that pops up during the setup i can not see the bottom of them because of the screen resolution.
:confused:

---

### Post by davmac on 2006-10-30
Krisz,

Not sure I understand your problem. Can you describe it in a bit more detail. When you say "i can now overwrite the 915resolution file because it is read only, and i don't have access to it. I can not move it delete it or otherwise", should that be "I cannot..."?

You can get round the 640x480 limitation if you're happy to work from the command line. Press ctrl-alt-f6 to switch to a console, login, do what you need to do (in console I use nano as an editor rather than gedit). Logout and then press ctrl-alt-f7 to get back to your normal session.

Hope this helps,

Dave Mac

---

### Post by Krisz on 2006-10-30
Dave

I am sorry for the miss spelling. My English isn't the best, and i was pretty mad when i posted the reply. SO unfortunately i can not overwrite the file 915resolution, because it is read only. I am not sure why i don't have access to it, since i am the only user on this computer. I went through many threads here to try to find out how to change the resolution of the screen, but most of the things i tried that was recommended here just crashed the xserver, and it gave me the blue screen that says the driver could not load properly, and i can only start my computer into command mode. 
I will try what you suggested here, and give it another try. It is just really bugs me that something extremely simple like changing the resolution of the screen takes so much to do and it is still not done yet. As i read through the forums here i see that many other people has the same problem.
Anyways i will try it tonight and let you know if it worked ot not.

Thank you for your help.

---

### Post by Krisz on 2006-10-31
Ok i did what you described, and still no. When i try to save the file from the console mode, it tells me i don't have permission to do that. "Permission Denied"
I am not sure what the problem is now, or how to fix it, but this 640x480 resolution drives me nuts. There is nothing i can do in Ubuntu because the resolution is so small.

---

### Post by devilsadvocate1987 on 2006-10-31
Hit 'ALT+F2' to open the application launcher.
In the thing that pops up, type 'gnome-terminal'

You will get a shell. Do everything from here and life will be a whole lot easier.

To install 915resolution, do 

```
sudo apt-get install 915resolution
```

Now, to edit the file, do 

```
sudo gedit /etc/default/915resolution
```

or, instead of gedit, I prefer to use nano in the console itself. The commands will be listed at the bottom. the ^ stands for ctrl

In the file, edit the XRES and YRES to suit your requirements.

---

### Post by bodhi.zazen on 2006-10-31
I wrote a mini how-to on 915resolution.

[See this link](http://ubuntuforums.org/showthread.php?t=269052)

Under the intel section ("915Resolution: Intel Video BIOS Hack") at the bottom (fairly detailed instructions and a few links if needed).

---

### Post by Krisz on 2006-11-01
Thank you for your reply.

I have tried all of these things and here is what i got.
With modifying the 915resolution file nothing happened, after i restarted the computer. I modified the resolution to 1280x1024, and when i restarted the computer it was at 640x480 just like before.

When i went to modify the xorg.conf it didn't let me save the file. It was telling me that i do not have permission to do that.

So now what.:-k

Oh yeah i forgot to mention if i try to edit xorg.conf file from the terminal with gedit, it will open a blank page. So i actually had to go into the directory and locate the file manually, than double click on it to edit it. But like i said it wont let me save it after i am done editing it.

---

### Post by devilsadvocate1987 on 2006-11-01
It wont let you edit xorg.conf unless you have superuser permissions. 

try this : 

```
sudo gedit /etc/X11/xorg.conf
```

otherwise, you could try

```
sudo gedit
```

and then browse for the file in gedits open file dialog. 


Are you sure you set XRES and YRES correctly in the 915resolution file? The file would have a lot of other stuff in it as well, mostly commented out.

---

### Post by Krisz on 2006-11-01
Ok and how do i get superuser permission since i am the only one using this computer and i am the only user so i don't understand if i installed the operating system onto my computer why don't i have the permission to do anything on the computer?

---

### Post by bodhi.zazen on 2006-11-01
> **Krisz said:**
> Ok and how do i get superuser permission since i am the only one using this computer and i am the only user so i don't understand if i installed the operating system onto my computer why don't i have the permission to do anything on the computer?

LOL it's for your own good !

See here: [Root sudo](https://help.ubuntu.com/community/RootSudo)

:lol:

---

### Post by luvdemheels on 2006-11-01
The only way I got mine to work was to install the intel driver for the xserver from synaptic. That was the easy part. After it is installed then you need to goto the terminal and recongire your xserver.. I think you need to type sudo dpkg-reconfigure xserver-xorg. That will let you be able to choose the resolution that you want to be able to use.

After I did that then I rebooted and have been happy ever since.

---

### Post by incubus on 2006-11-01
Krisz,

So you tried everything people suggested and you're still getting 640x480 when X starts?

If that's the case, I have a similar problem that I never figured out.  I have to restart X and then 915resolution does its magic.  So try Ctrl+Alt+Backspace in the login screen.

Let us know.

incubus

---

### Post by Krisz on 2006-11-01
Still nothing. No matter how much i edit the 915resolution file the beautiful 640x480 screen keeps on coming back like a bad rash. 
I will try that superuser thingy tonight and see if i can make a different. I think it will be a new video card purchase because i think it is my on board video thats the problem.
Also my refresh rate is set to 85Hz. I am not sure why i need so high refresh rate but i can not modify that either. I can almost swear that has something to do with me not being able to modify the resolution.

---

### Post by bodhi.zazen on 2006-11-01
> **Krisz said:**
> Still nothing. No matter how much i edit the 915resolution file the beautiful 640x480 screen keeps on coming back like a bad rash. 
I will try that superuser thingy tonight and see if i can make a different. I think it will be a new video card purchase because i think it is my on board video thats the problem.
Also my refresh rate is set to 85Hz. I am not sure why i need so high refresh rate but i can not modify that either. I can almost swear that has something to do with me not being able to modify the resolution.

I do not think you are on the right track at all.

Here is what I know about 915resolution, including examples:

915resolution is in the Ubuntu repositories.
[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

Either install it with Synaptic or;
```
sudo aptitude install 915resolution
```

_Configuration_:

[list=number][*]To list available resolutions:```
915resolution -l
```
_Note_: That is a small "L" and not the number 1.


[*]To use: If the resolution you desire is not listed you will need to edit one of the existing resolutions.
For example (using mode 5c (1920x1440):

```
sudo 915resolution [color=green]5c[/color] [color=red]1280 800[/color] [color=blue]24[/color]
```
[color=green]Mode to be changed[/color]
[color=red]Desired resolution[/color]
[color=blue]Desired color depth[/color]

Thus the Mode "5c" will be changed from the default resolution of 1920x1440 to the desired resolution of 1280x800 and a color depth of 24 bits.


[*]Additional examples:
> sudo 915resolution 3a 1440 900 24
sudo 915resolution 50 1280 768[/list]

[More Detailed Example](http://ubuntuforums.org/showpost.php?p=1465348&postcount=10)

[915resolution README](http://www.geocities.com/stomljen/readme.html)

This has worked for others and it should work for you as well.

after setting a new resolution with "sudo 915resolution ....." you need to restart X:

Ctrl-alt-Backspace

Select your new resolution, if needed, from the gnome menu.

---

### Post by Krisz on 2006-11-01
Ok

I followed your instructions word by word. After i set the resolution with 915resolution i get the message confirming that the current resolution set to 1280x1024 then i restart x with the Crtl+Alt+Backspace, then i get the 640x480 screen back.

I wonder if i should maybe wipe out my installation of Ubuntu and reinstall it again and try to do it again. I hate to be a pain in the butt but i don't know what am i doing wrong now.

---

### Post by bodhi.zazen on 2006-11-01
> **Krisz said:**
> Ok

I followed your instructions word by word. After i set the resolution with 915resolution i get the message confirming that the current resolution set to 1280x1024 then i restart x with the Crtl+Alt+Backspace, then i get the 640x480 screen back.

I wonder if i should maybe wipe out my installation of Ubuntu and reinstall it again and try to do it again. I hate to be a pain in the butt but i don't know what am i doing wrong now.

reboot

---

### Post by Krisz on 2006-11-02
Ok still no luck.
I went to change the resolution with sudo 915resolution 32 800x600 8, then reboot, nothing happened.
Then i went to edit the 915 file manually by sudo gedit /etc/default/915resolution and then reboot nothing happened.
I even have the latest version of the 915resolution it updated itself yesterday. Also i am running Ubuntu 6.10 in case anything is different in this release than it was in the previous one.
It is almost like Ubuntu completely ignores 915resolution all together. I have it installed properly i followed the instructions here. 

So you still think the problem not in my hardware?

---

### Post by Krisz on 2006-11-02
Also i forgot to mention this is a desktop computer not a laptop with intel 845 chipset. I dont know if theres something i can do to tweak the onboard video maybe theres something in the bios i can enable or disable to make things work maybe.:confused:

---

### Post by bodhi.zazen on 2006-11-02
1. What videocard do you have? Monitor?

2. What is your desired resolution and color depth? I assume you have an older videocard as you are setting your color depth at 8.

3. The command should read:
```
sudo 915resolution 32 **[color=blue]800 600[/color]** 8
```

not
sudo 915resolution 32 [color=red]**800x600**[/color] 8

4. Can you post /etc/X11/xorg.conf as an attachment (When you post, look down, see "Manage attachments", clikc that and select /etc/X11/xorg.conf)?

---

### Post by Krisz on 2006-11-02
Ok thank you i will give it a try tonight when i get home from work. I might made the mistake with putting x in the resolution.
I will let you know. ;)

---

### Post by Krisz on 2006-11-02
Still no luck
The strange thing is that i get the confirmation that the resolution has been changed or saved but still i am getting the 640x480 res.

To answer to your questions:
I have an onboard video card thats on my motherboard intel 845
The reason i was trying 8 bit in my settings is because i was just trying to switch my screen resolution to something else, other than 640x480. 

I would like to have 1280x1024 resolution with 32bit color depth and my monitor can support 85Hz refresh rate at that resolution. 
Here is my monitor : [http://www.bolha.com/oglas1958315](http://www.bolha.com/oglas1958315)

I tried the command without the X in the resolution but no luck. Like i said i get the confirmation about changing the resolution but after i restart the computer still the same 640x480 resolution is what i am getting.

I will post my xorg.conf file here.


```
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
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
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

```



Thank you for your help.

---

### Post by Krisz on 2006-11-02
I got it :KS 
In my bios for some reason i only had 1Mb set for my video adapter's memory. I changed it to 8Mb and now i can change my screen resolution to higher. Although i still can not go up to 1600x1200 but at least i can use 1280 x 1024 which is the one i wanted to use anyways.

Thank you for all your help guys.

---

### Post by devilsadvocate1987 on 2006-11-02
it seems things have changed since i last did this.

follow this how-to. It should work

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by encompass on 2006-12-22
Woops, bad post.

---

