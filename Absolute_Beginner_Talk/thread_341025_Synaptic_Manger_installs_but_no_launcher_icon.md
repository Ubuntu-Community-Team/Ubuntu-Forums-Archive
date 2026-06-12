---
title: "Synaptic Manger installs but no launcher icon?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by nayo on 2007-01-18
Hi.  I think I'm installing some things ok.  Anyway, Audacity went fine and installed an icon up above in the Applications>Sound & Video section.  But Rosegarden will run with an Alt + F2 command and yet there is no icon to be found anywhere.  Same goes for GnuChes and GnuGo which the Synaptic says is installed.  Actually for these there are no icons and I cannot get it to run even with alt+F2.  Please explain.  Thnks!

---

### Post by nsleiman on 2007-01-18
even though i never used GnuGo, but i would try to launch this prog from the console(Terminal)  itself and see what is missing/happening.

---

### Post by ekka on 2007-01-18
I had the same problem sometime back. The guys in the forum suggested me to do this, the problem is more or less solved now.

1.	Restart the system and see if the icons are there
2.	If not do this and see if it helps.

```
sudo update-menus
```

---

### Post by doerum on 2007-01-18
ok, i had a similar problem with network manager gnome. No icon in meny, even though the application was installed.

---

### Post by nayo on 2007-01-18
ekka and everybody, thanks

but when I try to run sudo update-menus in the terminal it says
command not found

same with running in alt+F2  (can you tell I don't know what I am doing?  :)

---

### Post by nayo on 2007-01-18
oh and I restarted it and the icons were not there.

---

### Post by ekka on 2007-01-18
err...may be I got the code wrong.

Try this code again with out the sudo, it worked for me.
```
update-menus
```

---

### Post by kerry_s on 2007-01-18
> **ekka said:**
> err...may be I got the code wrong.

Try this code again with out the sudo, it worked for me.
```
update-menus
```

You have to install "menu" first, than run the command and it will give you the debian menu.

---

