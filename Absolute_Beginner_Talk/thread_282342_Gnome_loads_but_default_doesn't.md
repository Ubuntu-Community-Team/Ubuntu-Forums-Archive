---
title: "Gnome loads but default doesn't?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by oilyrag on 2006-10-22
Hi all noob here,

I've installed 6.06 on a dual boot.  Everything was fine, next day ubuntu allows me to enter username and password whilst loading but then goes to a blank brown screen with a mouse pointer dead centre and stays there.  If i load up the gnome session then it loads up as expected.  The LIVEdisk works fine.  If i quickly press the reboot button it logs into a cmd line session and it prompts me to log in again, which i can do succesfully but I don't know how to get from here to the default ubuntu gui.  any help appreciated......

---

### Post by daou on 2006-10-22
If I understood you correctly, there is a problem loading the session after you log in with a default session, but no problem if you choose a Gnome session. So when you are in the log-in screen, change your session to the Gnome session and log in. This should prompt you whether you would like to make the Gnome session your default session. Click yes.

If you end up in command line and want to go back to the graphical log-in screen, type

```
sudo /etc/init.d/gdm restart
```

---

### Post by oilyrag on 2006-10-23
Thanks for that, all OK now.  Had to install the default gui as well.

---

