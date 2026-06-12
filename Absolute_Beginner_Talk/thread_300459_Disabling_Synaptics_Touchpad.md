---
title: "Disabling Synaptics Touchpad"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by speedwell68 on 2006-11-15
Hi, I'm a complete Linux virgin.  I have got a ACER ASPIRE 5101 and I want to disable the touchpad as I hate the thing.  I'm running Ubuntu 6.10.  I'm using a USB mouse and I keep dragging my hand over the touchpad as I type.  Anyone know how?  I've tried editing xorg.conf but I can't save it.

---

### Post by subluid on 2006-11-15
i am not sure, if there is a better way, but editing xorg.conf seems a good idea.

my only idea why you cant save it, is that you are not root/superior user so you don't have write-permissions outside your user-folder in the home-directory

in this case, try entering 'sudo gedit /etc/X11/xorg.conf' in a terminal, edit and save.

good luck anyway

---

### Post by ThrobbingBrain66 on 2006-11-15
see if this works for you

[http://www.ubuntuforums.org/showpost.php?p=732874&postcount=7](http://www.ubuntuforums.org/showpost.php?p=732874&postcount=7)

---

### Post by speedwell68 on 2006-11-16
That is cool I understand that.  My problem is this, I type sudo gedit /etc/x11/xorg.conf it opens a blank document.  I at a loss to explain why, there must be something else I'm doing wrong.

---

### Post by Bachstelze on 2006-11-16
It's **X**11, with a capital X. Filenames in Linux/*NIX are case-sensitive, and please use **gksudo** instead of sudo. But can't you just disable it in your BIOS ? I have this option on my Asus.

---

### Post by george29 on 2006-11-16
are you typing 

> sudo gedit /etc/x11/xorg.conf 

if so you should change it to 
> 
sudo gedit /etc/**X11**/xorg.conf

---

### Post by localuser on 2006-11-16
There's also a package called qsynaptics that I use.

---

### Post by speedwell68 on 2006-11-16
Ok, I've edited the xorg.conf file and changed it to this:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "False"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

That didn't work, so I removed the entire section of the file.  That didn't work either.  Does anyone else have any more suggestions as this touchpad is really begining to annoy me.  In Windows I can just turn the thing off with one click of a mouse.  There must be an easy way in Linux?

---

### Post by Bachstelze on 2006-11-16
I repeat, have you searched your BIOS for an option to disable it ? Also, have you restarted X after editing the xorg.conf ?

---

### Post by localuser on 2006-11-16
> **speedwell68 said:**
> Does anyone else have any more suggestions as this touchpad is really begining to annoy me.

Uhhm...There's also a package called qsynaptics that I use.

---

### Post by speedwell68 on 2006-11-16
Yes I restarted the PC after each change I made and no there is no setting within the BIOS to disable the touchpad which is a bit bad on Acer's part as my old Toshiba Satellite had the option to disable the Alps Touchpad.

---

### Post by speedwell68 on 2006-11-16
I've done it, thanks for all your help guys, I used the gsynaptics util in the end.  That was easy to do, once I had worked out how to install it.

---

### Post by localuser on 2006-11-16
> **speedwell68 said:**
> once I had worked out how to install it.

Oops, my bad.  Sorry.  I should have been more clear as to how to install the package rather than just telling you that there was a package.

Glad it worked out.

---

### Post by speedwell68 on 2006-11-16
No worries, I found it in the synaptics package manager, ran it from the terminal screen which produced an error message and told me the changes I had to make to xorg.conf, which I did.  I ran it again and simply turned off the touchpad.  You sowed the seed buddy, for which I am grateful, I just let you seed grow.  Linux is fun, much more hands on than Microsoft.  Thanks again.

---

### Post by localuser on 2006-11-16
> **speedwell68 said:**
> Thanks again.

Glad to help.  If you run into a problem that the changes don't stick after a restart, then you can modify your start-up session with

qsynaptics -r

Howto: Preferences | Sessions | Startup Programs | Add

---

