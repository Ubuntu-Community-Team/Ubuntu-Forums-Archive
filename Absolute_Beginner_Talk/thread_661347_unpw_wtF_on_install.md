---
title: "un/pw wtF? on install"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2008-01-07
trying to install unbuntu 7.04 cuz 7.10 cd is scrathced to hell and its asking me for un/pw on a new computer i JUST JUST JUST build wtf? anyone know the un/pw i tried root, guest and a few other combos

---

### Post by amingv on 2008-01-07
Did you try 'ubuntu' as your username?

Also, try to make your post more readable. It's not likely that you will get help if people can't understand what you need in the first place.

---

### Post by yourpalal on 2008-01-07
root is not allowed to login by default so this will not work...
your username and password should be set to what you entered during the disc setup for example if your name is "Mark Ralph Robertson" your UN would be "mark" and you entered a password during setup which would be your password..
if you cannot login re-install and pay close attention to what you input

---

### Post by cerealtx on 2008-01-07
> **yourpalal said:**
> root is not allowed to login by default so this will not work...
your username and password should be set to what you entered during the disc setup for example if your name is "Mark Ralph Robertson" your UN would be "mark" and you entered a password during setup which would be your password..
if you cannot login re-install and pay close attention to what you input

mabey u didn't read, i just built my cpu, as in put all the peices together, out of boxes i got from ups, there is NOTHING on my computer, there was no install previous i just stuck the cd in and selected install unbuntu like i have tons of times before, and it prompted me for a un/pw i tried unbuntu didn't work :/

---

### Post by kelbizzle on 2008-01-07
> **cerealtx said:**
> mabey u didn't read, i just built my cpu, as in put all the peices together, out of boxes i got from ups, there is NOTHING on my computer, there was no install previous i just stuck the cd in and selected install unbuntu like i have tons of times before, and it prompted me for a un/pw i tried unbuntu didn't work :/

Sooo...what un/pw did you eneter during the setup when it prompted you for one? Did you use a live cd? or the Alternate?

---

### Post by kelbizzle on 2008-01-07
Just reset the darn thing...```
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.
```

---

### Post by cerealtx on 2008-01-07
there was no install, there was nothing, it just went to un/pw as if linux was installed, there was no setup it went to the first splash, i selected Install, the top one and it keeps going to the beging login splash screen...

---

### Post by amingv on 2008-01-07
@all: I think he's asking for the login for the liveCD user. If I don't misunderstand the little information I could finagle, he hasn't formatted/installed anything yet.

@OP: I just popped a liveCD in my PC and tried username: ubuntu, password: <none>. It worked. Are you sure you typed it right?

---

### Post by cerealtx on 2008-01-07
you were exactly right amingv, i tried ubuntu, with no pass nothing, i have XP installed now so 1 of my hds is formatted but still can't install ...

---

