---
title: "Double Click in File Browser doesn't work"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by wyocracker on 2007-06-07
I can't tell if I'm missing something about how linux is supposed to work, but when I'm in my File Browser and double click on a directory, nothing happens.  (I have Feisty Fawn installed.)  To get it to open, I have to single click on it, then click Enter on my keyboard.  Or, right click, and select 'Open'. 

I looked around in my mouse settings and there doesn't seem to be any option to change this.

Also, I just installed gFTP and it seems to have a similar problem there as well for cruising through remote directories.

For what its work, I'm on a Thinkpad x40.  I also added the lines to my /etc/X11/xorg.conf file to get my middle scroll button working:
	Option		"EmulateWheel"
	Option		"EmulateWheelButton"	"2"

Thanks for the help.

---

### Post by rich.bradshaw on 2007-06-09
That isn't what's meant to happen. The file manager is called Nautilus, that might help you find more info on google - no one seems to know so far in here!

---

### Post by aberadam on 2007-06-09
Strange, double clicking works with me. 

I haven't noticed anything with files that's different to XP.

---

### Post by freebird54 on 2007-06-09
I suspect it is the mouse settings that you just made that are causing the problem.  Have you looked for mouse setting info in xorg?  If you have a scroll mouse of normal type, I would expect a similar section to this:
```

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection
```

to be the right settings.  I don't know what all you have in yours though, so I can't be sure.  You could post it here for checking though, if you need to...

---

### Post by verveusha on 2007-11-01
Hi there

I have similar problem with double clicking the folder not working on the file browser. If you have  a solution for this, please post it here. I have installed Fiesty recently and my xorg.conf looks very similar to the one posted by a member here.

Thank you

---

