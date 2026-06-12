---
title: "1440x900 resolution problem"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by hachirev on 2007-07-02
first off, I have looked at some of the other threads covering this topic but I have no idea what they are talking about. I got bored and decided to run ubuntu last night after wanting to for so long.
I cannot figure out how to change the resolution.  someone please tell me. I need a very thorough walkthrough seeing as I do not understand most of the teminology being used or what the things are. the only thing I know how to do is go to the terminal. the graphics is for ATI.

thanks

---

### Post by Seisen on 2007-07-02
To change your resolution you go to System>Preferences>Screen Resolution unless the 1440x900 isn't available then you will have to install the drivers for your graphics cards.

---

### Post by mysticrider92 on 2007-07-02
First, I will assume you are using the default open source video drivers. These should be able to support 1440x900 (at least the nVidia ones do), but you might want to do what Seisen suggested and switch to the ATi drivers.

You will probably need to edit the Xorg configuration file. To do this, open a terminal and type: > sudo gedit /etc/X11/xorg.conf
Scroll down and look for a line like this: 
> 	SubSection "Display"
		Depth	24
		Modes		 "1440x900"	 "1024x768"	 "640x480"
	EndSubSection
Your xorg.conf file will probably not have "1440x900" there, you will need to add this in the same place as mine. There may be additional numbers there, I have cleaned up my config file. After adding the line, save and close the file and restart X by pressing Control>Alt>Backspace. Log in, and the resolution should be correct. If not, open the window Seisen said and choose 1440 by 900.

---

### Post by hachirev on 2007-07-02
thanks

---

### Post by S1l3nt_Hunt3r on 2007-07-02
I manage to set the resolution in my pc: 1024x768 in a 15" Viewsonic E651 monitor, but the vertical refresh rate is set to 60 Mhz. How could I set it to a higher refresh rate, like 70Mhz ?

---

### Post by alienexplorers on 2007-07-02
Try putting a modeline in your "monitor" section of xorg.conf.  You can generate a modeline at:
> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

a modeline for 1024x768@70 would look like this:

> Modeline "1024x768_70.00"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync

---

### Post by S1l3nt_Hunt3r on 2007-07-03
> **alienexplorers said:**
> Try putting a modeline in your "monitor" section of xorg.conf.  You can generate a modeline at:


a modeline for 1024x768@70 would look like this:

I did the modeline thing but i think that i put it in the wrong place :-?. Anyway, I used the nvidia settings tool -> x server display configuration and set the appropriate refresh rate, then pressed the save to X configuration button. That action shows a  box with a preview button. In the preview windows I searched the next section and copied the bold entry to the clipboard  

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    **Option         "metamodes" "1024x768_70 +0+0; 1024x768_60 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"**
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

Then I opened the xorg.conf file and pasted the entry in bold in the Screen Section and commented the old one.  After that, saved the file and restarted the X server

I did the configuration in this way because the save button in the nvidia settings tool overwrite the xorg.conf file and I lose the other settings, like keyboard, etc.


PS: Thanks a lot **alienexplorers**, your answer did give me a hint about what to change!

---

### Post by alienexplorers on 2007-07-03
The modeline goes in the "monitor setcion of xorg.comf.
Example:

> Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 70.0
    VertRefresh     43.0 - 120.0
    ModeLine       "1280x1024_65.00" 119.4 1280 1368 1504 1728 1024 1025 1028 1063 -hsync +vsync
    Option         "UseEdidFreqs" "FALSE"
    Option         "UseEDID" "FALSE"
    Option         "DPMS"
EndSection


The EDID lines over ride the monitor refresh rates with a nvidia card.

---

### Post by S1l3nt_Hunt3r on 2007-07-03
Then that's why it didn't work; I didn't knew about the EDID lines. 

Well, with the nvidia settings is working.

---

