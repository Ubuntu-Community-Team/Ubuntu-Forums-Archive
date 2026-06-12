---
title: "Cant select screen res and slow audio...still puzzled."
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by chris_n00b on 2006-12-06
I've been searching and reading on these forums for about the past week now. Tried Ubnuntu 6.06 Dapper from the CD to check it out...wanted to get more into it so I built a computer, formatted the HDD and installed 6.06

I just plan on using this computer as a kind of media center. To store some mp3's, play some videos, play some DVDs etc...

I dont know anything really about linux. But I've been trying to learn here. I was able to do a few things on my own after searching and reading other peoples posts. I understand how to get to the command line. I dont understand what the commands mean or stand for, I just copy and paste to try to get what I want done LOL. 

Anyway. Went on YouTube, no sound. So read on here for a while and found a 'fix' entered the commands, one line at a time, hitting enter between each. Then the audio worked. BUT... its a bit slow and the pitch is lower than it should be. This is on all flash audio. Like the music players on myspace I tried and any other place I could think of. 

Is there any way to fix this?

Audio from CDs plays fine.

2nd problem Im having is with the screen resolution. It was stuck at 640x480 and 60hrtz. Im using a Nvidia geforce FX5200 256mb card. I read some posts around here, then snagged that Automatix thing from a link. Installed, then downloaded the drivers from that. Now my res is stuck at 800x600. Better, but I would like 1024x768 or even 1280x1024 would be ok. I opened that one config file trying to follow what other people are doing... the /etc/X11/xorg.conf one. 1024x768 IS listed under that Screen section. I just can't select it from the drop down menu.

What do I do next to fix this? Because when I open application windows and other things like that. They are so big I have to literally right click on the 'taskbar thing' and select 'Move' so I can drag it around to select what I want, THen right click and hit 'move' again to get to the save/close/apply etc.. button.  Pain in the butt.


 Should I get abook on linux or something also? to learn the commands and stuff? Or does this site pretty much have it all?

Thanks
Chris

---

### Post by Chinkostu on 2006-12-06
try
```
sudo dpkg-reconfigure xserver-xorg
```

you might have to switch to a terminal. use CTRL + ALT + F1.

it asks you a series of questions about your hardware. just answer them. if you got automatix drivers, use Nvidia. otherwise use NV.

theres also a script called Envy. it worked well for me. if it crashes, you'll have a backup xorg to work from and post back

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


the audio is probably an alsa problem. does it happen when you're playing MP3's from your hard drive or suchlike?

---

### Post by CatKiller on 2006-12-06
I don't use Flash, so I can't help you with your Flash sound problem. There are some posts about Flash causing sound problems, but I haven't read them for similar reasons.

You'll probably need to find the HorizSync and VertRefresh values for your monitor, and enter that information into your xorg.conf to get the resolutions you want. It's normally automatic, but sometimes it isn't.

In the meantime, Alt and left-click will let you drag windows around more easily.

Welcome to the community.

---

### Post by chris_n00b on 2006-12-06
> **Chinkostu said:**
> try
```
sudo dpkg-reconfigure xserver-xorg
```

you might have to switch to a terminal. use CTRL + ALT + F1.

it asks you a series of questions about your hardware. just answer them. if you got automatix drivers, use Nvidia. otherwise use NV.

theres also a script called Envy. it worked well for me. if it crashes, you'll have a backup xorg to work from and post back

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


the audio is probably an alsa problem. does it happen when you're playing MP3's from your hard drive or suchlike?

Ok I tried both but didnt' change anything. I rememeber though, before installing Ubuntu on the hard drive, I ran it off the cd, and I could during the original menu, press F4 to switch res and then when I ran Ubuntu in safe graphics mode off the cd I could switch the res under system > preferences. Now that its installed its at 800 x 600. ref rate 60hz

---

### Post by chris_n00b on 2006-12-06
> **Chinkostu said:**
> 
the audio is probably an alsa problem. does it happen when you're playing MP3's from your hard drive or suchlike?

Just tried playing some mp3s, plays correctly and quality is pretty good. *Almost can hear a little something like its clipping but its not really noticeable.*

EDIT After trying that other stuff, i ended up restarting a few times, and tried it again, played fine. Hmm... I, earlier, had installed some apps thinking I would need them. ( e.g. a CD burning program, some media players..etc..) I have just uninstalled them a litlle while ago.. maybe taht was the problem with the audio. Conflicts? Im gonna just be installing stuff as I need it I think.

The only problem now is that I want to increase my resolution above 800 x 600. What steps should I take to get that done?

Thanks.

---

### Post by gurcharan_cheema on 2006-12-06
hi,

i've been having the same problem...

i mange to get the option of 1024x768, and two refresh rates (60~70 hz). but on rebooting or turning off/on, the resolution goes back to the (safe) default setting of 800x600 and sometimes the sound is muted. 

i don't know how to gain control over this, but on restarting or turn off-on a few times, the set resolution is loaded.

this is becoming a little annoying..any help on working round the limited option allowed when setting the resolution

help appreciated - newbie

---

### Post by chris_n00b on 2006-12-06
I found a command to type in andmaybe this info can help.



Section "Monitor"
        Identifier      "DELL D1025TM"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "DELL D1025TM"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
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
 


That stuff was in the /etc/X11/xorg.conf thing.

---

### Post by chris_n00b on 2006-12-06
Ok in my Nvidia X Server Settings I have this info:

Graphics Processor: GeForce FX5200
Bus Type: AGP 8x

Operating System: Linux-x86
NVIDIA DRIVER VERSION: 1.0-8776

That makes me think I need this driver:

[URL="http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html"]
http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html[/URL]

On Step 2 : download the Driver file, how do I download that .run file? If i click it its just a page or script or something. I dont know commands yet...I can download it to the desktop by choosing Save link as, from the right click menu.. but the command that Nvidia gives


```
sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
```

says 'no such directory'

What do I do?

---

### Post by MacD on 2006-12-06
I have the exact same video card and didn't need to worry at all about video card drivers.

I'm pretty sure that what you need to do is change the vertical refresh rate in your xorg.conf file.

```
sudo gedit /etc/X11/xorg.conf
```

If this is indeed your monitor:
[http://support.dell.com/support/edocs/monitors/55341/specs.htm](http://support.dell.com/support/edocs/monitors/55341/specs.htm)
you will find the appropriate rate there.  Be careful, though, I think you can cause damage by setting the rate too high.

---

### Post by chris_n00b on 2006-12-06
> **MacD said:**
> I have the exact same video card and didn't need to worry at all about video card drivers.

I'm pretty sure that what you need to do is change the vertical refresh rate in your xorg.conf file.

```
sudo gedit /etc/X11/xorg.conf
```

If this is indeed your monitor:
[http://support.dell.com/support/edocs/monitors/55341/specs.htm](http://support.dell.com/support/edocs/monitors/55341/specs.htm)
you will find the appropriate rate there.  Be careful, though, I think you can cause damage by setting the rate too high.

Ok I tried that, but to no avail.


I wonder if I should change anything else in teh sections. For instance..

[B]Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	256000
	Option		"UseFBDev"		"true"
EndSection[/B]

The BusID, says PCI:1:0:0... I have it in an AGP slot... should that matter?

I set the Hor sync and Vert refresh to what it said in those stats on the dell support page ( that IS the correct monitor that Im using )

Then on the Server Layout section, it looks like this:

[B]Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection[/B]

screen says default screen.. should that be changed to anything?

I dont know why this seems to be so hard... all I want to do it bump it up to 1024x768 (or even have the option for 1280x1024 but not necessary)

Should I uninstall the nVidia drivers somehow? Maybe you were able to set yours up without the drivers and mine are overriding persay, to lockit down to 800x600.

---

### Post by MacD on 2006-12-06
Hmm... I don't know.

Here is the relevant section from my xorg.conf, if that helps at all.

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

It's also in an agp slot, came that way from Dell.

I also had this problem when I first installed, but I didn't get into drivers at all.

---

### Post by chris_n00b on 2006-12-07
> **MacD said:**
> Hmm... I don't know.

Here is the relevant section from my xorg.conf, if that helps at all.

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

It's also in an agp slot, came that way from Dell.

I also had this problem when I first installed, but I didn't get into drivers at all.

Wow the problem is gone now. Basically I was looking at your info and then did some more googling , etc... then for the heck of it changed 'nvidia' ( since I used Automatix ) to 'nv' then rebooted. EEEHHHH  * buzzer noise *  I couldn't reboot, said basically that my Xserver couldn't be started and I could load teh GUI because my etc/X11/xorg.conf file was not correct. Since Im brand new to Linux I didn't know really how to reedit that file or switch to my backup.  I found out how to change to the /etc/X11 directory but couldn't open the xorg.conf file. 

To make a long story short, since I had nothing at all on teh computer to lose I just reformatted and reinstalled 6.06 (Dapper)  Boom now the monitor is 1024x768 BUT the refresh rate is fixed at 0.  All I know is that its good enough for me LOL. Now I have to install all the updates and well see what happens.

---

### Post by CatKiller on 2006-12-07
> **chris_n00b said:**
> Since Im brand new to Linux I didn't know really how to reedit that file or switch to my backup.  I found out how to change to the /etc/X11 directory but couldn't open the xorg.conf file.

For reference, **nano** is a command line editor, so ```
sudo nano /etc/X11/xorg.conf
``` would have let you edit it back. **cp** is the copy command, so ```
sudo cp /path/to/xorg.conf.backup /etc/X11/xorg.conf
``` would have restored your backup.

---

### Post by chris_n00b on 2006-12-07
Oh I see, sweet! Thanks for that info! :)

---

