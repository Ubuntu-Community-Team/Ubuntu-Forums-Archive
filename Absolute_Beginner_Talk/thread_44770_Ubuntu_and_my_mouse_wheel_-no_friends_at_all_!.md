---
title: "Ubuntu and my mouse wheel -no friends at all !"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by robertzhong on 2005-06-27
Hi, all
Have been using Ubuntu for 2 days now, very happy in general, small things troubling me , one of them is Logitech's cordless mouse wheel does not scroll.

Yes, I did search the forum and found a few answers, played for a few HOURS!, but nothing works.

But I remerbered this wheel did work in Fedora, here is my configs in the /etc/X11/xorg.conf, please Ubuntu experts, this seemingly little problem starts to take its toll on me now.

any ideas welcomed
thks
robert zhong


Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"mouse"
	Option 		"Device" 	"/dev/input/mice"
	Option 		"Protocol" 	"ExplorerPS/2"
	Option 		"Buttons" 	"7"
	Option 		"ZaxisMapping" 	"6 7"
	Option 		"Resolution" 	"800"
EndSection

---

### Post by skoal on 2005-06-27
*Option "Protocol" "ExplorerPS/2"*

change that to:

Option "Protocol" "Auto" or Option "Protocol" "IMPS/2"

...and booyah! That should fix the scroll for ya.  I had a wireless cordless Logitech and that always worked for me.  I don't know what all those other options you have listed are for.  Sounds like you have a mini airplane control panel for a mouse there...mine was just the 'ole 3 button doohickey.

\\//_

---

### Post by robertzhong on 2005-06-27
Hi, getting better - tried "Auto", the side buttons (back and forward)are working ! BUT not the wheel.

more ideas, thks
robert zhong

---

### Post by khwang on 2005-06-27
The problem I have, is that my mouse cursor jumps around all over the place, then my calendar pops open in the top right corner, then a window opens to show the contents of my Trash can, it just goes crazy.  Anyone else experience this?

---

### Post by skoal on 2005-06-27
oops! Robert, it sounds like you have a pretty fancy mouse there.  I thought it was just a simple clearance rack special like mine.  Anyways, I did find this link:

[http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons](http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons)

which sounds more like yours.  By the way, I'm pretty sure there's a thread somewhere in this forum already dealing with this issue you're having, and a sol'n.

\\//_

---

### Post by robertzhong on 2005-06-27
hi, skoal, the logitech mouse came with logitech keyboard as a set. 

The mouse itself is black in its base metalic silver on top,on top , you will find -

 Left click (1),  Right click (2) and the wheel in between (I understand from the forum that the middle wheel counts as 3 buttons - wheel click (3), wheel up (4) and wheel down(5) ).

On left hand side, you will find two arrowed buttons - forward (5) and backward (6).

anyway I am reading your link now, thks again
robert zhong

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=robertzhong]Hi, all
Have been using Ubuntu for 2 days now, very happy in general, small things troubling me , one of them is Logitech's cordless mouse wheel does not scroll.

Yes, I did search the forum and found a few answers, played for a few HOURS!, but nothing works.

[/QUOTE]

DO this command, pcik the generic usb/ps2 wheel mouse as an option, then tell it you want to emulate three buttons and you want the mouse wheel to work.

> sudo dpkg-reconfigure xserver-xorg

---

### Post by robertzhong on 2005-06-28
took the dare, unfortunitely messed up with Xserver confi stuff i think it was vga card, Ubuntu boot to the text mode out of my knowledge, ended up reinstall the Ubuntu again.

I might just buy a "down grade" mouse and finish with scrolling nightmare.

thks anyway
robert zhong

---

