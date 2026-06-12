---
title: "Integrated Video Card"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Trzone on 2007-09-23
Hi, i have an Hp Pavilion 521 N running Feisty Fawn and here's what i get when i use  glxinfo | grep rendering


theo@Ubuntu:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by w4ett on 2007-09-23
What video chipset have you got....from the terminal:
```

lspci
```

and post the results.

---

### Post by Trzone on 2007-09-23
Here's the output.. any help would be great! 

00:00.0 Host bridge: VIA Technologies, Inc. VT8361 [KLE133] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0d.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)

---

### Post by w4ett on 2007-09-23
As far as I know the trident driver is only 2D, 

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)

How is your 2d performance?

---

### Post by Trzone on 2007-09-23
I can play movies, etc a lot better than in windows, im not looking to go into 3d kind of stuff

it's just that i've had that error message when i've done glxinfo | grep rendering and i dont know what i did to make it show all those errors...

---

### Post by w4ett on 2007-09-23
in the terminal type:

```
cat /etc/X11/xorg.conf
```

and let's see what driver you have installed.

---

### Post by Trzone on 2007-09-23
Here it is.

---

### Post by w4ett on 2007-09-23
You might try adding this to the end of your xorg.conf:

> Section "Extensions"
Option "Composite" "Disable"
EndSection


---

### Post by Trzone on 2007-09-23
I added those lines to the end.. i attached the new file

I still get 
theo@Ubuntu:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by w4ett on 2007-09-23
Well,  the error status of the GLX module not loading indicates that the 3d is not working however, since you are not trying to use any 3d applications (video is 2d)....it's not really an issue.  

I did some searching with the following results:

[http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=Xlib%3A+extension+%22GLX%22+missing+on+display+%22%3A0.0%22+trident#779](http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=Xlib%3A+extension+%22GLX%22+missing+on+display+%22%3A0.0%22+trident#779) 

So, we know the trident diver is not 3d capable, and since your desktop responds ok, and it looks like your xorg.conf is properly built, so I would say that unless there is a new driver released for that chipset, there is nothing that can be done apart from removing the glx module...which probably won't give your any gain in video performance.

---

### Post by Trzone on 2007-09-23
Thanks a lot!
Video plays good in ubuntu considering my 5 year old computer.. well it plays better than in windows weirdly enough.
im sure this computer will die one day and i'll just have to get a new one.
...with ubuntu on it

---

