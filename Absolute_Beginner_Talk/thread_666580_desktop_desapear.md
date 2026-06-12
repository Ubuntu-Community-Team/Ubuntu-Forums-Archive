---
title: "desktop desapear"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by astathios on 2008-01-13
hello 
i dont know what i did and i lost my desktop (gnome)
the bars are working and all the windows too
but the desktop is totaly black and i cant see the icons on it
also with right click on desktop nothing happens
any idea?

---

### Post by russell.h on 2008-01-13
That happened to me once. You might try logging out and logging back in again. That did it for me.

---

### Post by astathios on 2008-01-13
> **russell.h said:**
> That happened to me once. You might try logging out and logging back in again. That did it for me.

i did it many times 
i also rn the failsafe gnome but the problem remains

---

### Post by astathios on 2008-01-13
how can i reinstall desktop?

---

### Post by limac on 2008-01-13
you can reconfigure X. See this: [http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

Best regards,
limac

---

### Post by astathios on 2008-01-13
> **limac said:**
> you can reconfigure X. See this: [http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

Best regards,
limac

nothing:(

---

### Post by edm1 on 2008-01-13
mmm...if you make a new user and log into that does everything look correct?

---

### Post by astathios on 2008-01-13
> **edm1 said:**
> mmm...if you make a new user and log into that does everything look correct?

yes if i create new user system seems to apear ok
is any way to repair  it?

---

### Post by Fraktyl on 2008-01-17
Try killing nautilus, then restarting it.

Open a terminal:
killall nautilus
nautilus&

---

### Post by astathios on 2008-01-19
hello,
i was away for some days . i still have t same problem but i notice that if i click the icon of garbage can (right bottom ) then all is coming to normal any idea?

---

### Post by Fraktyl on 2008-01-20
Sound like Nautilus isn't running.  That's what gives you the icons on your desktop.

Click the trashcan might be starting it.  Once you've clicked the trashcan, try logging out.  Then logging back in to see if it saved Nautilus to your session.

If it doesn't save.  Try this.
System->Preferences->Sessions

Then click on the Current Session Tab.  Find nautilus in the list.  Click it.  Make sure the Style is set to Restart.  It'll be in a drop down box below the list of running programs.  Click apply, and it should auto start whenever you log in now.

---

