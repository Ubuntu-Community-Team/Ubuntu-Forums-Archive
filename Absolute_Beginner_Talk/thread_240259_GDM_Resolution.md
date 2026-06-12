---
title: "GDM Resolution"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-08-20
Desktop = 1280 x 1024
GDM Login = No idea (Weird resolution)

GDM Login resolution is different to my desktop, so I searched forum and found how to edit my xorg conf, however GDM refuses to change resolution to 1280 x 1024, here is my xorg after editing it:

Just pasted the Screen section :)



Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R300 ND [Radeon 9700 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by Leonivek on 2006-08-20
I had the same issue and removed all references of higher resolutions that I didn't want.  BUT, I had forgotten to change the Virtual line in xorg.conf:
>    SubSection "Display"
    depth 24
    virtual 2048 1536
    modes (long list here - removed)
  EndSubSection 
I simply changed it to "virtual 1280 1024" and my login screen was fine.  If you don't have that line, maybe try adding it.

---

### Post by Dinerty on 2006-08-21
> **Leonivek said:**
> I had the same issue and removed all references of higher resolutions that I didn't want.  BUT, I had forgotten to change the Virtual line in xorg.conf:
 
I simply changed it to "virtual 1280 1024" and my login screen was fine.  If you don't have that line, maybe try adding it.

Thanks for the tip, it did not work though, I don't know how much more I can edit the xorg conf file I deleted all resolutions which where not needed and added the Virtual line in, yet it won't change :(

EDIT:

Just hit the auto config button on my monitor on GDM screen and it solved it

---

### Post by ewl1217 on 2006-08-21
Did you restart xorg after you edited xorg.conf? The changes wont take effect until you do so.

---

### Post by Dinerty on 2006-08-21
Thanks, already sorted it now, found another thread regarding the same problem, just hit the auto config on my monitor and it immediately resized itself

---

### Post by Leonivek on 2006-08-21
Kewl... that was my next suggestion:  a monitor setting. :)

---

