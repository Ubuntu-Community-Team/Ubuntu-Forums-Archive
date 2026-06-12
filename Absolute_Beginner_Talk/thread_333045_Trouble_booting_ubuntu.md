---
title: "Trouble booting ubuntu"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Striker9 on 2007-01-06
Hello, I'm trying to install Ubuntu but when I get past the loading bar I get the following screens:
> **Rotodyne said:**
> 

The error
[IMG]http://img443.imageshack.us/img443/7232/imgp1953be3.jpg[/IMG]

Continued
[IMG]http://img441.imageshack.us/img441/2060/imgp1954iy1.jpg[/IMG]

If you could scroll down in the second picture it would say

(EE) No Devices Detected

Fatal Service Error:
No Screens Found

----------


I have no idea what to do. I've used the same CD to install ubuntu on another computer so I know it's not that. If it matters, my graphics card is an x300.

---

### Post by kingmonkey on 2007-01-06
Try typing in terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Sef on 2007-01-06
Something is up with your graphics card and xorg.  Try kingmonkey's fix first.

---

### Post by Striker9 on 2007-01-06
> **kingmonkey said:**
> Try typing in terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

How am I supposed to get to the terminal? After I get past the screen all I see is a blinking cursor. Nothing I type there seems to do anything.

---

### Post by Rotodyne on 2007-01-06
Many of us who have the x300 are having this problem, and I have no idea how to solve it ](*,)

---

### Post by Rotodyne on 2007-01-06
I got it to work finally!

But this is really wierd, I hooked up a CRT monitor and tried to boot, nothing showed up. I then plugged my LCD back in, and it worked :D 

Can anyone explain this?

---

### Post by Striker9 on 2007-01-07
Tried hooking the monitor up to the analog output instead of DVI but it still did the same thing. Any ideas on what to do?

---

### Post by MkfIbK7a on 2007-01-07
ok striker after all this you see a blinking cursor?
if so pres ctrl+alt+F1
put in you name and password then type what kingmonkey said

---

### Post by Striker9 on 2007-01-12
Ok, I got into the terminal and reconfigured xserver. Is there something I should be changing when I go through the reconfiguring process? Also, what do I do once I'm done, I don't know how to restart the installation.

---

### Post by Striker9 on 2007-01-12
Bump

---

### Post by RubberDuk on 2007-01-12
Okay, I've dealt with this myself but I do not remember the 100% details.

This is what I think you should do:
when you get the error, press ctrl+alt+f1 (iirc)
then do sudo nano /etc/X11/xorg.conf and find where the resolutions are listed. Now remove all but 640*480. Save and when you're back in command line, type startx. You can move the windows better by pressing ctrl+f5 (iirc) as you have to complete installation in 640*480. There could be a more 'sophisticated' way to do this but this is how I did it. You can obviously change resolutions and install drivers when you're done. Helped me with my x800 series card.

---

### Post by Striker9 on 2007-01-12
I tried that but when I try startx I get:
```
Fatal server error:
no screens found
XIO: fatal IO error 104
```

From my earlier post:
> **Striker9 said:**
> Ok, I got into the terminal and reconfigured xserver. Is there something I should be changing when I go through the reconfiguring process? Also, what do I do once I'm done, I don't know how to restart the installation.

---

### Post by Striker9 on 2007-01-12
Sorry to bump the thread again but I really need this solved soon.

---

### Post by RubberDuk on 2007-01-13
Okay, I think I can finally help you. 

> **RubberDuk said:**
> Okay, I've dealt with this myself but I do not remember the 100% details.

This is what I think you should do:
when you get the error, press ctrl+alt+f1 (iirc)
then do sudo nano /etc/X11/xorg.conf and find where the resolutions are listed. Now remove all but 640*480. Save and when you're back in command line, type startx. You can move the windows better by pressing ctrl+f5 (iirc) as you have to complete installation in 640*480. There could be a more 'sophisticated' way to do this but this is how I did it. You can obviously change resolutions and install drivers when you're done. Helped me with my x800 series card.

Do what I described in the earlier post (above) but also change 'ati' to 'radeon' from the appropriate section in xorg.conf. I did this again today and got the same error as you did when it was set to 'ati'. Changing it helped. Best of luck!

---

### Post by Striker9 on 2007-01-13
Thanks alot. That worked.:D

---

