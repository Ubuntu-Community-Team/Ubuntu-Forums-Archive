---
title: "Out of range, 96x96 DPI and Firefox problem - New User"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by DaeronTinúviel on 2007-05-16
hi, i new to the whole ubuntu/linux thing but i must sy that i really impress with it....everything has been  fine except for those 3 things in the topic titles, let me elaborate:

** First Issue:**

when i power up the pc right before to get to the login screen i get an Out of Range error that stay like 5-10 seconds and then i get the login screen, how can i fix that? here is my xorg.conf:

```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver		"ati"
        Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	22-82
        VertRefresh     56-76
#       DisplaySize	212	159	# 800x600 96dpi
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
		SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Option          "AIGLX" "true"
        Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

i try to find info about my LCD Display(advueu) but havent found anything that can help me here is my model #: **A170E1-02 **
Rev. C1

**2nd Issue**

I have try everyhting i found to set my fonts to 96x96DPI but always stays @ 75x75, any ideas?


**3rd Issue**

I have use firefox in my windows pc since 2 or 3 years ago and never experience this issue: if i go to any site that has lots of thumbnails Firefox start displaying them but then it just display a few of them and then just stays there tryinf to load the rest but never do it, at the same time if I try to open a new tab to go to another site while I wait the other site will not open it just stay lookin to load.......until i have to close firefox to load any other site....this has me without any idea

well hope u guys can help me, thkz in advanced

---

### Post by DaeronTinúviel on 2007-05-17
???

---

### Post by DaeronTinúviel on 2007-05-20
nobody?

---

### Post by DaeronTinúviel on 2007-05-20
:(

---

### Post by Toky on 2007-05-24
I don't see what version of Ubuntu you are using posted... what is it??
----No veo la version de ubuntu que usas... cual es??

1-It seems your xorg.conf is missing lower color depth resolutions, did you edit the xorg.conf???
----Parece que tu xorg.conf le faltan resoluciones con cantidad de colores mas bajos, tu editastes el file???

2-The default font in Ubuntu desktop is sans 10pt (96x96 dpi). This can be changed 
----El font "standard" en ubuntu es sans 10pt, esto lo puedes cambiar en:
System > Preferences > Font applet.


There is a difference between font size and dpi.
----Hay differencia entre el tamano del font y el (o los) dpi.

Fontsize is the "visible" size of the font on a given output device (ie monitor or printer)
----Fontsize es el tamano "visible" de el font en cualquier dispositivo de output (como el monitor o el printer)

DPI is the amount of dots used to "render" (maybe display is a better word?) the font, so the more dots, the "smoother" it looks.
----DPI es la cantidad de puntos usados para "dibujar" los fonts, mientras mas puntos mas definida se vera el font.

3- I think we need more info to help on this one...
what type of internet connection do you have?
what version of firefox,
amount of RAM on your system?

----Creo q necesitamos mas info para ayudarte en esta...
----Que tipo de coneccion tienes?
----que version de Firefox usas?
----cuanto ram tiene tu PC?

Firefox behaves the same way in Window$ as in Linux.

---

### Post by DaeronTinúviel on 2007-05-24
> I don't see what version of Ubuntu you are using posted... what is it??
----No veo la version de ubuntu que usas... cual es??

Ubuntu 7.04

> 1-It seems your xorg.conf is missing lower color depth resolutions, did you edit the xorg.conf???
----Parece que tu xorg.conf le faltan resoluciones con cantidad de colores mas bajos, tu editastes el file???

yes i edited, my monitor is a LCD and only support those resolutions listed

> 
2-The default font in Ubuntu desktop is sans 10pt (96x96 dpi). This can be changed
----El font "standard" en ubuntu es sans 10pt, esto lo puedes cambiar en:
System > Preferences > Font applet.

i know that but if i check using the terminal its output is 75x75

> 3- I think we need more info to help on this one...
what type of internet connection do you have?
what version of firefox,
amount of RAM on your system?

----Creo q necesitamos mas info para ayudarte en esta...
----Que tipo de coneccion tienes?
----que version de Firefox usas?
----cuanto ram tiene tu PC?

i have DSL 2mb/512

latest firefox version 2.0.0.3

pc ram is 1gb

---

