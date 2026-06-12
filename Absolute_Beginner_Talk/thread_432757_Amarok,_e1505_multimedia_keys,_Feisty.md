---
title: "Amarok, e1505 multimedia keys, Feisty"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2007-05-04
Inspirin e1505 multimedia keys are recognized in System --> Preferances --> Keyboard Shortcuts, but they won't set in Amarok's global shortcuts, for play, skip, previous, etc.

Any ideas?


Edit: The keys work great in Rythme Box. All of them.

Can't understand why they won't in Amarok. Thanks for any input, i'd much prefer to use Amarok. (Unless some good suggestions otherwise?)

---

### Post by rickycodie on 2007-05-04
if you love amarok try exaile. it is almost exactly like amarok, only written for gnome and not for kde.

---

### Post by Acglaphotis on 2007-05-04
Its a documented bug , no fix yet : ( .

-Acgla

---

### Post by Inxsible on 2007-05-04
I have the same problem !

---

### Post by BrowneR on 2007-05-18
ditto on my dell 9300

---

### Post by BrowneR on 2007-06-22
I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

---

### Post by danielandrews on 2007-06-22
> **rickycodie said:**
> if you love amarok try exaile. it is almost exactly like amarok, only written for gnome and not for kde.

Woah, very cool.  Thanks for the tip!

---

### Post by orb9220 on 2007-06-22
Worked for me on my MS Digital Media Pro keyboard.

Thanks! I shall:**"Sacrifice one virgin MicroSoft Employee to the Fires of the Goddess Ubuntu!"** in you name as tribute.

---

### Post by BrowneR on 2007-06-22
> **orb9220 said:**
> **"Sacrifice one virgin MicroSoft Employee to the Fires of the Goddess Ubuntu!"**

the community grows stronger! haha

---

### Post by DemonStar55 on 2007-06-24
the media keys work fine in Amarok if you're using KDE

---

### Post by BrowneR on 2007-06-24
> **DemonStar55 said:**
> the media keys work fine in Amarok if you're using KDE

thats correct. this issue is related to a change in the way gnome handles keyboard shortcuts as of v2.18.
previously each individual application would bind to the shortcut keys it wanted. as of 2.18 gnome binds to the common keyboard shortcuts and then relays their activity to applications over dbus.
this requires applications to listen for the signals on dbus and as amarok is a kde app it only (currently) supports dcop for IPC.
this issue should go away once kde moves to dbus as of kde4 and amarok 2.

---

