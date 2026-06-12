---
title: "Command Line Help Please - X Windows down"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by roxics on 2006-06-30
I was messing around with the xorg conf file for the monitor and screwed something up. When I restarted X it wouldn't restart. So I have to go into recovery mode. But I don't know how to run linux off the command line. I've memorized a couple of commands, one of which is "startx" and I get returned with a list of text that tells me: 
> 
there is a parse error on line 103 of /etc/X11/xorg.conf of section "Monitor"

1400x900 is not a valid keyword in this second


I need to recomment out that entire line 

Right now it looks like this
> 
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
[COLOR="Red"] 	 DisplaySize	370	277	    1400x900 96dpi[/COLOR]
#	DisplaySize	423	370	# 1600x1400 96dpi


It needs to look like this

> 
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
[COLOR="Red"]#	DisplaySize	370	277	# 1400x1050 96dpi[/COLOR]
#	DisplaySize	423	370	# 1600x1400 96dpi


How do I do this from a command line so X will start up properly again?

---

### Post by CarpKing on 2006-06-30
type: 
```
nano /etc/X11/xorg.conf
```

I don't know how to work nano, but it is the command-line text editor for ubuntu (i think kubuntu has pico?)

---

### Post by nemtudod on 2006-06-30
sudo apt-get install mc

sudo mc

go to /etc/X11 and edit xorg.conf

---

### Post by croak77 on 2006-06-30
[QUOTE=roxics]
How do I do this from a command line so X will start up properly again?[/QUOTE]

Like Carpking said, use nano. It's installed by default.
```
sudo nano -w /etc/X11/xorg.conf
```

Edit xorg.conf. Save with Ctrl-X.

---

### Post by roxics on 2006-06-30
I'll try that. But I just realized I do have a backup of that file if that would make it any quicker to restore.

---

### Post by woedend on 2006-06-30
sudo vi /etc/X11/xorg.conf

use arrow to scroll to to section.  Push inset key once(this allows you to start typing).  Put your # in place.  Push escape once.  Now type ":wq" or :x and push enter.
if you have a backup, use the cp command
sudo cp source destination
for example
sudo cp /etc/X11/xorg.backup /etc/X11/xorg.conf

---

### Post by roxics on 2006-06-30
Thank you everyone. I got it back up and runing from the backup file.

---

