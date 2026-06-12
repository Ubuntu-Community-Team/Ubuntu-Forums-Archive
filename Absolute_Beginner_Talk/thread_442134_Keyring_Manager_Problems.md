---
title: "Keyring Manager Problems"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by adma on 2007-05-13
Whenever I try to run the Keyring Manager, it prompts: "Enter password for default keyring to unlock"

I've never specified this password, so I don't know what it is. Leaving it blank doesn't work - and neither does my login password.

It is extremely frustrating not being in control of your own computer :(

Thanks for helping!

---

### Post by Metacarpal on 2007-05-13
The first time I used keyring (or rather, the first time Ubuntu prompted me to use keyring), it asked me to set a password.  I'm not sure if you may have done this without realizing it, or if someone else did this while on your profile, but I think I found a fix:

NOTE: only do this if you know all the passwords you had keyring saving for you.  If I'm right, this will clear your keyring entirely.

Open a terminal (Applications menu > Accessories > Terminal) and type:
```
rm ~/.gnome2/keyrings/default.keyring
```
Hopefully, that'll fix you right up.

---

### Post by adma on 2007-05-13
Thank you! That fixed it right away!

I really can't exclude the possibility of having set the password, but I swear I can't remember doing that :confused: 

Thanks!!

---

### Post by VorDesigns on 2007-05-14
1st, thank you, this allowed me to kill my default keyring that apparently cannot accept a real password.
2nd, I did enter the password when prompted by nm-applet and, following the complexity rules for those of us actually bothering to try and secure their equipment, I entered a password that like n0$3bl33d! and the keyring manager accepted it without issue.  Upon logging back in, nm-applet prompted for the password.  Too bad it couldn't use the one I gave it.

---

### Post by Metacarpal on 2007-05-15
It may have been the $ character that did it.  I'm not sure how keyring operates, but $ starts a variable string in many programming environments.  I use a combination of alphanumeric and non-alphanumeric characters in my keyring password without issue.

---

### Post by eode on 2007-12-20
..that would be hideously insecure.

---

