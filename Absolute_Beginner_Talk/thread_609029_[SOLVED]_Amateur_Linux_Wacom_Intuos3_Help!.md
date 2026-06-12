---
title: "[SOLVED] Amateur Linux Wacom Intuos3 Help!"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-11-10
Can anyone help me with my Wacom Intuos3? I have had it for about a week now and have gone to the Linux Wacom Project page multiple times - I look at it so much it is as if I live to see that page. However, the documentation is still too advanced for me as I have been using Ubuntu for about a month and a half and have no coding and not too much terminal experience (though I have received links to terminal documentation that I am currently going over.) I still do not fully know what "X" is, I do not know how to access or what an xorg.conf file is or whatever it may be, and I cannot seem to get past the wacom.(k)o configuration part in the documentation with my 64-bit 2.6.19 kernel that is somehow in a 2.6.22 folder. I do not know what the heck is going on here, as I cannot even run the command more /proc/bus/usb/devices in terminal anymore! Someone help me out here because this is making me think back to the days where Windows was somewhat more straightforward than this... even though I do not think I will ever go back!! x_x

---

### Post by matthewcraig on 2007-11-10
X is the Graphical Desktop Manager (gdm).  The service will allow a GUI login by your keyboard and monitor, or even some other computer's keyboard and monitor.

Is Wacom using an Ubuntu installation?  I am confused on that.

Also, in Ubuntu, you can use the System -> Administration -> Screens and graphics, instead of having to edit the xorg.conf file.

---

### Post by ShadowMKII on 2007-11-10
To try and get my tablet working, I went to the Linux Wacom Project page and downloaded the latest .tar file that they have there. The .tar file has 64-bit support, as well as a whole bunch of folders within it that can support many different types of kernels, depending on what kernel version one has. It will work on all types of Linux, from what I have heard.

---

### Post by Bale on 2007-11-12
I'm in the same boat as you.  I've been through the Linux Wacom pages so many times that i'm just sick of it.  I've even emailed them, but never heard anything back.  I've followed their tutorials over, and over, and over..... with no luck.

---

### Post by ShadowMKII on 2007-11-13
Ghah, being an amateur with a lack of assitance sure is a show-stopper. Well, at the very least, I feel your pain!

---

### Post by ShadowMKII on 2007-11-23
Hello out there?

---

### Post by clesage on 2007-12-02
I found this thread to be **very** helpful. I got my new Intuos 3 working within 10 minutes.

[http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)

1. Install wacom-tools by using sudo apt-get
2. sudo gedit /etc/X11/xorg.conf - This is the tricky part that you do as root. Save a backup first, just in case. Edit xorg.conf according to the instructions (add/delete the lines that do/don't apply to you.)
3. Restart
4. Enable the tool in your programs (like Gimp)

I wish you luck. I know how hard it can be when you don't fully understand the concepts. Hang in there, and things start to make more and more sense as you go.

Cheers,
Chris

---

### Post by ShadowMKII on 2007-12-06
Well, I got pretty far and copied what I needed to copy, I think, but I am not sure. I went so far as to restart X after being not entirely sure what lines I needed copied, but now my X will not start back up. Once I get that working - if I ever do - I will post my gedit file here so you can see why I am so confused as to what lines I need put in there. I also want to get my pressure sensitivity working.

---

### Post by clesage on 2007-12-06
Ah sorry to hear that. :(

That's why it is important to save a backup of this file.

Here is what I used for my configuration. I have an Intuos3, USB connection. These lines go directly after the mouse section. I removed all the serial lines, and I kept the USB lines. I also kept the Tablet PC lines, but I don't have a tablet PC. But it works.

```

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"		#USB ONLY
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"		"on"		#USB ONLY
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"	#USB ONLY
	Option		"Type"		"cursor"
	Option		"Mode"		"relative"
	Option		"USB"		"on"		#USB ONLY
	Option		"ForceDevice"	"ISDV4"		#Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  #USB ONLY
EndSection

```

But, I bet you had trouble with the following:
In MetalMusicAddict's post, there were only 4 lines that were black, and the rest were slightly greyed out. The **only** lines you should have added were the 4 black lines. Everything else should remain however it was.

- Did you add these lines in the "ServerLayout" Section?
- Did you leave all the other lines around it the same?
- Did you put the lines in the same order? (I don't know if that matters or not)

```

Section "ServerLayout"
        ### Whatever you had before you should remain here! ###
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
        InputDevice    "pad"   #If you have Intuos3/Cintiq 21UX/Graphire4 tablets. It should NOT send core event
EndSection

```

Good luck.

---

### Post by ShadowMKII on 2007-12-20
Well, I have finally got around to doing what you told me to in your last post, and the pressure sensitivity works perfectly! Thank you very much for all of your assistance! When I was editing the xorg.conf file, I did the first part that you pasted onto the thread here incorrectly. I tried editing everything manually, which caused me to make a couple of mistakes. As a consequence, my X shut down and I had to do some fiddling here and there to get everything working. (I posted a thread about that on this forum, so just search up that thread and you will understand what I mean.) Now that I have my pressure sensitivity, thanks to you, the only thing I have left to do is to learn how to program each button and zoom bar on the Intuos3's tablet to do what I want it to do. If you would like to help me with that, it is completely up to your discretion. Thank you very much again! This venture, compared to the one on the Wacom Project's website is far more simplistic and effective! I am one joyous digital artist now thanks to this help of yours!

---

### Post by teethgrinder on 2008-01-09
> **clesage said:**
> 
1. Install wacom-tools by using sudo apt-get
2. sudo gedit /etc/X11/xorg.conf - This is the tricky part that you do as root. Save a backup first, just in case. Edit xorg.conf according to the instructions (add/delete the lines that do/don't apply to you.)
3. Restart
4. Enable the tool in your programs (like Gimp)


Ta very much for this clesage ! Simple ist gut... works like many treats all exploding in one fancy-as hit. For the others out there who are like me--formerly self-assured and as fresh as less than a few hours into your first lick at the vortex of linux and more than a little ubunted for it - the sudo apt-get in step 1 is:

```
sudo apt-get install wacom-tools
```

backing up your xorg.conf pre step 2 be like this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

(just to put it all in one place). Funny how it all makes sense after you do it...

---

