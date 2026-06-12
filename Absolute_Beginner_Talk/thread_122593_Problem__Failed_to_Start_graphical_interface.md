---
title: "Problem:  Failed to Start graphical interface"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Enzo on 2006-01-28
I've just installed ubuntu on my new dell e510.
I've never used ubuntu before and hear good things about it so i wanted to try it out.  I ordered the dell ready for open source so nothing was done to hard drive.  I installed ubuntu and everything seemed to go fine but then right before it would boot up it pops up with 

Failed to start the X server (your graphical interface)  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

Has anyone seen this before?  IS the problem due to my video card? 

Any help would gladly be appreicated...

---

### Post by Perfect Storm on 2006-01-28
Hi.

Try with this:

sudo dpkg-reconfigure xserver-xorg

---

### Post by alamba on 2006-01-28
Incase that does'nt work, let us know your video card model incase you know it. Else log in via console and navigate to /etc/X11/xorg.conf change driver of your video card to "vesa". 

Akshay

---

### Post by Enzo on 2006-01-28
thanks for the quick reply guys...

I just tried that code and reconfigured xserver
 
At the end i got the following error

xerver-xorg postinst warning:  overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf .200601280220

---

### Post by Enzo on 2006-01-28
the video card im using is 
Ati x300 128mb

---

### Post by alamba on 2006-01-28
Use google to find linux drivers for it. Meanwhile try the vesa thingy too. It should atleast get you up and running.

Akshay

---

### Post by Enzo on 2006-01-28
ok thanks...  How do i go to /etc/x11 folder?

What's the command for that?
I'm new to this as you can tell...
Not new to computers though...

---

### Post by alamba on 2006-01-28
Log into console with your username and password, then:

1. cd /etc/X11
2. vi xorg.conf
3. Scroll down to the section called "Device"
4. In front of Drivers would be a word (maybe in ""). Change that word to vesa. 

Also post what word is in it currently. Might be ati.

Akshay

---

### Post by Enzo on 2006-01-28
reading further at the bottom of the error it states..

(EE) No devices detected

Fatal Server error:
no screens found.

Could the problem be my flat screen monitor?
sounds like it's not detecting it...

---

### Post by alamba on 2006-01-28
Could be. But you need to post a couple of lines more of the error...which section does it say no devices detected, the monitor ones of the modes one.

Akshay

---

### Post by Enzo on 2006-01-28
Okay..

so following your commands i got:

in the device section:

identifier.........  "ATI Technologies, Inc. Radeon X300 SE(RV370)
driver.....          "ati"

in the monitor section:

identifier.....     "Dell E176FP"
Option....      "DPMS"


BTW... How do i exit this screen?

---

### Post by alamba on 2006-01-28
hmm...the driver seems to be right. Change to vesa and see if it works. If not, can you post your xorg.conf and the complete error message? I could then try to locate the section of the xorg that's causing the error.

Akshay

---

### Post by Enzo on 2006-01-28
**[COLOR="Red"]These are the errors...[/COLOR]**

(==) Using config file:  "/etc/X11/xorg.conf"

Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":
  No symbols found
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":
  No symbols found
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":
  No symbols found
(EE) No devices detected...

Fatal server error:


**[COLOR="Red"]Then this is the detailed error:[/COLOR]**

(**) :--> Screen "Default Layout"
(**) :-->Monitor "Dell E176FP"
(**) :-->Device "ATI Technogolies, Inc Radeon .....
(**) :-->Input Device "Generic Keyboard"
(**) :-->Input Device "Configured Mouse"

(WW) the directory " /usr/share/X11/fonts/cyillic" does not exist
                   Entry deleted from font path
(WW) The directory "/usr/share/X11/fonts/CID"  does not exist
                   Entry deleted from font path

(WW) 'fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

(run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID).
(**) Font Path set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:.........
(==)rbgpath set to "/usr/X11r6/lib/X11/rgb"
(==)ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APm failed (/dev/apm_bios) 
No such file or directory


(WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected!

(EE) No devices detected.
Fatal server error
no screens found.


I guess it's not detecting the video card...
as well as i few other warnings..

---

### Post by alamba on 2006-01-28
[QUOTE=Enzo]**[COLOR="Red"]These are the errors...[/COLOR]**
(WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected![/QUOTE]

Did you do try changing ati to vesa and rebooting?

Akshay

---

### Post by Enzo on 2006-01-28
YES and it worked!!!!

what do i do now? 
Do i attempt to get it to work with ati drivers?
why didn't it work before with ati drivers?

also how about the other warnings?  Should i worry about them?

---

### Post by alamba on 2006-01-28
glad u're up and running atleast. Be aware of this...vesa is just a generic driver so while u're up and running it would be best to find a driver for your hardware that works for you. I believe there would be considerable video performance enhancement too.

Search around google for updated drivers for your chipset. (Maybe ati website has some) Compile them and see if they work for you.

As for the other errors, I'd suggest you open a new thread by posting the errors you're getting at this point (some would have gone since your X11 is up now). I'm not sure how critical some of them are.

Akshay

---

### Post by Enzo on 2006-01-28
thanks alot for your help...

i'll be posting in the future with more questions, right now i'm learning linux and so far i really like it..  I can't wait to completely switch over to this and forget windows forever...\\:D/ \\:D/ \\:D/

---

### Post by alamba on 2006-01-28
u're welcome...drop in here with your problems and u'll generally find someone who'll be able to help you out. And don't forget to post answers to solutions u're aware off.

Akshay

---

### Post by aceron on 2006-01-30
haveing same problem.....and i do think its the monitor

---

