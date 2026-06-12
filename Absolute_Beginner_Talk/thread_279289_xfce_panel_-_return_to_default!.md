---
title: "xfce panel - return to default!?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Ansible on 2006-10-17
I just installed xubuntu a few days ago on my old vaio laptop.  Everything's been ok, even got wireless working.  Until, I copied some files from a usb drive, then pulled the drive out.  When I looked back at the screen, the panel app had disappeared, together with the thing at the bottom, whatever it is.  Anyway, now each time I log back in it automatically starts the GIMP and a terminal session up for me (I had those two open at some point in the past), but no xfce panel.  I can run xfce panel from the terminal, but when I close the terminal, the panel closes as well.  I tried this command in ~/.config/:

mv xfce4 xfce4.backup

then logged out and back in, but I still get the GIMP and the terminal, and no panel.  

So, I'd like to return to the default settings somehow, can someone help?  I still have access to the right click menu, and I can quit and log back in.

---

### Post by taurus on 2006-10-17
Your personal config for XFce4 is in ~/.config.  Try renaming it to something else to see if you get your default back...

```
mv ~/.config ~/.config.backup
```
Log out and back in again to see if it works.

---

### Post by Ansible on 2006-10-20
Thx for the reply, I got it to work again, finally.  I'm not exactly what I did to make things ok again, but I was able to start the panel outside the terminal by right clicking and using the Run option.  Then if I selected quit from the panel menu it told me the  session manager wasn't running, so it couldn't quit.  But I was able to quit from the right click menu, selecting (iirc) 'save session for next time' or something like that.  Somewhere after that I logged in with the default session from the login prompt, and that also changed a few things like the font.  Anyway, everything's ok again now.  Its that session memory thing that is kind of a pain; when you log off and tell it not to remember the session settings that it just leaves the settings from the previous time you quit and saved the settings.  So when you log back in you get the settings from the last sucessful save, which in my case consisted of GIMP, a terminal, and no panel.  What it should do is blank them out instead, reverting to a default state.

---

### Post by tijean on 2006-10-20
_*Extra tip:*_
> I can run xfce panel from the terminal, but when I close the terminal, the panel closes as well
You can prevent this by adding '&' at the end of the line, so just write the following in the terminal: 
> xfce4-panel & 

The panel(s) are then back up and as you said when quiting: save the session for future logins.

---

