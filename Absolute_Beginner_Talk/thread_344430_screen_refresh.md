---
title: "screen refresh"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by none21 on 2007-01-22
question about refresh. my screen refresh rate is locked @ 85. the screen seems like it's blinking on and off rapidly and it hurts my eyes. how would I go about changing the refresh rate if there's no other options and would you think I should increase, or decrese Hz

---

### Post by riven0 on 2007-01-22
Have you tried just doing a reconfiguration and letting xserver automatically configure it for you? That's what I did and it worked fine.

> sudo dpkg-reconfigure xserver-xorg

---

### Post by none21 on 2007-01-22
/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed

confused here?

---

### Post by Bachstelze on 2007-01-22
That sounds bad. Maybe try :

```
sudo apt-get -f install
```

---

### Post by none21 on 2007-01-22
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

wow, I wish this was easier for me

---

### Post by riven0 on 2007-01-22
Okay so try doing that:

> sudo dpkg --configure -a

Then:

> sudo apt-get install --resintall xerver-xorg

---

### Post by Wim Sturkenboom on 2007-01-22
With 85 Hz you should not see the flickering unless you have very good eyes. If you want to get it better, you need to increase.

I wonder if you still can increase it. If your screen is not recognized, it will usually default to 60 Hz (not 85).

You need to modify the file */etc/X11/xorg.conf*.
[LIST]
[*]Search for *VertRefresh* and *HorizSync* in the *monitor section* and make sure that they reflect the capabilities of your monitor.

[*]Further you can add the following line to the *device section*:
```

Option       "UseEdidFreqs" "False"
```My setup was stuck at 75 Hz and this did the trick for my Nvidia card. Not sure for other cards.
[/LIST]

After the changes, you have to restart the X-server with <ctrl><alt><backspace>

If the given solutions don't work, your monitor probably does not support higher refresh rates at the used resolution.

Please post the make and model of your videocard and your monitor and the used resolution.

---

### Post by none21 on 2007-01-22
compaq fs7600 as far as the video card (nvidia GeForce 6150 LE)

---

### Post by Wim Sturkenboom on 2007-01-22
Sorry, but you can't go higher at 1024x768.

You can calculate some stuff yourself on [http://zaph.com/Modeline/](http://zaph.com/Modeline/)

In the horizontal section, fill in the pixels (i.e. 1024). In the vertical section fill in the pixels (i.e. 768 ) and the frequency (vertical refresh rate; i.e 85) and click calculate. Do NOT change the other info unless you know what it's all about.

Check the result. In the horizontal section a frequency will be given (68.255 kHz). This (horizontal) frequency must be within spec of your monitor (which is 30 - 70 kHz; see [http://www.dealtime.com/xPF-Compaq-Monitor-FS7600](http://www.dealtime.com/xPF-Compaq-Monitor-FS7600) )

If you choose a higher vertical refresh rate, you will see that the result will fall outside the spec of the monitor.

Only options you have
[LIST]
[*]decrease the resolution if you want to use a higher vertical refresh rate 
[*]buy better monitor
[/LIST]
Both are probably not an option :cool:

---

### Post by none211 on 2007-01-23
I just found a menu option directly on my screen. it reads;
H: 48.4kHz
V: 60Hz

and that calculator thing reads;

Horizontal  	Pixels  	1024
Frequency 	68.255 kHz

Vertical  	Pixels  	768
Frequency 	85.0 Hz

would this have anything to do with my screen looking crappy? because I can't change what the screen reads out

---

### Post by Wim Sturkenboom on 2007-01-24
OK you're not using 85 Hz but 60 Hz so I can understand that you get headaches.

Check /etc/X11/xorg.conf. There are two lines in the monitor section (VertRefresh and HorizSync); verify that they have the correct values (see specs) and adjust if not

In the same file, you can check which driver you're using (in the device section; vesa, nv or nvidia).

---

