---
title: "Mouse Problems... Help pls... =)"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by unique1 on 2005-11-29
Ok, I did install Ubuntu on my Old PC, after the installation it started normal on the login screen and i could type properly and enter into my account but when I try to move my mouse, it does not move? so I did restart my PC and tried entering the bios since this has a mouse cursor support, and in the bios the mouse worked fine... any ideas or help? thanks! :)

---

### Post by aragorn2909 on 2005-11-29
Is it a serial mouse?

---

### Post by Kyral on 2005-11-29
Try

```
sudo dpkg-reconfigure xserver-xorg
``` in the terminal and pay attention to the mouse part :D

What kind is it? USB or PS/2?

---

### Post by unique1 on 2005-11-29
Serial

---

### Post by aragorn2909 on 2005-11-29
Simple solution.  For an old 2 button serial mouse, all you need to do is edit your xorg.conf file.  At the login screen, type "Alt-S" to choose a session, and use your keyboard to scroll down to "Failsafe Terminal".  Log in as normal.  Once your in the terminal, type "sudo nano /etc/X11/xorg.conf"   Use your keyboard to scroll down to "inputDevice" section where your mouse is configured.  Change "/dev/input/mice" to read "dev/ttyS0" (for com1) and change "ImPS/2" to read "microsoft".  Once thats done, just Ctrl-x to save the new config file, type exit, and everything should be working fine.

---

### Post by unique1 on 2005-11-29
ey, y can't i save it? i ctrl-X it and it ask me if i want to save so i press Y, but then after i exit, it goes back to the wat it was before?

---

### Post by unique1 on 2005-11-29
ok, i was able to save it, but my mouse won't still work? any other ideas?

---

### Post by unique1 on 2005-11-29
ow, n by the wat wen u told me to change /dev/... to dev/ttySO is the last character there letter o or number zero? cause I put letter o.

---

### Post by aragorn2909 on 2005-11-29
[QUOTE=unique1]ok, i was able to save it, but my mouse won't still work? any other ideas?[/QUOTE]

Is your mouse on com1?  If, say, its on com2, you need to edit /dev/ttyS1, com3 /dev/ttyS2, and so on.  Just make sure that /dev/ttyS0 is a zero, not the letter o.

---

### Post by unique1 on 2005-11-29
lol, such a new I am, hehe, i c, il give it a try, thanks. :p

---

### Post by aragorn2909 on 2005-11-29
[QUOTE=unique1]lol, such a new I am, hehe, i c, il give it a try, thanks. :p[/QUOTE]

That makes 2 of us!;)

---

### Post by unique1 on 2005-11-30
I, just wondering, how would you know on what port your mouse is connected to? cause i did try what you said and yet still my mouse dosn't move?

---

