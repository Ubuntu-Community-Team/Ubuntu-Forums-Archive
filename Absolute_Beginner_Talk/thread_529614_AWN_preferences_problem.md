---
title: "AWN preferences problem"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by -Morgoth- on 2007-08-19
I just installed Avant Window Navigator and then started the program. A black bar appeared down in the middle-bottom of the screen just as it should (I think...). Then I right-clicked it and selected 'Preferences' and the 'Preferences' window opened up. I had a look around and added a launcher for firefox and left the 'preferences' window. Then the problems came... The Launcher I had created didnt appear on the AWN bar. And I can't enter the 'Preferences' window anymore. When I click it, nothing happens :S
The AWN bar seems to work fine as a windows list

Anyone know whats wrong here?

---

### Post by -Morgoth- on 2007-08-19
No one?

---

### Post by walkerk on 2007-08-19
try dragging an item from the gnome menu on to awn. that should add it. :)

---

### Post by -Morgoth- on 2007-08-20
Hmm, yeah that works. Thanks :)

But i still can't change the preferences :/ I would like to customize a bit and use autohide. Do you know any other ways to access the preferences page ?

---

### Post by Xzandafer on 2007-08-22
:-k got the same problem. I've installed AWN as this guide made by **reacocard** says: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981). I think it's because of SVN version of AWN that this guide suggests to install. Can anyone say how to install stable version? Maybe this will help?

**EDIT:**

Okay, I think I figured out what to do to 'fix' this... Try to **reset your Desktop settings to defaults**. It will change your entire desktop to way it looked at first boot ([click here to read more about that]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")). This is how to do it:

Open terminal and paste this:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Then logout or restart.

If this won't help try also to restart X by hitting **Ctr+Alt+Backspace**.

In my case it solved the problem.

---

