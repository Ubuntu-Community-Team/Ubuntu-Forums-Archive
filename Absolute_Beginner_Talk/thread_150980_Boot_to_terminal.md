---
title: "Boot to terminal?"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Zooropa on 2006-03-27
Newbie question - but how do I stop myself from booting into Gnome, and just boot to a terminal?

Is there any way?

I have a GRUB install dual booting with Windows XP and Ubuntu.

---

### Post by Kurt` on 2006-03-27
System->Administration->Services

Disable "Graphical Login Manager (gdm)"

Reboot

---

### Post by Zooropa on 2006-03-27
Thanks!
How would I get back into Gnome to re-enable it once I had done that?

I'm not at my machine right now as I'm in work.

---

### Post by codejunkie on 2006-03-27
[QUOTE=Zooropa]Thanks!
How would I get back into Gnome to re-enable it once I had done that?

I'm not at my machine right now as I'm in work.[/QUOTE]
login and run```
startx
```in the terminal.

---

### Post by 3rdalbum on 2006-03-27
Is there a way to boot into the terminal as a once-off? For instance, if I hold down a key at startup?

---

### Post by Kurt` on 2006-03-27
Well you can wait for GNOME's login screen to load, Left-Alt + Left-Ctrl + F1 to get to a terminal, then login and do "killall gdm". :P

If you want to get back into GNOME (if you didn't kill gdm), hit Left-Alt + Left-Ctrl + F7

---

### Post by engla on 2006-03-27
[QUOTE=3rdalbum]Is there a way to boot into the terminal as a once-off? For instance, if I hold down a key at startup?[/QUOTE]
You should be able to boot into single user mode from your bootloader, by adding "single" to the kernel command line.. You could make an entry for that or so. 

However, single user mode will put you as root in a bit decimated system (many services don't run in single user mode), so you would have to do something extra to be able to log in as your user and do everything but start gdm.

So, good question, I'd like to know how.

---

### Post by az on 2006-03-27
[QUOTE=3rdalbum]Is there a way to boot into the terminal as a once-off? For instance, if I hold down a key at startup?[/QUOTE]
Pick the recovery option in the grub menu.  Press escape when you boot if you do not see that menu already.

---

### Post by BobSongs on 2006-03-27
[QUOTE=Kurt`]System->Administration->Services

Disable "Graphical Login Manager (gdm)"

Reboot[/QUOTE]
Odd. I just tried that. All that happened is my Gnome session shut down. I rebooted the PC and it came right back to the GUI. Ubuntu is strangely resistant to booting to a command prompt.

---

