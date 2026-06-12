---
title: "I ran Envy to upgrade my NVIDIA legacy card but...."
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2006-12-18
The screen resolution, video quality etc are unchanged. I'd like to go to my monitor's native 1280X1024 but my max in dapper here seems to be 1024x768. Hmm :(

---

### Post by bodhi.zazen on 2006-12-18
What monitor ?

Post xorg.conf (/etc/X11/xorg.conf)

---

### Post by konungursvia on 2006-12-18
It's a Philips 15" LCD which in M$ Windoze can handle higher resolutions.

---

### Post by bodhi.zazen on 2006-12-18
We likely need to modify the monitor section in xorg.conf to include the monitor's specifications.

---

### Post by konungursvia on 2006-12-18
Thanks for that kind reply, bohdi.zazen. Any more specific info on how to do that? I did manage to mount a fat32 drive by editing one of those text files, so I can probably do that too, with a little help. Hopefully this may help others here too.

---

### Post by bodhi.zazen on 2006-12-18
In a terminal type:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```

The first command makes a backup, just in case :)

Post the contents of that file, or at least the monitor section :p

---

### Post by konungursvia on 2006-12-18
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Well, that's what this says. Hopefully this form will parse the breaks as <br> or <p> so you don't have to read it as a single string paragraph. :)

---

### Post by bodhi.zazen on 2006-12-18
Try changing to:

> Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31-61
VertRefresh 43-75
EndSection
```

Then re-start x:

Ctrl-Alt-Backspace

or 

sudo /etc/init.d/gdm restart

If that fails, you will drop to a comand line (Ctrl-Alt-F1 in needed)

type:```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

---

### Post by konungursvia on 2006-12-18
Thanks! So I did edit that into it, but I still can't select anything greater than the present resolution, after a restart (though I didn't restart the way you suggested, I just clicked on the exit door and then on restart)/

---

### Post by bodhi.zazen on 2006-12-18
Try re-booting ....

---

### Post by qamelian on 2006-12-18
> **konungursvia said:**
> Thanks! So I did edit that into it, but I still can't select anything greater than the present resolution, after a restart (though I didn't restart the way you suggested, I just clicked on the exit door and then on restart)/
You also need to edit the mode lines. Currently, the only resolution showing in any of your mode lines is 1024x768. Change the mode lines to read
```
mode "1280x1024" "1024x768"
```
and resave the file. Logout of your session and press Ctrl-Alt-Backspace to restart your X server. When you log back in, you should be able to run at 1280x1024.

---

### Post by konungursvia on 2006-12-18
Ok, have done so again. Still there appears to be no change, though I now open that file and see the new entry for "monitor". Do we need to include a new entry in the section below it as well?

---

### Post by bodhi.zazen on 2006-12-18
Like this:

> Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV17 [GeForce4 440 Go]"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768"
EndSubSection
EndSection

Thanks qamelian :p

I totally missed that one :(

---

### Post by konungursvia on 2006-12-18
Very interesting. I appreciate all the help. This time when I first hit the gui, the fonts for Applications Places System were smaller for a quarter of a second, then went back to the usual size. I still can't explicitly see or select higher than the 1024x768 in Screen Resolution, though I see that now Linux seems to be able to display what I want, if only for an instant.

---

### Post by qamelian on 2006-12-18
> **bodhi.zazen said:**
> Thanks qamelian :p

I totally missed that one :(

No problem. I've missed the same thing more than once. I usually realize what I've missed after putting substantial dents in the wall...with my head.:)

---

### Post by qamelian on 2006-12-18
> **konungursvia said:**
> Very interesting. I appreciate all the help. This time when I first hit the gui, the fonts for Applications Places System were smaller for a quarter of a second, then went back to the usual size. I still can't explicitly see or select higher than the 1024x768 in Screen Resolution, though I see that now Linux seems to be able to display what I want, if only for an instant.

Can you find the specific model number? I've been checking on Philips LCD monitors, but all the 15" models I can find listed specify 1024x768 as the maximum resolution. With the specific model, we might be able to locate the specs online to find the specific refresh rates of your monitor. This can affect a number of aspects of your display.

---

### Post by qamelian on 2006-12-18
Further checking shows one model that will handle 1280x1024: the Philips 150MT10Y. The refresh rate on this monitor is 60 Hz. If this is your model, you may need to set the range for your refresh rate to 60-60 rather than the current range of      ```
VertRefresh    43-60
```

---

### Post by konungursvia on 2006-12-18
Whoops! Sorry for the delay. I tried it and it didn't work, so I hastily cut and pasted your settings into the text file and saved. I think I did so incorrectly, because I was in text only mode for half an hour trying to remember from Dos and Sun Solaris how to rename the .bak file onto the original to get it running again. 

I apologize, but now I see it's a 17" philips monitor. Model No 170S5FG/27.

I'll try the new idea as well.

---

### Post by qamelian on 2006-12-18
> **konungursvia said:**
> Whoops! Sorry for the delay. I tried it and it didn't work, so I hastily cut and pasted your settings into the text file and saved. I think I did so incorrectly, because I was in text only mode for half an hour trying to remember from Dos and Sun Solaris how to rename the .bak file onto the original to get it running again. 

I apologize, but now I see it's a 17" philips monitor. Model No 170S5FG/27.

I'll try the new idea as well.
No worries. I go through this once in a while when I decide to test a new distro on my laptop. I used to be more well-versed in this stuff. My first linux distro required me to install X by hand and I learned a lot, but I've become spoiled since most distros just seem to work for me now. No pain, no gain, I guess.

---

### Post by konungursvia on 2006-12-18
Thanks again. Well now I've put the refresh rte at 60 Hz with the last suggestion. This is an improvement, as now I see less of that subtle interference (waves descending toward bottom right along all the monitor). Now, interestingly, there are only 3 choices rather than 4 for screen resolution, and the highest is still... 1024x768. Strange. Don't know what else to try. Here's what I have now, and have rebooted into it.

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Go]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-61
	VertRefresh	60-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Go]"
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

Any other things I missed?

---

### Post by bodhi.zazen on 2006-12-18
LOL :lol:

Change > Driver "nv"

To```
Driver "nvidia"
```

---

### Post by konungursvia on 2006-12-18
Lol ok!

---

### Post by konungursvia on 2006-12-18
Ok, done that. Still the same, nice display in 1024x768max. Hmm.

---

### Post by bodhi.zazen on 2006-12-18
Add this to your monitor section:

        Option 		"UseEdidFreqs" "1"

Like this:```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31-61
VertRefresh 60-60
Option   "UseEdidFreqs" "1"
EndSection
```

---

### Post by konungursvia on 2006-12-18
Thank you! It worked! I'm now in the resolution I wanted! Wonderful, God Bless Montana!

---

