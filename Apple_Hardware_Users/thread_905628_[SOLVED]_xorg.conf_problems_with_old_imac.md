---
title: "[SOLVED] xorg.conf problems with old imac"
date: 2008-08-30
forum: Apple Hardware Users
---

### Post by Kilz on 2008-08-30
[In my last thread]("http://ubuntuforums.org/showthread.php?t=905485") I figured out how to get the imac to the command prompt. But I have run into a brick wall with the xorg.conf. With the stock xorg.conf it ends up with a black screen. 
So I went on a search of the forums and found a xorg.conf. The computer ends up with a blue screen telling me the x server isnt configured and that the failsafe failed if I click Yes.
Here is an xorg.conf I have that at least leads to the blue screen.




```
Section "Device"
	Identifier	"ATI Technologies Inc Rage 128 Pro Ultra TR"
	Driver		"ati"
        BusID           "PCI:0:18:0"
	Option		"UseFBDev"		"true"
EndSection


Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	58-62
         VertRefresh	75-117

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage 128 Pro Ultra TR"
	Monitor		"iMac"
	DefaultDepth	24
	SubSection "Display"
		Modes	"800x600" "640x480"
	EndSubSection
EndSection
```

Would anyone have a working setup for one of these old 266 iMacs, or a clue as to how to get this working? I have reinstalled xorg and xubuntu desktop. I have tried dpkg-reconfigure xserver-xorg with and without the -phigh. I have a working cli system, but cant get to the desktop.

---

### Post by tiresia on 2008-08-30
You can try this:
[http://ubuntuforums.org/showthread.php?p=4808544](http://ubuntuforums.org/showthread.php?p=4808544)

---

### Post by Kilz on 2008-09-01
> **tiresia said:**
> You can try this:
[http://ubuntuforums.org/showthread.php?p=4808544](http://ubuntuforums.org/showthread.php?p=4808544)

Thanks for the link, now it goes to a blank screen when it should show the login and the power button goes orange. I can actually sign in and hit ctl + alt + f1 and get to a command line. But I still have no desktop.

---

### Post by gaussian on 2008-09-01
Try
```

Option		"UseFBDev"		"false"

```

---

### Post by Kilz on 2008-09-02
Thanks for the suggestion, but it didnt work. I then went and lowered the  VertRefresh to 50-60 then 50-70 and I have a desktop. Its only 640x480, but at least its progress.

This xorg.conf is the current one.

```

Section "Device"
	Identifier	"ATI Technologies Inc Rage 128 Pro Ultra TR"
	Driver		"ati"
        BusID           "PCI:0:18:0"
	Option		"UseFBDev"		"false"
EndSection


Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	58-60
         VertRefresh	50-70

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage 128 Pro Ultra TR"
	Monitor		"iMac"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1027x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by tiresia on 2008-09-02
Of course it should be 102**4**
> **Kilz said:**
> 
		Modes	"102**4**x768" "800x600" "640x480"


Why don't you try with the values from the link I gave you?

---

### Post by paul_mcl on 2008-09-02
Thank you very much for this information. I had the same problem. 'startx' or 'start(anyx)' crashed my system (Power Mac G4 466 DA) too. Now I'm happy. Thanks again.

---

### Post by Kilz on 2008-09-02
> **tiresia said:**
> Of course it should be 102**4**


Why don't you try with the values from the link I gave you?

The values in the link you gave dont work. They leave me with a blank screen and a orange start button. I will edit the 1024, but I cant even get into 800x600. I have a feeling there is some driver not loading.

---

### Post by ristosu on 2008-09-02
The reason for the black screen lies in the hardware: the screen won't sync on anything but 60 kHz horizontal frequency. The values in your first post are the correct ones:
```
HorizSync 59-61
VertRefresh 75-117
```
Put those values into the xorg.conf that gives you black screen, and it should work. I have a 333 Mhz iMac that is working with 1024x768 resolution in Ubuntu 6.06.

Risto

---

### Post by Kilz on 2008-09-02
> **ristosu said:**
> The reason for the black screen lies in the hardware: the screen won't sync on anything but 60 kHz horizontal frequency. The values in your first post are the correct ones:
```
HorizSync 59-61
VertRefresh 75-117
```
Put those values into the xorg.conf that gives you black screen, and it should work. I have a 333 Mhz iMac that is working with 1024x768 resolution in Ubuntu 6.06.

Risto

Thanks , Ill try that, but can you please post or attach the xorg.conf for that machine?

---

### Post by stream303 on 2008-09-02
You may also want to disable glx and dri.  You may have to manually add a "modules" section at the end:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

---

### Post by ristosu on 2008-09-03
> **Kilz said:**
> Thanks , Ill try that, but can you please post or attach the xorg.conf for that machine?

Sure, I'll be back...

Ok. I had to rename the file to xorg.conf.txt for being able to upload it. So this file works on an iMac G3/333.

Risto

---

### Post by Kilz on 2008-09-04
Thanks I have 1024x768 graphics working now. Its kind of slow. But the xorg.conf file has helped a lot.

---

