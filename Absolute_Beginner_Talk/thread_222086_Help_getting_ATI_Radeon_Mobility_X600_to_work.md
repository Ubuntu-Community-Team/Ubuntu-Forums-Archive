---
title: "Help getting ATI Radeon Mobility X600 to work"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by cptvitamin on 2006-07-24
I have been trying to fix my display problem for days.  It seems like the problems I am having are common with the ATI line of video cards (resolution is poor, no OpenGL or 3D support, etc).  I have followed both Methods listed here: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Both produced no errors. However, whenever I run flgrxinfo, I get:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Any help would be appreciated.

---

### Post by Paerez on 2006-07-24
fglrx is a pain to get running. I can try to help you through the fglrx, or you can just go with opengl 3d with good resolution through the open source radeon driver. I do this on my laptop because its much easier and requires less maintenance. I get good 3d performance, but fglrx is a bit better.

whats your choice?

---

### Post by cptvitamin on 2006-07-24
I'd be happy going with the open source radeon driver option.  Will I be able to use Xgl and Compiz with this solution?

---

### Post by ovimunt on 2006-07-24
Hi,

The problem is probably exactly the fact that you followed BOTH methods. I would assume that one didn't work and then you tried the other. This however has probably messed up everything further.

A good start would be to try and remove all ATI drivers what so ever. By doing this you might loose all graphic display first and you'll have to do everything in text mode. Yet, I had some problems myself  but this worked very well for me.

Please let me know if you'd like to go down this route before I start writing pages of help.

---

### Post by Paerez on 2006-07-24
it just so happens I wrote a howto for running xgl and compiz with the radeon driver on mobility cards:
[http://www.ubuntuforums.org/showthread.php?t=219336](http://www.ubuntuforums.org/showthread.php?t=219336)

---

### Post by cptvitamin on 2006-07-24
Paerez, everything in stage 1 went just fine until I checked glxinfo and it said that direct rendering was still a no...

---

### Post by Paerez on 2006-07-24
did you make sure to uninstall fglrx and RE install libgl-mesa[-dri]? Both those packages have their own /usr/lib/libGL.so.1.2, so you have to remove fglrx's and put mesa's back in, which has the radeon.

---

### Post by cptvitamin on 2006-07-24
When I attempt to uninstall fglrx I get this:
The following packages are BROKEN:
  fglrx-control
The following packages will be REMOVED:
  xorg-driver-fglrx
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 26.8MB will be freed.
The following packages have unmet dependencies:
  fglrx-control: Depends: xorg-driver-fglrx but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
xorg-driver-fglrx [8.26.18-1 (now) -> 7.0.0-8.25.18+2.6.15.11-3
(dapper-security)]

Score is -39

Accept this solution? [Y/n/q/?]

---

### Post by Paerez on 2006-07-24
ok just remove both:
```
sudo aptitude remove xorg-driver-fglrx fglrx-control
```
then reinstal the mesas.

---

### Post by cptvitamin on 2006-07-24
Ok, those are gone.  When I re-install mesa, it says:
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Also should note one another anomaly.  After sudo rmmod fglrx It says:
ERROR: Module fglrx does not exist in /proc/modules


Sorry this is so messed up ...

---

### Post by Paerez on 2006-07-24
ok you have to say:
```
sudo apt-get --reinstall install
```
followed by the packages to get them to reinstall.

The error just means fglrx wasn't loaded, so it didn't need to be removed.

---

### Post by cptvitamin on 2006-07-24
Thought some of this might be helpful:
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: ATI
client glx version string: 1.3
GLX version: 1.2
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by Paerez on 2006-07-24
that will be helpful only as a "yes it worked" because it will say direct rendering: Yes.

---

### Post by cptvitamin on 2006-07-24
I now have craptastic 1024x768, but i still get direct rendering: no.  I think the problem is in my xorg.conf.  There were duplicate sections for Display and Screen.  One with generic info, the other with detailed (and correct) info.  for example:
Section "Device"
	Identifier  "aticonfig-Device[0]

VS

Section "Device"
	Identifier  "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"

I tried commenting out corresponding pairs but to no avail.  Each time I get direct rendering: no.

At least I can still run xserver and gnome...

---

### Post by Paerez on 2006-07-24
try running:
```
sudo dpkg-reconfigure xserver-xorg
```
you can pretty much hit enter through the whole thing. Then apply my xorg changes from the howto.

---

### Post by cptvitamin on 2006-07-25
wlan0 is totally gone now, but I don't think that has anything to do with resetting my xorg...  anyway, regarding the xorg changes in the howto:
I changed the driver to from ati to radeon.
I commented out all the resolution stuff that was there and replaced it with:
SubSection "Display"
	Depth		24
	Modes		"1024x768" "800x600" "640x480"
EndSubSection
(This messes my disply BTW since my laptop is widescreen, so I added 1280 x 800)
DO I have to add this at the end of the file:
Section "Extensions"
	Option "Composite" "Enable"
EndSection

AND 

Do I have to add anything to SEction Module?  This is what is there now:
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Thanks again for all your help.

---

### Post by Paerez on 2006-07-25
The Module section is fine, and you only need the Extensions section if you want Compiz on XGL.

---

### Post by cptvitamin on 2006-07-25
I'm still getting a No on direct rendering ...  The only thing I can think of is that while trying to install the right drivers for flgrx yesterday, I followed this instruction in one of the HOWTO's:

... This may be fixed by replacing /usr/lib/libGL.so.1.2 with alibGL.so.1.2 from the previous driver version (8.24.8). To do this download this file: [[http://files.covertprestige.info/important/libGL.so.1.2]](http://files.covertprestige.info/important/libGL.so.1.2]) and then copy it to the /usr/lib/ directory. ...

I may have the wrong libGL, but wouldn't that have been overwritten when I reinstalled the mesa drivers?

I'm completely frustrated everytime I see direct redering: No

---

### Post by Paerez on 2006-07-25
try:
```
sudo rm /usr/lib/libGL.so.1.2
sudo aptitude --reinstall intstall libgl1-mesa libgl1-mesa-dri
ls -l /usr/lib/libGL*
```

---

### Post by cptvitamin on 2006-07-25
Interesting...
after removing libGL.so.1.2 and reinstalling the mesa drivers, ls -l  /usr/lib/libGL* returns:

lrwxrwxrwx 1 root root     16 2006-07-03 13:04 /usr/lib/libGLEW.so.1.3 -> libGLEW.so.1.3.1
-rw-r--r-- 1 root root 205204 2005-11-30 15:47 /usr/lib/libGLEW.so.1.3.1
lrwxrwxrwx 1 root root     20 2006-07-24 14:58 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.060500
-rw-r--r-- 1 root root 483308 2006-06-28 15:21 /usr/lib/libGLU.so.1.3.060500

now, glxinfo returns:

glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

---

### Post by Paerez on 2006-07-25
ok do this:
```
sudo aptitude install apt-file
sudo apt-file search /usr/lib/libGL.so.1.2
```

---

### Post by cptvitamin on 2006-07-25
First of all, you should be commended for your patience and tenancity (thank you).  I wish we could figure out what the problem is...

apt-file search returns nothing
glxinfo still returns error

---

### Post by Paerez on 2006-07-25
ok, try it with just:
sudo apt-file search /usr/lib/libGL.so.1

---

### Post by cptvitamin on 2006-07-25
I had already tried that with the same result (nothing) :(

---

### Post by Paerez on 2006-07-25
darn. OK I am at work right now and I am gonna take my lunch break, but I am going to leave a note to myself to post my libGL.so.1.2 to this thread so you can download mine (from wherever the expletive it came from) and pop it in.

---

### Post by arkangel on 2006-07-25
Hi  i have an ati X700  and i tried all what is written  about that fglrx  in ubuntu 6.06 

Finally I downloaded the drivers from Ati 
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

and i  running  directly you know 

# chmod +a  ati_driver_.run
# sudo ./ati_driver_.run 

and  worked  perflectly , i udpated the kernel twice  i am using xgl  and since then  worked  well 

have you tried that way?

---

### Post by Paerez on 2006-07-25
here is my libGL.so.1.2

---

### Post by cptvitamin on 2006-07-26
I replaced the **libGL.so.1.2** and that didn't help any.  sudo apt-file search /usr/lib/libGL.so.1.2 still returned nothing.  Then I tried the ATI installer that arkangel recommended.  That didn't help any.  The installer went without a hitch, but direct rendering is still a no, and glxinfo now includes "Xlib:  extension "XFree86-DRI" missing on display ":0.0".
" I think this is hopeless.  I better stop before I really screw something up.  I already have to figure out where my wlan0 went...

---

### Post by Paerez on 2006-07-26
ok. Sorry it didn't work out for you. Good luck on your wireless.

---

### Post by Paerez on 2006-07-27
ok I figured out what may be going wrong. When you run "--reinstall" it doesn't actually overwrite the stuff in /usr/lib. I had to go into aptitude (or synaptic) and force mesa back to 6.4 and downgrade it. Then upgrade it back to 6.5 for my libGL to be correct.

---

### Post by cptvitamin on 2006-07-27
when I try to downgrade mesa to 6.4, it wants to remove ubuntu-desktop and x-window-system-core.  Should I do this?

---

### Post by Paerez on 2006-07-27
no. I think you need to use aptitude to downgrade, since synaptic is not as smart as aptitude.

---

