---
title: "Regarding tablet settings..."
date: 2008-07-07
forum: Art &amp; Design
---

### Post by Waqsione on 2008-07-07
Hi. I'm wondering how other people keep their tablet settings saved up after shutting down the computer. I tried wacomcpl, but it seems to reset every time I turn the computer on. I thought of editing the xorg file but keep getting stuck on setting the buttons (is there a clear, simple manual on what format it should be written in?). I'd appreciate it if anyone can help me on either method.

---

### Post by Xfcn on 2008-07-07
[http://linuxwacom.sourceforge.net/index.php/howto/wacomcpl](http://linuxwacom.sourceforge.net/index.php/howto/wacomcpl) -- Is what all you need to know about wacomcpl. I'm not sure why it doesn't save, though. Mine don't save down, either.

---

### Post by Buzzdee on 2008-07-08
x.org is writable only for root - did you sudo-start that applet?

---

### Post by Waqsione on 2008-07-09
To Xfcn: I've already read that page, actually.
To Buzzdee: I think so.

---

### Post by Xfcn on 2008-07-09
It only writes to a local directory anyway, Buzz. It's ~/ directory as a .hidden file. Anyone should have read/write access. For some reason it's erasing the file after a reboot.

---

### Post by spupy on 2008-07-11
I got my Wacom tablet today, and I haven't restarted. I don't plan on restarting my computer much anyway. 

Apart from the settings that are entered directly into xorg.conf, i used xsetwacom to adjust buttons and such. I have these commands in a txt file. Later I can execute this file as a bash script to restore the settings.

---

### Post by Waqsione on 2008-07-12
spupy: Can you tell me specifically how I can set up the buttons properly with xorg? It's the only thing I'm stuck on even after reading the instructions at the linux wacom site (I can change the other settings with it just fine). Perhaps an example with some explanations?

---

### Post by spupy on 2008-07-13
> **Waqsione said:**
> spupy: Can you tell me specifically how I can set up the buttons properly with xorg? It's the only thing I'm stuck on even after reading the instructions at the linux wacom site (I can change the other settings with it just fine). Perhaps an example with some explanations?

I copy-pasted the xorg.settings from this page:
[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)
The first 3 sections about "eraser", "stylus" and "cursor" **and** the 4th one about the "pad" - for the buttons on the tablet itself. I removed the lines that say "Serial only" or "Tablet PC only". Then I changed the Device they point to to my actual one (you can see which in your current xorg.conf).
You may need not change these if the tablet is working. Just make sure that you have a section for **pad**.

Now, I don't have any more settings in xorg.conf beside these. When I plug in my tablet, I run this script to configure it in the right mode and set the keys:
```
#!/bin/bash

#set mode to "absolute"
xsetwacom set stylus mode absolute

#set scrolling with ring
xsetwacom set pad RelWUp "key core pgdn" 
xsetwacom set pad RelWDn "key core pgup"

#set zoom with ring
# xsetwacom set pad AbsWUp "core key -" 
# xsetwacom set pad AbsWDn "core key +"

# Button <  set to + (Zoom in)
xsetwacom set pad Button1 "core key +"
# Button FN1  set to - (Zoom out)
xsetwacom set pad Button2 "core key -"
# Button > to Ctrl Z (undo)
xsetwacom set pad Button3 "core key ctrl z"
# Button FN2 to Ctrl Y (redo)
xsetwacom set pad Button4 "core key ctrl y"

#setting the buttons on the stylus
# xsetwacom set stylus Button3 3
# xsetwacom set stylus Button2 2
```

Some of these can be entered in xorg.conf, you can see what to write with (for example)
```
xsetwacom -x get stylus mode
```
This will return a line in xorg.conf syntax, you can write it to xorg.conf in the stylus section to save this setting permanently.
But it says you can't setup key combos in xorg.conf, so that's why I still use this script.

Hope this helps.

EDIT: If you decide to use xsetwacom, [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom) has some examples.

---

