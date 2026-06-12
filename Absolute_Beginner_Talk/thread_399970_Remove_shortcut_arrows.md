---
title: "Remove shortcut arrows"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-04-03
One of my pet peeves in windows XP was those shortcut arrows. They are entirely pointless. Of course, they're shortcuts. I know they're shortcuts. I put them there.

 Now that I have finally found out how to put shortcuts on the desktop, I am shocked to see that the shortcut arrows in Ubuntu are twice as large as Windows...s, and I cannot find a way to remove them(Ubuntu does not seem to have an easily accessible registry, if it has one at all).

 Can anyone help me out with this?

 -ZW:guitar:

---

### Post by seshomaru samma on 2007-04-03
If you right-click on the icon and choose properties you can change the icon to your liking -choose any icon you want

---

### Post by ZeroWing on 2007-04-03
Using Xubuntu, by the way.

 ...Xubuntu is becoming a bit of a problem... Would there be a way to switch to Ubuntu  without losing my data...?

---

### Post by seshomaru samma on 2007-04-03
yes
install gnome
```
sudo aptitude update
```
```
sudo aptitude install ubuntu-desktop
```
when asked choose GDM instead of KDM
log out and choose 'gnome' in the 'sessions' option in the GDM screen

---

### Post by ZeroWing on 2007-04-03
> **seshomaru samma said:**
> yes
install gnome
```
sudo aptitude update
```
```
sudo aptitude install ubuntu-desktop
```
when asked choose GDM instead of KDM
log out and choose 'gnome' in the 'sessions' option in the GDM screen

 Alright, thanks.:)

---

### Post by baltazar_in_oz on 2007-04-04
I also wish to remove the shortcut arrows and tried seshomaru samma's 
advice but that doesn't remove the arrow just puts up another emblem.. Can someone please explain how to remove the arrow ??? after similiar research in M$ Windoze XP it was an easy thing ... surely the same must be said for Ubuntu (dapper)

thanks
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
Baltazar_in_oz

---

### Post by oilchangeguy on 2007-04-04
just a quick windows tip. to remove the shortcut arrows go to start, run, regedit. find, find what in the box type IsShortcut click search. right click the shortcut, select delete. you'll need to repeat this until it gets from a-z and shows finished searching the registry.

---

### Post by ZeroWing on 2007-04-04
Thanks, we Ubuntu users *love* Windows tweaks! :roll:

---

### Post by oilchangeguy on 2007-04-04
hey, you were the one complaining about the arrows in windows. just trying to help you out.

---

### Post by david_kt on 2007-04-04
> **baltazar_in_oz said:**
> I also wish to remove the shortcut arrows and tried seshomaru samma's 
advice but that doesn't remove the arrow just puts up another emblem.. 
Baltazar_in_oz

That is because after you choose property, you add emblem. Remove all emblem. After that, click on the icon. It will open a window to let you choose whatever icon you want, just navigate to the icon you want.

DK

---

### Post by knobuddixspexdazpanishin on 2008-01-07
If you are still interested in knowing how to do this see my reply at [http://ubuntuforums.org/showthread.php?t=554820&highlight=remove+shortcut+arrows]("http://ubuntuforums.org/showthread.php?t=554820&highlight=remove+shortcut+arrows")

cheers :KS

---

