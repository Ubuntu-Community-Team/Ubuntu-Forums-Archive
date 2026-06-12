---
title: "[SOLVED] after turning compiz fusion on i can not minimiz a window?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by shortybookit on 2007-09-20
is this something  you loose w/ compiz

if so how do you minimiz the window if you do not have the "-" on the top right?

i just noticed i can not close the window with the "x" 

what the heck?

---

### Post by shortybookit on 2007-09-20
and when i do the alt control down for the 3d cube it is not a cube it is i dunno unfolded no 3d effect whatso ever

---

### Post by shortybookit on 2007-09-20
what is the <super> button 

i.e. when i am in the compizconfig manager and i click one of the icons then actions 
it says the button shortcut for this effect is <super>and a leter

---

### Post by forestpixie on 2007-09-20
I think you need to add this into your xorg.conf file

> Option "AddARGBGLXVisuals" "True" to your screen section, mine looks like this

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024_75 +0+0;"
    [COLOR="Red"]Option "AddARGBGLXVisuals" "True"[/COLOR]
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection    
EndSection
```

backup first -

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.2009
```

then edit the file

```
gksudo gedit /etc/X11/xorg.conf
```

gksudo gedit assumes you're using Ubuntu, Kubuntu is kdesu kate I believe

---

### Post by Billy_McBong on 2007-09-20
[COLOR="Blue"]it is alt ctrl left click to do the cube

and im not sure about the minimize/close problem. emerald might solve it
EDIT:the <super> key is the key with the windows logo[/COLOR]

---

### Post by shortybookit on 2007-09-20
the alt control left works but the videos i watched about this 3d cube when u hit alt control and left the whole cube shrinks down so you can see the whole cube and the entire cube is like half the screen then you could see through the cube what settings do i have to change for this?

---

### Post by shortybookit on 2007-09-20
how do u edit the xorg.conf file
I AM A TOTAL NEWBIE
thanks

---

### Post by LowSky on 2007-09-20
> **Billy_McBong said:**
> [COLOR="Blue"]it is alt ctrl left click to do the cube

and im not sure about the minimize/close problem. emerald might solve it
EDIT:the <super> key is the key with the windows logo[/COLOR]


I like the old beryl way to use the cube... Mouse button two, on a open desktop..ah memories... oh wait just change the settings.... ah, works the way I like

---

### Post by forestpixie on 2007-09-20
yea - saved post when I put kids to bed - edited it now - hope that helps, that should get rest of your windows back.

After you've edited and saved - ctrl- alt - backspace will restart

---

### Post by LowSky on 2007-09-20
> **shortybookit said:**
> how do u edit the xorg.conf file
I AM A TOTAL NEWBIE
thanks

```
sudo-i
```
enter passowrd

```
gedit /etc/X11/xorg.conf
```

---

### Post by shortybookit on 2007-09-20
were do i put the option
 Option "AddARGBGLXVisuals" "True"???

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection

---

### Post by LowSky on 2007-09-20
see the red? right there

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024_75 +0+0;"
    [COLOR="Red"]Option "AddARGBGLXVisuals" "True"[/COLOR]
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection    
EndSection
```

---

### Post by shortybookit on 2007-09-20
i added the line but i still have no option to close,minimiz, or resize a window 

do i need to reset and it should work after reset?

---

### Post by forestpixie on 2007-09-20
yes do a ctrl-alt-bkspc

---

### Post by rickycodie on 2007-09-20
wow pay more attention to the posts please, these were both explained to you.

---

### Post by shortybookit on 2007-09-20
after reset i still have no way to resize,close,minimiz ANY window i had the option a few seconds ago before i turned compiz fusion on

---

### Post by forestpixie on 2007-09-20
I'm afraid I can't help anymore then - I just know that should do it from when I flirted with beryl and then compiz-fusion. I have it all turned off now :(

It might be worth posting your xorg.conf to make sure you've put it in right place.

```
cat /etc/X11/xorg.conf
```

---

### Post by shortybookit on 2007-09-20
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        Option "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

---

### Post by forestpixie on 2007-09-20
try putting it right at the end - but I'm not sure if it'll help

```
Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82865G Integrated Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
Option "AddARGBGLXVisuals" "True"
```

---

### Post by shortybookit on 2007-09-20
nope

---

### Post by forestpixie on 2007-09-20
sorry can't help then :(

don't even know how to turn compiz off

---

### Post by mlentink on 2007-09-20
> **forestpixie said:**
> 
don't even know how to turn compiz off

Ahhh, wouldn't System>Preferences>Desktop Effects and switching them ***off*** help?

---

### Post by shortybookit on 2007-09-20
ummmmmmmmmm anyone

---

### Post by shortybookit on 2007-09-20
had to go in to the compiz config manager and click enable window decoration

:)

---

