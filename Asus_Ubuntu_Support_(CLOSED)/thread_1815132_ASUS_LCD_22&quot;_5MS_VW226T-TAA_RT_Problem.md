---
title: "ASUS LCD 22&quot; 5MS VW226T-TAA RT Problem"
date: 2011-07-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dscarfogliero on 2011-07-30
I was trying to update my xorg.conf file to update my screen resolutions. I thought I did it right so I saved everything and now ubuntu will not boot. Please help!

---

### Post by gordintoronto on 2011-07-30
What version of Ubuntu? What computer?

Perhaps the easiest way to continue is to boot from a LiveCD and rename xorg.conf.

---

### Post by dscarfogliero on 2011-08-15
How do I edit this file to include 1680x1050 resolution?


Section "Device"
Identifier	"Configured Video Device"
Driver	 "fbdev"
EndSection

Section "Monitor"
Identifier	"Configured Monitor"
EndSection

Section "Screen"
Identifier	"Default Screen"
Monitor	 "Configured Monitor"
Device	 "Configured Video Device"
EndSection


Thanks!

---

### Post by Arny006 on 2011-08-16
Hi,
don't bot at all or you come in to command-line that ask you for user and password?
If the system ask you for user or password execute following commands:

user name$ [**insert user name**]
password$ [**insert password**]

# restore  xorg.config:
**sudo cp /etc/X11/xorg.config.backup /etc/X11/xorg.config**

# now you have the old "xorg.config with smaller resolution and we want start the normal desktop:

**sudo /etc//init.d/gdm restart**
# or
**sudo restart gdm**

# now if you have a NVIDIA grafic-card execute following:
**sudo nvidia.settings**
# or
**gksudo nvidia.settings**

# NOTE: for ATI grafic-card you should insert the correlated command.
# now in the second line of the first screen you can read "**X Server Dispay Configuration**" click on it. You can see on the right-bottom-side the possibility to change the resolution and the frequency.
# NOTE: you cannot acces the frequency if you don't change the resolution. Also modify firt the wished resolution and than the frequancy. When you are finish press first "**[COLOR=Black]Apply[/COLOR]**" and than "**Save to X Configuration File**".
# now restart again the "**X Server" with**":

**sudo /etc//init.d/gdm restart**
# or
**sudo restart gdm**

# Now you should have the wished resolution. Enjoy

---

