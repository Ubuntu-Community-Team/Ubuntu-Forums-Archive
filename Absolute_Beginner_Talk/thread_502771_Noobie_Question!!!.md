---
title: "Noobie Question!!!"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-07-17
okay i cant even see the TOP OF THE BARS ?!?! like  ican move the windows or anything im using beryl please help me out.. i must have changed a setting but idk ... its like there not even visible...

---

### Post by CautionaryX on 2007-07-17
I think you need to add something in your xorg.conf.

In a terminal type 
```
sudo gedit /etc/X11/xorg.conf
```

scroll down to the Devices section and add the following:
```
Option "AddARGBGLXVisuals" "true"
```

Save the changes and restart your computer (or just press Ctrl+Alt+Backspace). The 'bars' should appear now.

---

### Post by Likenota on 2007-07-17
umm i cant even see my terminal... its all white... ugh.. :-/ is there another way ?

---

### Post by dpar on 2007-07-17
Maybe turn off Beryl first, then make the changes.

---

### Post by Likenota on 2007-07-17
nope... its still white.. man you guys reply really fast i love this place.. id really like to get this working anyway without this terminal??? id like to move on to more advanced things like vmware but i cant do that without the capability OF NOT BEING ABLE TO MOVE WINDOWS!! ugh or access terminal.

---

### Post by CautionaryX on 2007-07-17
You'll soon learn to love the terminal. Anyways, just press Ctrl-Alt-F2 login and do what I said above except replace **gedit** with **nano**.

---

### Post by Likenota on 2007-07-17
umm that didnt work i believe there has to be something before sudo ?... it didnt recognize the command gedit just alone... also how do i exit the terminal when i use the alt+ctrl+f2 thingy?

---

### Post by meindian523 on 2007-07-17
Alt+F7 to get back to your malfunctioning GUI login........

---

### Post by Malibu Illusion on 2007-07-17
To try CautionaryX's method, as he said, you need to replace gedit with nano:

```
sudo nano /etc/X11/xorg.conf
```

Then add the line in his post.

After doing so, you will need to do:

```
sudo /etc/init.d/gdm restart
```

---

### Post by Likenota on 2007-07-17
thanks for the help... umm i tried the sudo nano stuff but the file was blank didnt have a single thing in it.. even when i browse to it manually it does have stuff in it... also the alt+f7 didnt work is there another way to exit the terminal.. i try some of the commands then i have to restart my computer completely just to exit terminal..

---

### Post by CautionaryX on 2007-07-17
Restart your computer and enter recovery mode. Then try what I sugguested above. BTW, the terminal is case sensitive. So, if you put **sudo nano /etc/X11/Xorg.conf** instead of **sudo nano /etc/X11/xorg.conf** nothing will show up in your file.

---

### Post by Likenota on 2007-07-17
ooo well thanks.. i probably should have waited, but i just went ahead and reinstalled the whole os. but at least ill know what to do next time if something like this happens again.. hmm i wonder why it happened in the first place?..

---

### Post by rickycodie on 2007-07-17
i've got the same problem, so i'll se if it works.

---

### Post by Likenota on 2007-07-17
well what i dont get is after you edit the file how do you go about saving the file ?...

---

### Post by CautionaryX on 2007-07-17
When you are done press Ctrl-X > Y > Enter. That will overwrite the existing xorg.conf with the modified one.

---

### Post by Likenota on 2007-07-23
thanks for your guy's help/

---

### Post by rickycodie on 2007-07-24
it worked for me!!

---

### Post by jdackle on 2007-07-24
> **CautionaryX said:**
> I think you need to add something in your xorg.conf.

In a terminal type 
```
sudo gedit /etc/X11/xorg.conf
```

scroll down to the Devices section and add the following:
```
Option "AddARGBGLXVisuals" "true"
```

Save the changes and restart your computer (or just press Ctrl+Alt+Backspace). The 'bars' should appear now.

Hi guys!

I'm not sure if Likenota's probelm was any similar to my own and thus I don't know if that line will fix mine...

My problem is:
- My video card: ATI 3D Rage Pro (AGP)
- Maximum resolution is 1152x864 but I prefer 1024x768
- In /etc/X11/xorg.conf I changed:
```
"1152x864" "1024x768" "800x600" "720x400" "640x480"
```
to
```
"1024x768" "1152x864" "800x600" "720x400" "640x480"
```
everywhere that line appeared.
- In result, I now do have a 1024x768 display only not quite... The visible area is 1024x768 but the screen is not "complete" - if I move the mouse pointer upwards (or downwards, left or right) beyond the visible area limits, it will "move up" and show the top (bottom, far-left, far-right) of the screen! This means if I have a panel at the bottom I'll have to move the mouse pointer down to "move" the visible area down and actually see it ( and thus hiding more of the topper part of the screen.

So my questions are:
- Is this like your problem Likenota?
- Is the line add to xorg.conf suggested by CautionaryX safe to try or will I mess it even more?

Thanks! :)

---

### Post by jdackle on 2007-07-24
> **Likenota said:**
> also the alt+f7 didnt work is there another way to exit the terminal.. i try some of the commands then i have to restart my computer completely just to exit terminal..

This is how it works:
- By pressing CTRL+ALT+Function-key N you are moving to screen N!
- Usually, screens 1 to 6 (F1 to F6) are text-consoles (terminals). F7 is usually the GUI. F8 (in Ubuntu) is for system logs output.
(In fact you only need to add the CTRL key to that combo when you are in the GUI screen, otherwise it's enough to press the desired ALT+Function-key-number. This is why it should be enough to press ALT+F7 to get into that screen (only getting out of that partiocular one needs the CTRL key).)
- But that is the *usual* setup. It may be changed. So if you can't find your GUI "in" ALT+F7, it's possible though not likely you'll find it in some other "screen"; just go from CTRL+ALT+F1 to CTRL+ALT+F12.

Hope that helped. :)

---

### Post by jdackle on 2007-07-24
> **jdackle said:**
> 
So my questions are:
- Is this like your problem Likenota?
- Is the line add to xorg.conf suggested by CautionaryX safe to try or will I mess it even more?

Thanks! :)
Yes, I'm quoting myself! Hey, if nobody else does!...

So... I did try CautionaryX's tip (I figured I'd just login to a text-console and revert to the older xorg.conf file if needed) but STILL NO LUCK! Visible screen and "real" screen still do not match. :(
So I guess I'll post a new topic with this.

But in the meantime, here's where and what I added in my /etc/X11/xorg.conf file, jsut in case id didn't do it as it was suposed:
```
Section "Device"
        Identifier      "ATI Technologies, Inc. 3D Rage Pro (AGP)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AddARGBGLXVisuals" "true"
EndSection
```

[Link to my new thread]("http://ubuntuforums.org/showthread.php?p=3074034#post3074034")

---

