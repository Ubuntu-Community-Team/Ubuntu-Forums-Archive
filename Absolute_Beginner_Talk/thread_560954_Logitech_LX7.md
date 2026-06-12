---
title: "Logitech LX7"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by OutlawTruth on 2007-09-27
Okay, so I just installed Ubuntu 7.04 as a guest OS via VMWare Workstation (the host is XP). I've gotten mostly everything to work on my laptop, but I'm having trouble with the features of my mouse.

I have a Logitech LX7 mouse, which has back and forward buttons and a tilt wheel. I've searched this subject quite a bit and haven't really found anything that is geared for an Ubuntu noob like myself.

I'm not sure if it's possible to get that functionality because of the fact I'm on VMWware, but I figured I'd try and ask anyway. If anybody could help, that'd be great :-)

If not, thanks anyway.

---

### Post by sunexplodes on 2007-09-27
Not sure about the tilt wheel, but this worked for my back and forward buttons:

open up a terminal, and type "sudo aptitude install xvkbd xbindkeys", which will install a couple of packages that do this pretty well.

then. in the terminal, type "sudo gedit /etc/X11/xorg.conf", and scroll down to the part where it talks about your mouse, and make sure it's says:

	Option		"Protocol"		"ExplorerPS/2"

instead of

	Option		"Protocol"		"ImPS/2"

Then, open gedit, and add the following text:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```

Depending on the mouse, you may have to change the "b:8" and "b:9" parts to "b:6" and "b:7". Trial and error. 

Save this file as /home/yourusername/.xbindkeysrc .

Now, the last thing you'd need to do is go into System>Preferences>Sessions, and add "xbindkeys" to your startup programs. 

Reboot, and your back/forward buttons SHOULD work. That works for me on my Logitech mouseman, anyhow.

---

### Post by sunexplodes on 2007-09-27
Oh, and here's the guide i took that info from:

[http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mice+new+guide](http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mice+new+guide)

There's a lot of info there, but all I had to do was the part I mentioned to you.

---

### Post by OutlawTruth on 2007-09-27
I tried it, but no luck. For the record, the info on my xorg.conf file didn't say "ImPS/2" it just said "ps/2"

Here's what it says now:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Also, I tried both 6&7 and 8&9. Now when I go to the sessions manager, and I click new, what do I type in each field?

Right now, I just have "xbindkeysrc" for both name and command.

Any ideas?

---

### Post by sunexplodes on 2007-09-28
Ah, yeah. In sessions, where it says "Name", enter Xbindkeys or whatever you want it to be listed as, it's arbitrary.

Under "command" have it say xbindkeys. 

To test it, just run xbindkeys in a terminal.

and make sure that .xbindkeysrc file is titled ".xbindkeys" WITH the period at the beginning, too.

---

### Post by OutlawTruth on 2007-09-28
How do I run xnbindkeys in terminal?

Also, I did do a command in terminal that let me know what programs were running, and xbindkeys was one of them, so I guess I entered it correctly in the sessions manager, however it's still not working. I'll try to change the xbindkeys file again as far as the 8/9 6/7 thing. Anything else I should check for?

---

### Post by OutlawTruth on 2007-09-28
It's funny, actually I forgot where I saw that xbindkeys was running and I'm not sure anymore that it is.

Is it "xbindkeys" I have to put in the sessions manager, or do I put ".xbindkeysrc"?

---

