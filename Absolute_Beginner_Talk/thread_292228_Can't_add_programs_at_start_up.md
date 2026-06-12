---
title: "Can't add programs at start up"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by highllamas on 2006-11-03
Hi. I have installed Edgy Eft two days ago and I have a strange problem. I have been using Dapper Drake for a month and I didn't have any similar problems...
I go to System>Preferences>Sessions>Start Up Programs and add a command (for example gdesklets) to make this eye candy tool load on start up. Everything seems to be fine and I press Close. The problem is that when I go again on System>Preferences>Sessions>Start Up Programs the command has been disappeared. Of course when I reboot gdesklets don't load automatically.... This is happening with any command I use for start up (I have tried for example xmms)...still nothing...Any ideas?
Thanks.

---

### Post by wilberfan on 2006-11-16
This is happening to me, too...   I did a clean install of Edgy less than a week ago.

---

### Post by taurus on 2006-11-16
That's weird because I don't have any problem with gdesklets, gkrellm, & gdeskcal at all when I log into Gnome...

---

### Post by wilberfan on 2006-11-16
I think my previous clean Edgy install worked fine in this regard, too!   Very weird...

---

### Post by aidanr on 2006-11-16
strange, you can try adding them manually to ~/.config/autostart
create a new file **program.desktop**, open it in gedit and put in the following
```
[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=program
X-GNOME-Autostart-enabled=true
```
of course change program to whatever

or run gnome-session-properties in a terminal and see does it spit out any errors

---

### Post by wilberfan on 2006-11-17
Hey, thanks for the suggestion!

I did try it, and not only does gdesklets now start at startup--but there is a gdesklets entry now in the "Sessions" window--which is exactly where I could NOT get an entry to stay...

I don't know if this is related:   Why does my 'sessions' window open automatically at login now?  It's kind of annoying.   Is there a way to turn that off?

---

### Post by manishraichur on 2006-11-17
My problem is ...whenever i put gdesklets in session for autostart,it hangs my system during the boot.

manish

---

