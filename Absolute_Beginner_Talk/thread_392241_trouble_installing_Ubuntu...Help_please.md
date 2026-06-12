---
title: "trouble installing Ubuntu...Help please"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-03-24
I seem to be having some dificulty getting Ubuntu 6.10 to install.  I boot up the cd and sometimes I get as far as actually having the desktop. Sometimes I can even launch the installer but  it seem to get caught in a loop and the screen will flash a couple of times then goes to a login screen.  This is an older PII machine 256 MB RAM. Any Ideas?

---

### Post by halitech on 2007-03-24
are you booting the Live CD trying to install from there? if it's an older machine and you know for sure you want to install, I'd suggest grabbing the alt install cd and booting from there

edit: if it's a PII, you may want to go Xubuntu instead, Gnome is pretty heavy for a PII but Xubuntu should run fine.

---

### Post by lamalex on 2007-03-24
the most common fix to livecd issues are add these boot flags
```

noapic acpi=off

```
to add boot flags, before you hit enter to load the lve cd, hit f6 and add them into that string of text. if that fails come back and let us know. hopefully it works and you can come back and let us know in ubuntu!!

the other possibility is a bad burn, use the check cd option, did you burn the iso at a slow speed? isos should never be burned above 8x.

---

### Post by Drakkor on 2007-03-24
Did you verify the md5 sum of the download, and then check the CD for defects ?

---

### Post by mramsey on 2007-03-24
> **Iamalex said:**
> the most common fix to livecd issues are add these boot flags
```

noapic acpi=off

```
to add boot flags, before you hit enter to load the lve cd, hit f6 and add them into that string of text. if that fails come back and let us know. hopefully it works and you can come back and let us know in ubuntu!!

the other possibility is a bad burn, use the check cd option, did you burn the iso at a slow speed? isos should never be burned above 8x.

Ahhh that did the trick....Thanks!:)

---

### Post by mramsey on 2007-03-24
:( Alas Ubuntu has installed...however...It seems to boot fine, I enter user name and password, the desktop starts to load then the screen flashes a couple of times , then returns to the main login screen. What to do?

---

