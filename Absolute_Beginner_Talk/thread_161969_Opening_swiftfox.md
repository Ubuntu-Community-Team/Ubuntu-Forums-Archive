---
title: "Opening swiftfox"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by slimdog360 on 2006-04-18
I just installed swiftfox and it works great but I cant find anysort of icon to open it. Each time I do open it I have to go to a terminal window and write

cd swiftfox
sudo ./swiftfox

I know thats its not alot of writing but its still annoying to have to do. Is there someway I can create a shortcut with this code to open it swiftfox, or perhaps some other method.
Thanks

---

### Post by dcstar on 2006-04-18
[QUOTE=slimdog360]I just installed swiftfox and it works great but I cant find anysort of icon to open it. Each time I do open it I have to go to a terminal window and write

cd swiftfox
sudo ./swiftfox

I know thats its not alot of writing but its still annoying to have to do. Is there someway I can create a shortcut with this code to open it swiftfox, or perhaps some other method.
Thanks[/QUOTE]
Firstly, you **do not** run applications with sudo, secondly you create launchers by right-clicking a vacant part of the desktop and selecting that function.

If you want to see how they are done, just look at your existing Firefox launcher.

---

### Post by jamesdodd on 2006-04-18
I agree with not running applications as sudo in principle

But I have found many problems when I don't do this:

Mainly I can't use any of the inbuild software update tools in:

firefox
azureus

If there is an alternate way around this (I currently run them as root every now and again to install updates)...




Anyway launchers are the way to go:

you can even add them into your menu if you have a menu editer...

One problem you may find is ugly icons, so you may have to browse for one...

the default ones are a little bit crap
browse to:

/home/you-name/.icons/

pick out your favourite theme and then go into apps/scalable or whatever

usually gnom-internet.png is a good choice :)

---

### Post by slimdog360 on 2006-04-18
[QUOTE=dcstar]Firstly, you **do not** run applications with sudo, secondly you create launchers by right-clicking a vacant part of the desktop and selecting that function.

If you want to see how they are done, just look at your existing Firefox launcher.[/QUOTE]

I tried creating a launcher but it doesnt work, can someone give me some more details please.
Thanks

---

### Post by _simon_ on 2006-04-18
Right click on your desktop
Select "Create Launcher"


Command is the important bit here.

it's simply the location of swiftfox.

e.g. my location is: /home/simon/swiftfox/firefox

Then just add "Swiftfox" in the Name field.

---

### Post by slimdog360 on 2006-04-18
[QUOTE=_simon_]Right click on your desktop
Select "Create Launcher"


Command is the important bit here.

it's simply the location of swiftfox.

e.g. my location is: /home/simon/swiftfox/firefox

Then just add "Swiftfox" in the Name field.[/QUOTE]

I tried it but it doesnt work. The file is a shell script, this is the file I use to open it in the terminal window. Is there another way?

---

### Post by _simon_ on 2006-04-18
Yes that's right it is a shell script. In the example the last part "firefox" is the script.

I'm not sure why it's not working for you from a launcher.

---

### Post by slimdog360 on 2006-04-18
Thats what Ive got, but im running kubuntu so it looks slightly different. When I click on the button I get a thingy, I dont know what to call it but the rectangle thing that comes up when an application is open in the taskbar and it just seems to hang, then finally goes away

---

### Post by aktiwers on 2006-04-18
On my computer it is not called /home/MYUSER/swiftfox/Firefox

It is called:

/home/MYUSER/swiftfox/swiftfox

I changed the Firefox launcher in my taskbar to this, and it works fine!

---

