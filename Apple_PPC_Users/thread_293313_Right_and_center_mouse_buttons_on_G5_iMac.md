---
title: "Right and center mouse buttons on G5 iMac?"
date: 2006-11-05
forum: Apple PPC Users
---

### Post by mike_hore on 2006-11-05
OK folks, I know this one has come up before, but as usual things don't seem to be working for me as they should.

Basically I want F12 and F13 to give a center and right click.  So following someone's advice I did
xev
and saw that F13 was code 182.  So far so good.
Now I did
xmodmap -e "keycode 182 = Pointer_Button3"

No result.  Hitting F13 didn't give me a right click (or any click).  I also tried 
xkbset
but it told me the command was unrecognized.  The advice said I might have to  load a package or something but I'm lost at this point.

--  Mike.

---

### Post by stream303 on 2006-11-05
You're not going to like my answer: I just attached a Microsoft optical usb wheel mouse and love it. :)

---

### Post by mike_hore on 2006-11-05
> **stream303 said:**
> You're not going to like my answer: I just attached a Microsoft optical usb wheel mouse and love it. :)

You're right.  (Basically at the moment I'm broke).
--  Mike

---

### Post by mike_hore on 2006-11-06
Don't all reply at once -- I might get buried under helpful suggestions...

--  Mike.

---

### Post by stmiller on 2006-11-07
[http://club.mandriva.com/xwiki/bin/view/KB/XwinXkeys](http://club.mandriva.com/xwiki/bin/view/KB/XwinXkeys)

This may help.

---

### Post by mike_hore on 2006-11-07
> **stmiller said:**
> [http://club.mandriva.com/xwiki/bin/view/KB/XwinXkeys](http://club.mandriva.com/xwiki/bin/view/KB/XwinXkeys)

This may help.

No, sorry, it doesn't.  Basically it tells me to do what I described in my first post on this thread, which is what I can't get to work.  I try mapping various function keys (particularly F11, F12 and F13, keycodes 95, 96 and 182, to Pointer_Button3.  But it has no effect whatsoever.  Hitting the function keys does nothing.

Another problem I've had is how to remove an icon from the menu bar, and the helpful advice I got was "right-click on it".  I can't !!!!!

--  Mike.

---

### Post by stmiller on 2006-11-07
Just buy a 3 button mouse. I don't know how people function with the poor apple one-button mice. Yuck!

---

### Post by mike_hore on 2006-11-07
The continuing saga...
Some more advice I received was to edit /etc/sysctl.conf to uncomment the lines

dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 95
dev/mac_hid/mouse_button3_keycode = 96

(or whatever the right keycodes are), then do
sysctl -p

But when I do this I get
error: "dev.mac_hid.mouse_button_emulation" is an unknown key
error: "dev.mac_hid.mouse_button2_keycode" is an unknown key
error: "dev.mac_hid.mouse_button3_keycode" is an unknown key

I'm totally lost as to what this means or what to do about it...

--  Mike.

---

### Post by mike_hore on 2006-11-07
Some more advice in another thread was to create a file .Xmodmap in my home directory, and put in lines

keycode 95 = Pointer_Button2
keycode 96 = Pointer_Button3

(using the keycodes my keyboard generates for F11 and F12).

I did this, restarted, got a dialog saying did I want to load the keyboard map, I answered yes.

now xev shows that F11 and F12 are indeed generating Pointer_Button2 and Pointer_Button3.
BUT THESE AREN'T DOING ANYTHING!  No mouse click is occurring.

So obviously some important ingredient is still missing.  Help somebody?  Please??

--  Mike.

---

### Post by stmiller on 2006-11-08
You might have better luck here:

[http://www.nabble.com/Free-Desktop---xorg-f1091.html](http://www.nabble.com/Free-Desktop---xorg-f1091.html)


Or just buy a 3-button mouse and join us in the 21st century. :)

---

### Post by mike_hore on 2006-11-08
> **stmiller said:**
> You might have better luck here:

[http://www.nabble.com/Free-Desktop---xorg-f1091.html](http://www.nabble.com/Free-Desktop---xorg-f1091.html)


Or just buy a 3-button mouse and join us in the 21st century. :)


Thanks for the pointer -- I see there are various complex issues with button emulation and possibly bugs -- but you're right, it's clear that 1-button mice are a rapidly dying breed with no future.  I'm not going to waste much more time on this.

Cheers,  Mike.

---

