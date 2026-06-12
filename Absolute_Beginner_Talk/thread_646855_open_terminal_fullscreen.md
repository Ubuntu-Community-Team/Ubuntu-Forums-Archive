---
title: "open terminal fullscreen"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-12-21
what is the option that needs to be added to gnome-terminal to get the terminal to open in full screen mode? 

thanks

---

### Post by ssaamon on 2007-12-21
I am refering to opening the terminal in a shell

---

### Post by banewman on 2007-12-21
If you press ctrl-alt-F2 you will get to a fullscreen terminal - 
and press alt-F7 to get back to the desktop.
:)

---

### Post by wormser on 2007-12-21
I think you are referring to switching to a different tty.  Ctrl + Alt + F2.  You can use F2 - F6 for multiple shells.  To switch back Ctrl + Alt + F7.

---

### Post by RomeReactor on 2007-12-21
Hi. In gnome-terminal you can press F11 to go to fullscreen; press it again to restore it.

---

### Post by seventhc on 2007-12-21
not sure if this is what your talking about but if you have a shortcut for the terminal on your launcher panel you can right click on it and choose properties. in the command box add --geometry ##x##

gnome-terminal --geometry ##x##        
#=the value

edited after correction below. :)

---

### Post by jordanmthomas on 2007-12-21
> **seventhc said:**
> not sure if this is what your talking about but if you have a shortcut for the terminal on your launcher panel you can right click on it and choose properties. in the command box add --geometry 1280x800
I chose 1280x800 to test it, but you might need to make it smaller. not sure what you have for your resolution.

gnome-terminal --geometry 1280x800

By the way, 1280x800 means 1280 characters by 800 characters, not pixels.

---

### Post by seventhc on 2007-12-21
Thanks for the correction...but it did still give me a full screen but I think it just maxed out :D
Even when i had read about this I know it said it's characters but for some reason it didn't click in my brain. ;)
thanks again:)

---

### Post by ssaamon on 2007-12-22
after looking around i found the --full-screen option.

thanks a lot everyone

---

