---
title: "Blender doesn't run"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by josefcarel on 2006-10-14
I have Blender installed and was running well but some mistake I did and now it doesn't run. From the Shell windows I get te following message:
Using Python version 2.4
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window

What is the error and what to do to fix this?

Thanks a lot
Josef ](*,)

---

### Post by anders_gud on 2006-10-14
> **josefcarel said:**
> 
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window

What is the error and what to do to fix this?

Thanks a lot
Josef ](*,)

It looks like you are trying to run a dynamic build of Blender on a system without hardware OpenGl acceleration. 

Check if your /etc/X11/xorg.conf has these sections enabled 
...
 Load    "dri"
 Load    "glx"
...

---

### Post by josefcarel on 2006-10-14
Yes, it is writen in the file xorg.config as follow:

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	[COLOR="Red"]Load	"dri"[/COLOR]
	Load	"extmod"
	Load	"freetype"
	[COLOR="Red"]Load	"glx"[/COLOR]
	Load	"int10"
	Load	"type1"
	Load	"vbe"
 
Maybe in an other place?
Thanks
Josef

---

### Post by josefcarel on 2006-10-14
> **anders_gud said:**
> It looks like you are trying to run a dynamic build of Blender on a system without hardware OpenGl acceleration. 

Check if your /etc/X11/xorg.conf has these sections enabled 
...
 Load    "dri"
 Load    "glx"
...
Yes, sections are enabled as I wtote in my replay! 
What can i do ?

---

