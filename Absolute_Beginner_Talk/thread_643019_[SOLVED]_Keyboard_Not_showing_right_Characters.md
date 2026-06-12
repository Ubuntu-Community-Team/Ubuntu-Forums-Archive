---
title: "[SOLVED] Keyboard Not showing right Characters"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by tinglew on 2007-12-17
I have a Dell Latitude D505 and have just installed 7.10. While using the live CD version characters typed in the terminal window showed correctly. Now after installing to the hard drive, they don't. I thought choosing the Dell Latitude Laptop keyboard in Preferences/Keyboard would make a difference but it doesn't. This is really annoying as I'm sure it is an easy fix, but....I can't figure it out.

Warren

---

### Post by Lord_Dicranius on 2007-12-17
Does it look like "jibberish"?  Or are they keys just typing different letters?  What does "System -> Preferences -> Keyboard -> Layouts" show?

---

### Post by tinglew on 2007-12-17
Not gibberish, just not the character shown on the actual key, for example, the pipe | and backslash \ key just above the enter key actual type right > and left < arrow keys instead.

Under Preferences\Keyboard\Layouts I have chosen Dell Latitude series Laptop for my keyboard model. Do I need to choose this and reboot the system for it to take effect?

Warren

---

### Post by Lord_Dicranius on 2007-12-17
Sounds like you might have chosen the Dvorak or International layout (the keys are mapped differently in this layout).  You see anything in that window that reads "U.S. English" or "U.S. English - Dvorak"?

I apologize for the vague descriptions.  This is from memory and from screenshots I can find online haha  I'm at work on a WinXP box right now.

---

### Post by jken146 on 2007-12-17
I don't believe you have to reboot.  You could try restarting X though (Ctrl+Alt+Backspace, you will be logged out).

If changing the settings in Gnome fails, you may have to change the X settings yourself.  You can edit the appropriate section in /etc/X11/xorg.conf or do ```
sudo dpkg-reconfigure xerver-xorg
```

---

### Post by tinglew on 2007-12-17
> **Lord_Dicranius said:**
> Sounds like you might have chosen the Dvorak or International layout (the keys are mapped differently in this layout).  You see anything in that window that reads "U.S. English" or "U.S. English - Dvorak"?

I apologize for the vague descriptions.  This is from memory and from screenshots I can find online haha  I'm at work on a WinXP box right now.

No, the selection is Dell Latitude series laptop for keyboard model, and the selected layout has Canada showing in the window below.

And this isn't even the big problem I have, no wireless connection, but that's another thread...

Warren

---

### Post by tinglew on 2007-12-17
> **jken146 said:**
> I don't believe you have to reboot.  You could try restarting X though (Ctrl+Alt+Backspace, you will be logged out).

If changing the settings in Gnome fails, you may have to change the X settings yourself.  You can edit the appropriate section in /etc/X11/xorg.conf or do ```
sudo dpkg-reconfigure xerver-xorg
```

I tried the sudo command and got an error message that that xerver-xorg was not installed.

and the section in the xorg.conf file has pc105 for xkbmodel, any idea what the phrasing would be for the Dell Latitude series laptop, or would I just put that in there.

Warren

---

### Post by Lord_Dicranius on 2007-12-17
Oops, that above command should be "xserver", not "xerver" hehe

Where the layout reads "Canada", can you change that to "U.S. English"?  Reboot may be needed.

**EDIT**
Aha!  I found a video on youtube that shows how to change the keyboard layout haha  Like this one, just make sure you have "U.S. English - Default" selected, not the dvorak layout as is shown in the video.

[http://www.youtube.com/watch?v=iMKleULMhmE&watch_response](http://www.youtube.com/watch?v=iMKleULMhmE&watch_response)

---

### Post by tinglew on 2007-12-17
> **Lord_Dicranius said:**
> Oops, that above command should be "xserver", not "xerver" hehe

Where the layout reads "Canada", can you change that to "U.S. English"?  Reboot may be needed.

**EDIT**
Aha!  I found a video on youtube that shows how to change the keyboard layout haha  Like this one, just make sure you have "U.S. English - Default" selected, not the dvorak layout as is shown in the video.

[http://www.youtube.com/watch?v=iMKleULMhmE&watch_response](http://www.youtube.com/watch?v=iMKleULMhmE&watch_response)

That did it, chosing the U.S. English - Default for a layout, and a reboot was not necessary,

Thanks a bunch
Warren

---

### Post by Lord_Dicranius on 2007-12-17
Awesome!  Glad to hear it's working now! :-D

Make sure to mark the thread as "solved" from the "thread tools" menu near th e top :)

---

### Post by jken146 on 2007-12-17
Sorry about that typo!

---

