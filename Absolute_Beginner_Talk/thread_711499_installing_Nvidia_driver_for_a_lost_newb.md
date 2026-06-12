---
title: "installing Nvidia driver for a lost newb"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by repick_ on 2008-02-29
I'm fairly new to Ubuntu, so be gentle with me,

I have an 8800GT, but I can't get the drivers to install >.< I looked at a lot of tutorials and stuff, but in their advice the restricted drivers manager somehow snagged the right drivers...Mine doesn't :( 

I have the drivers downloaded, followed the instructions to on the page [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html) When I enter
sh NVIDIA-Linux-x86-169.12-pkg1.run"
I get a message like "Can't open sh NVIDIA-Linux-x86-169.12-pkg1.run" 

I've tried enableing to run as an .exe, but I get the error message
"ERROR: nvidia-installer must be run as root" 
I have a feeling ^ is the source of my problems. Like I stated before, I'm pretty new to Ubuntu and any help would be appreciated greatly.

---

### Post by Teber on 2008-02-29
you would need to find a way to log in as root user? there should be some thread explaining how. search should help you find it

---

### Post by repick_ on 2008-02-29
How do I get that Nvidia package to run as a root user? >.<

---

### Post by Therion on 2008-02-29
Do it the easy way.  Install and run [Envy](http://albertomilone.com/nvidia_scripts1.html).

---

### Post by handydan918 on 2008-02-29
> **repick_ said:**
> I'm fairly new to Ubuntu, so be gentle with me,

I have an 8800GT, but I can't get the drivers to install >.< I looked at a lot of tutorials and stuff, but in their advice the restricted drivers manager somehow snagged the right drivers...Mine doesn't :( 

I have the drivers downloaded, followed the instructions to on the page [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html) When I enter
sh NVIDIA-Linux-x86-169.12-pkg1.run"
I get a message like "Can't open sh NVIDIA-Linux-x86-169.12-pkg1.run" 

I've tried enableing to run as an .exe, but I get the error message
"ERROR: nvidia-installer must be run as root" 
I have a feeling ^ is the source of my problems. Like I stated before, I'm pretty new to Ubuntu and any help would be appreciated greatly.
Have your tried synaptic? There is a restricted drivers section that has nvidia drivers in it...
If that doesn't work, running the command ```
sh NVIDIA-Linux-x86-169.12-pkg1.run
``` must be prefaced by ```
sudo
```, so the whole thing looks like this...
```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

That will only work if you have successfully changed the permissions on the file to make it executable.


From the terminal, ```
sudo chmod +x NVIDIA-Linux-x86-169.12-pkg1.run
```

Hope this helps!

---

### Post by Therion on 2008-02-29
Forgot too mention, if your 8800 is anything like mine, once you use Envy to install the driver and configure X, your monitor will be set to use some horrible resolution like 600x480.  You just need to make a quick change in your xorg.conf file to correct that and you should be good to go.

First, back-up your existing xorg.conf file:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Now open your xorg.conf file and change the default resolution```
sudo dpkg-reconfigure xserver-xorg
```

Use the Tab button to move around, and highlight in red, the defaults for everything until you come to the part about Monitor Resolutions.  Look closely here...  There will be a little window with all the screen resolutions you can choose from, even though you'll only see about six or eight in the window (you can scroll up for higher resolution choices).   

Choose three resolutions here by using the spacebar to put an "*" in the resolutions you want to be able to use, and removing the "*" from the resolutions you don't want to use -- know now that the HIGHEST RESOLUTION you choose here will become the new DEFAULT screen resolution once you reboot.

Use Ctrl+X to overwrite the file with your changes, Save and Exit.  

Cross your fingers for good luck.

Use Ctrl+Alt+Backspace to restart X.

---

### Post by repick_ on 2008-02-29
I used Envy and it worked! 

I guess I must have messed with the xorg file... actually I think Envy did it for me.

---

### Post by Therion on 2008-02-29
> **repick_ said:**
> 

I used Envy and it worked! 

I guess I must have messed with the xorg file... actually I think Envy did it for me.
Envy is scripted to configure your xorg.conf, but it's not uncommon for the resolution to be screwy; guess you got lucky!  

Glad so hear everything panned out for you.

---

### Post by 141N on 2008-02-29
Good to see that its working! :) Just my 2p here, but I backed up my xorg.conf file like is mentioned above, then edited it this way, so that:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
```

becomes:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
```

I have restarted X and it works fine, and has been fine for the last few hours - I apologise if anybody feels I may be beating a dead horse here :confused:, and if anybody can see anything wrong with the above then let me know :)

---

### Post by aparabola on 2008-03-04
Please help! I made some kind of configuration in the terminal that I read in some post that I can't find. If I could find that post, I might be able to get my small, normal resolution back. The thread centered around the 8800GT graphics card. 

Now, my screen resolution is HUGE. Funny thing is, I was not experiencing any issues at all either. No problems at all. Now I have a problem. I misread the post and thought I had a backup plan where if I entered: 

cp /var/backups/xorg/xorg.conf.2008-03-04-00:15:14 /etc/X11/xorg.conf 

into the terminal I would be able to bring my computers settings back to where they were before. I guess that's what I get for horsing around. With so many others here with real problems, I go and mess something up where I have no business. I feel really stupid and now my resolution is HUGE, something like 800X400. My resolution did used to be a very nice 1680 X 1150.

Can anyone suggest a way to reconfigure xorg or just some fix in general so I can get my screen back to small please? It should be just a matter of entering the right code into the terminal. Thanks in advance for your help.

---

### Post by PmDematagoda on 2008-03-04
Boot Ubuntu in Recovery Mode and execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
and select the proper resolution for the monitor, after reconfiguration is done, check the settings by starting the X-Server using:-
```
sudo startx
```

---

