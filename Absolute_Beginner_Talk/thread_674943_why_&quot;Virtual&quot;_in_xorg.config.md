---
title: "why &quot;Virtual&quot; in xorg.config?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by OAP on 2008-01-22
trying to set res. to monitor recommended 1440x900@60 but no matter what res. i set xorg uses Virtual xxxx    xxxx (see below)
running 7.10 on Inspiron 530, Targa LCD 19-4  Widescreen.
Can anyone explain Virtual and would it have anything to do with wobbling windows when opening and closing

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Integrated Graphics Controller"
	Monitor		"LCD 19-4 Wid"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1280x854"	"1280x768@60"	"1152x768@54"	"1280x720@60"	"800x600@60"	"1280x800@75"	"800x600@85"	"1280x768@75"	"800x600@75"	"1280x720@50"	"800x600@72"	"1280x800@60"	"800x600@56"	"1440x900@75"	"720x400@85"	"1440x900@60"	"640x350@85"	"1600x1024@60"	"640x400@85"	"1680x1050@60"
	EndSubSection

---

### Post by tophcito on 2008-01-22
Hello!

You can use ```
man xorg.conf
```  to access the man page of the X.org config file. There all the options that can be set are described in detail.

From the xorg.conf man page:
```

 Virtual  xdim ydim
              This optional entry specifies the virtual screen  resolution  to
              be  used.   xdim  must  be a multiple of either 8 or 16 for most
              drivers, and a multiple of 32 when running in  monochrome  mode.
              The  given  value  will be rounded down if this is not the case.
              Video modes which are too large for the specified  virtual  size
              will  be  rejected.   If  this entry is not present, the virtual
              screen resolution will be set to accommodate all the valid video
              modes  given in the Modes entry.  Some drivers/hardware combina&#8208;
              tions do not support virtual screens.  Refer to the  appropriate
              driver-specific documentation for details.

```

I am not quite sure of this, but i think this means that your Desktop will be actually larger than what fits on your screen. By some means then you can determin which part of your Desktop is presented by your screen.

(2) I dont think that this has to do anything with wobbling windows. I believe they are rather related to the Compiz Visual Effects manager. You could use System -> Preferences -> Appearence to change how many effects there actually are. 

cheers.

---

