---
title: "Quitting Safely after a Lockup?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-02-28
What key combination is used to make sure that it is safe to power down the computer after a hard lock up?  For instance, I was doing something with a screen saver and the computer froze so badly turning it off at the button didn't even help.

What is to be done in these cases before I unplug the computer?  Are the key combinations different for Gnome and KDE?

---

### Post by 23meg on 2007-02-28
[http://www.ubuntuforums.org/showpost.php?p=1185718&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1185718&postcount=12)

---

### Post by Darklighter137 on 2007-02-28
Thank you for the suggestions!

However there are some problems.  Even when the computer is working normally (and most certaintly when it is not), Ctrl + Alt + Backspace does nothing.  The other command works fine normally, but the computer didn't recognize any of it when I repeated the freeze I had earlier.

Whenever I select the screensaver "Hyperspace", the computer rolls over and dies; it needs to be unplugged because I guess it doesn't see any input at all after that happens.  I was running that screen saver a week ago, but then it suddenly stopped working (it went to a black screen rather than the screen saver.  Now whenever I even click on it, the computer explodes.  :confused:

---

### Post by 23meg on 2007-02-28
[QUOTE=Darklighter137]However there are some problems. Even when the computer is working normally (and most certaintly when it is not), Ctrl + Alt + Backspace does nothing.[/QUOTE]

That's unusual. There must be something wrong with your X config.

Before the "skinny elephants" key combination I'd try switching to a virtual console (Ctrl + Alt + F1) and doing ```
sudo shutdown -h now
```

[QUOTE=Darklighter137]
Whenever I select the screensaver "Hyperspace", the computer rolls over and dies; it needs to be unplugged because I guess it doesn't see any input at all after that happens. I was running that screen saver a week ago, but then it suddenly stopped working (it went to a black screen rather than the screen saver. Now whenever I even click on it, the computer explodes.[/QUOTE]

It's likely that somethings's wrong with your OpenGL configuration. Do you have problems with other 3D apps and screensavers as well?

---

### Post by Darklighter137 on 2007-02-28
Ctrl + Alt + F1 also fails to have any effect, even when the computer is running normally.  I did install my ATI drivers (which work great), but Ctrl + Alt + Backspace didn't work even before that.  In fact, it didn't work under the LiveCD either.

Unless you count Nexhuiz, everything I've tried to run works just fine, and even that screen saver worked fine and then just stopped working abruptly. =(

---

### Post by 23meg on 2007-02-28
Ctrl + Alt + F1 doesn't give you a black screen, but just does nothing? There's a known fix for the black screen, but I really am not familiar with such basic key combinations not working. It may be ATI related, but I also don't know anything about the ATI drivers so I can't help you there. Try reverting to the "vesa" driver temporarily and see if the same happens. Also do a forum search if you haven't, to see if others have had similar problems.

One more thing: look into your /var/log/Xorg.0.log file to see if anything unusual is reported.

---

### Post by Darklighter137 on 2007-02-28
I've actually tried that before, and it isn't related to the drivers (it failed then as well).

Should that file you mentioned exist?  I'm having trouble getting to it.  If I try and get to it normally, I get a permission denied error.  If I try with sudo, I get a command not found error.

Thanks for your help. =)

---

### Post by 23meg on 2007-02-28
Yes, it should exist. I'm beginning to think you have a seriously malfunctioning X.

What does ```
tail /var/log/Xorg.0.log
``` return?

---

### Post by Darklighter137 on 2007-02-28
The output is thus:
justin@justin-desktop:~$ tail /var/log/Xorg.0.log
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

---

### Post by 23meg on 2007-02-28
So it exists. You can view the whole log in System / Administration / System Log, or by opening it with a text editor as well.

---

### Post by Darklighter137 on 2007-02-28
Okay, I have opened it....  Now what should I look for?

---

### Post by 23meg on 2007-02-28
Any kind of error really; nothing specific I can think of.

---

### Post by Darklighter137 on 2007-02-28
Thanks.

To be honest, if I'm reading the file correctly, no errors have been issued (at least none are listed).  The freeze is so hard I don't doubt this system is unable to even log it.

---

### Post by 23meg on 2007-02-28
Look into the other logs in System / Administration / System Log (after it occurs) as well.

---

### Post by Darklighter137 on 2007-02-28
I've looked them over for that time span, but none of it means anything to me (I'm a Linux newbie).

---

