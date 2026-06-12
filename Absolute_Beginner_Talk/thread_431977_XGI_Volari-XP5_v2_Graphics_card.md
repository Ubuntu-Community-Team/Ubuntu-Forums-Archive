---
title: "XGI Volari-XP5 v2 Graphics card"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by cage27 on 2007-05-03
How do I set the driver in xorg.conf file to “vesa,” or anyother driver that will work with XGI Volari-XP5 v2 Graphics card:confused:

---

### Post by Seisen on 2007-05-03
To set xorg.conf file to vesa you do this in the terminal

```
gksudo gedit /etc/X11/xorg.conf 
``` Just follow the same directions except you don't need to press the shift keys and all that. Then save the file and reboot. If you can't access Gedit then try this.

```
sudo vim /etc/X11/xorg.conf
``` this will open up the xorg.conf file. Next you need scroll down till you get to here

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps" "true"

``` then you need to press shift+I and it should say insert. Go to where it says Driver  ""
change whatever is in the quotation marks to vesa. Then press the shift +Q and it should say this

```
Entering Ex mode.  Type "visual" to go to Normal mode.
:

``` right after the colon enter 
```
wq
``` this will write the file and quit vim. Then reboot and it should work now.

---

### Post by Seisen on 2007-05-03
I also looked and unfortunately I don't see any linux drivers for your graphics card at the current time.

---

### Post by cage27 on 2007-05-03
Thanx I'll give it a try. report back soon

---

### Post by cage27 on 2007-05-03
**sudo vim /etc/X11/xorg.conf** worked,
but "vesa" was already the driver. Are there any alternative drivers that will work with ubuntu6.10 , My ubuntu 6.06 was working fine untill I upgraded. now the screen goes blank after splash load up screen.
How can I revert back to the driver that was on 6.06?

---

### Post by cage27 on 2007-05-03
a selection of vidio drivers came up during reconfig:
[B]sis
sisusb
tdfx
tga
trident
tseng
vesa
vga
via
vmware
voodoo.
[/B]
I tryed the vmware, it didn't work but i can now get into xorg.config with nano.
any sugesgens which driver to use before i start the proses of elimination.

---

### Post by Seisen on 2007-05-03
Try the vga one, if that doesn't work its back to the drawing board.

---

### Post by cage27 on 2007-05-04
Have so far tryed
[B]sis
vga
vmware
vesa
trident[/B]
no luck yet, however I have found some more info about XGI Volari-XP5 v2 and Linux
**[www.linuxquestions.org/questions/showthread.php?t=248394](www.linuxquestions.org/questions/showthread.php?t=248394)**
and
**[www.webspawner.com/users/dell5160/index.html](www.webspawner.com/users/dell5160/index.html)**

---

