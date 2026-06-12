---
title: "Fluxbox theme info script"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by semperfiguy on 2007-11-21
You know how some screenshots have a terminal displaying the system information and then the GTK theme, What font it is, What window manager it is etc...  Is it possible to write a script like that for fluxbox?  So like:

WM:          Fluxbox 1.0.rc3
GTK:         CleanBlue
Fluxbox theme:      NovaBlue

I am trying to do something like this just to experiment with scripting.  So I guess my questions are is it possible and What file is the fluxbox theme declared in?

---

### Post by ticopelp on 2007-11-21
I could be wrong, but I think the theme is declared in ~/fluxbox.rc.

---

### Post by RedSquirrel on 2007-11-21
> **semperfiguy said:**
> So I guess my questions are is it possible 

Yes.

> **semperfiguy said:**
> What file is the fluxbox theme declared in?

It's in ~/.fluxbox/init:

```
session.styleFile:            *your-theme*
```

---

### Post by semperfiguy on 2007-11-21
Allright thankyou.. So I can get the theme with the code
```
echo "WM Theme:          `grep "styleFile" ~/.fluxbox/init | cut -c 54-100`"
```
Where is the WM declared? what file?  And then gtk? would I just look in my .gtkrc-2.0 file?

Edit:  Ok I know I can get the gtk theme name from the .gtkrc-2.0 file, but how do I cut out just that section?  it goes /usr/share/theme/THEMENAME/gtkrc/gtkrc-2.0 in the file, but how do I cut out just the theme name part?

---

### Post by semperfiguy on 2007-11-22
This is what I have so far:

```
#!/bin/bash
##### 
##### Info/Screenshot script to be run
##### in a terminal to display theme info then 
##### output a screenshot.
#####

# Screenshot Directory
sdir="$home/Desktop/screens"

# Screenshot Name
screen=`date +%m_%d_%y`.png

clear
echo 
echo "LINUX"
echo -----------------------------------------------------------------
echo "Kernel:		`uname -r`"
. /etc/lsb-release 
echo "Distro:		$DISTRIB_ID $DISTRIB_RELEASE $DISTRIB_CODENAME"
echo "Uptime:         `uptime |cut --delimiter=" " -f 2`"
echo
echo "CPU"
echo -----------------------------------------------------------------
echo "CPU:		`grep "model name" /proc/cpuinfo | cut --delimiter=":" -f 2`"
echo "Speed:		`grep "cpu MHz" /proc/cpuinfo | cut --delimiter=":" -f 2` mhz"
let memtotal=`grep "MemTotal" /proc/meminfo | cut -c 12-22 | indent -i0`/1024
let memfree=`grep "MemFree" /proc/meminfo | cut -c 12-22 | indent -i0`/1024
let memcache=`grep "Cached" /proc/meminfo | cut -c 12-22 | indent -i0`
let memcache=$memcache/1024
let memfreetotal=$memfree+$memcache
let memused=$memtotal-$memfreetotal
echo "Memory Used:	 $memused mb"
echo "Memory Free:	 $memfreetotal mb"
echo "Memory Total:	 $memtotal mb"
echo
echo "THEME DETAILS"
echo -----------------------------------------------------------------
echo "WM:		 "
echo "WM Theme:		 `grep "styleFile" ~/.fluxbox/init | cut -c 54-100`"
echo "GTK Theme:	 "
##sleep 4
##scrot '%m_%d_%y-$wx$h.png' -e 'mv $f ~/Desktop/screens'
exit 0
```

[ATTACH]51064[/ATTACH]

---

### Post by RedSquirrel on 2007-11-23
> **semperfiguy said:**
> Edit:  Ok I know I can get the gtk theme name from the .gtkrc-2.0 file, but how do I cut out just that section?  it goes /usr/share/theme/THEMENAME/gtkrc/gtkrc-2.0 in the file, but how do I cut out just the theme name part?

A simple way would use cut. Something like the following should work:

```
grep theme .gtkrc-2.0 | cut -d "/" -f 5
```

---

### Post by semperfiguy on 2007-11-23
That worked, but how? I tried man cut but that doesn't give any details about the funcions.  Could you elaborate alittle about how cut works?

---

### Post by RedSquirrel on 2007-11-24
> **semperfiguy said:**
> That worked, but how? I tried man cut but that doesn't give any details about the funcions.  Could you elaborate alittle about how cut works?

The '-d "/"' tells cut to divide the input by the "/" character.

The '-f 5' tells cut to output the fifth field.

Example:

**include "/usr/share/themes/Industrial/gtk-2.0/gtkrc"**

```
grep theme .gtkrc-2.0 | cut -d "/" -f 1
```

Output:
[B]include "

[/B]```
grep theme .gtkrc-2.0 | cut -d "/" -f 2
```

Output:
[B]usr
[/B]
... and so on. ;)

---

### Post by semperfiguy on 2007-11-24
Oh now I get it, thank you.  I can finish the script for fluxbox now.  The only thing I want to try to add eventually is WM detection.  I saw one script that scans the ps list for WM names, but I think if it is declared in a file somewhere that would be a bit easier.  Thank you for your help.

---

### Post by RedSquirrel on 2007-11-24
Scanning the ps output would be OK. If it turns out you're running fluxbox, you can get the version with either 'fluxbox -v' or 'fluxbox -i' depending on how much detail you want.

---

### Post by semperfiguy on 2007-11-24
It would work but the example I have is written in perl, and I think its a little to advanced for me to figure out right now.  Is there a file that the WM or DE is selected in? I figure there must be for GDM to know which WM to start.

---

### Post by RedSquirrel on 2007-11-27
> **semperfiguy said:**
> It would work but the example I have is written in perl, and I think its a little to advanced for me to figure out right now. Is there a file that the WM or DE is selected in? I figure there must be for GDM to know which WM to start.

Often, gdm simply reads the settings in the *.desktop files located in /usr/share/xsessions. For example, when you select Fluxbox from the login screen, gdm would know to look in /usr/share/xsessions/fluxbox.desktop. I'm not sure if there's a file that would tell you which WM/DE you selected when you logged in. I don't use gdm anymore so I can't check. If you find such a file or setting, please post. 

There might be a setting that tells gdm what your default WM/DE is, but then you might not always run your default.

---

### Post by yabbadabbadont on 2007-11-27
~/.dmrc I think holds the last selected gdm session.  However, if the user doesn't use gdm (neither RedSquirrel nor myself do), then that doesn't help much.  You might also look for ~/.xinitrc, ~/.xsession (or is it ~/.Xsession?) and see if you can parse out the window manager from there.

---

