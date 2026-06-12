---
title: "Serial Mouse--Assistance for Noob with Disability"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by wintermute2_0 on 2006-09-17
Hello.  I just tried running the Ubuntu Desktop Live CD and it wouldn't recognize my serial mouse.  I use a type of head mouse that plugs into the serial port (I have a physical disability) and I can't use the computer at all if it isn't recognized.  It recognized the USB mouse fine, but that doesn't do me much good.  

I really would like to learn Linux, but I'm reluctant to install it if it won't work with my adaptive hardware.  Is there any way to get the Live CD to recognize a serial mouse?  I really appreciate any assistance you can offer.  Thanks.  

Mark
[www.the19thfloor.net]("http://www.the19thfloor.net/")

---

### Post by rccharles on 2006-09-18
> **wintermute2_0 said:**
> Hello.  I just tried running the Ubuntu Desktop Live CD and it wouldn't recognize my serial mouse.  I use a type of head mouse that plugs into the serial port (I have a physical disability) and I can't use the computer at all if it isn't recognized.  It recognized the USB mouse fine, but that doesn't do me much good.  



You might try a serial to usb converter.  You need one eventually since new computers are dropping serial ports in favor of usb.

This query should find them on ebay:
  		
USB to PS/2 PS2 Port KB Mouse Converter Adapter Y-Cable

I offer this a suggestion because I am not knowledgeable about configuring serial ports.

Robert

---

### Post by bodhi.zazen on 2006-09-18
You will need to edit xorg.conf.

In a terminal type```
sudo cp /etc/X11/xorg.conf /etc/Xzz/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf
```

This will back up xorg.conf and open the file for editing.

The file is overwhelming at first, but you are looking to edit the input device section for your mouse to look like something this:
> Section "InputDevice"
	Identifier	"Mouse1"
	Driver		"mouse"
[b]Option "Device" "/dev/ttyS0"
Option "Protocol" "Microsoft"[/b]
	Option		"CorePointer"
	Option		"Protocol" "ExplorerPS/2"
	Option		"Emulate3Buttons" "False"
	Option		"Buttons" "7"
	Option		"ZAxisMapping" "4 5 6 7"

**[size=2]My xorg.conf will be different from yours. Edit ONLY the 2 lines I bolded. DO NOT CUT AND PASTE THE ENTIRE SECTION.[/size]**

---

### Post by halitech on 2007-01-21
thanks you, had the same problem where my serial mouse wasn't being seen. replaying to say thanks and so I know what to do the next time :)

---

### Post by Shinoda on 2007-11-03
> **bodhi.zazen said:**
> 
```
sudo gedit /etc/X11/xorg.conf
```
[FONT=Courier New]gksudo[/FONT] is recommended for graphical apps.

---

