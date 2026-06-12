---
title: "LiveCD Boot Problems"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Fipe on 2006-04-23
I've been attempting to boot from the LiveCD but have been having problems with it. It boots to the intro screen fine, and the help files work perfectly, but once I actually boot the OS itself (just by pressing enter, not with any of the extra options) the keyboard stops working, so I get stuck at the language selection menu without the ability to actually do anything. 

Is this a problem with my keyboard? (It's a Logitech Internet Keyboard, fairly old but not astoundingly so.) It works perfectly all the way up to the language menu, so presumably if so it's that Ubuntu doesn't recognise it properly. Is there any special boot command that I could use, or should I dig out another keyboard ?

---

### Post by dermotti on 2006-04-23
Is it USB?

---

### Post by Fipe on 2006-04-23
No, it's not. It plugs into the keyboard port.

---

### Post by dermotti on 2006-04-23
EDIT for liveCD

hmmm maybe a keybaord got detected wrong.


run **sudo dpkg-reconfigure xserver-xorg**

there should be a keyboard selection in there.

then kill gdm and restart it

---

### Post by Fipe on 2006-04-23
Thanks. I'll give it a try.

---

### Post by Fipe on 2006-04-23
Just entering that into the boot menu gives you an error (the exact phrasing escapes me, but it had to do with the kernel). Entering it with **live** in front of it boots and sends you to the language menu, but with the same problem as before - the keyboard won't work.

---

### Post by Sutekh on 2006-04-23
I wonder what options you would have if you tried
```
live-expert
``` from the main screen?

Also are there any options you could use if you press F1 for help and advanced options?

---

### Post by Fipe on 2006-04-23
Using **live-expert** puts me into another startup menu in which (as usual) the keyboard doesn't work. I also had a go with the parameters listed in the advanced options (I used **live noapic nolapic**) and, after a long stream of boot information, got the error message "Kernel panic - not syncing: Attempted to kill init!", followed by a prompt at which the keyboard (again) didn't work.

---

### Post by Fipe on 2006-04-23
Anyone got any ideas as to how to get the keyboard working? I have pretty much no knowledge of the command line, particularly the boot prompt version.

---

### Post by Fipe on 2006-04-23
Anyone?

---

