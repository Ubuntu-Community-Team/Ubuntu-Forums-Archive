---
title: "Xubuntu (feisty) fails to start Xserver, TiBook G4"
date: 2007-08-13
forum: Apple PPC Users
---

### Post by fifteen90 on 2007-08-13
hey guys, i'm new around here, but from what i've read so far there seems to be plenty of knowledegable  around to help me out with this one.

i've decided to install xubuntu on my 400mhz powerbook g4.  the install seemed to go pretty smoothly, until it started its first boot up.  i got a message saying that xserver has failed to start.  a glance at the error log says something about an "invalid IO allocation" (i'm a n00b at this, btw, so i don't know what that means :confused:).

i've already tried sudo apt-get update/upgrade and  sudo dpkg-reconfigure xserver-xorg.  the reconfig walked me through some questionnaire-type steps, but still no dice.

anyone have any experience with this setup?  thanks in advance!

---

### Post by stmiller on 2007-08-14
Hey if you can get to the x.org error log, that would help to see what's going wrong.

Tell us any lines that have (EE) beside them on this log by typing this at the terminal:
```

less /var/log/Xorg.0.log

```
or 
```

cat /var/log/Xorg.0.log |more

```

---

### Post by fifteen90 on 2007-08-14
thanks for the advice, stmiller!  i looked through the log and noted all the warnings and errors i saw.

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
		Entry deleted from font path
```

```
(WW) ****INVALID IO ALLOCATION**** b: 0xf0000400 e: 0xf00004ff correcting^G
(EE) end of block range 0xefffffff < begin 0xf0000000
```

```
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
		(you may have to look at the server log to see warnings)
```
```

(EE) Screen(s) found, but non have a usable configuration
```

any ideas of what i should do next?

---

### Post by fifteen90 on 2007-08-15
found the answer!  on a [german ubuntu wiki]("http://translate.google.com/translate?hl=en&sl=de&u=http://wiki.ubuntuusers.de/Apple_Powerbook_G4_Titanium&sa=X&oi=translate&resnum=8&ct=result&prev=/search%3Fq%3Dpowerbook%2Btitanium%2B400%2Bmhz%2Bfeisty%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DG"), no less.

the key was the horizontal/vertical sync rates for the display.  they should be set to:

horizontal: 31-46 
vertical: 50-70

those germans sure know what they're doing :)

---

### Post by danrubin on 2008-05-12
I was also experiencing the black screen after install (TiBook/400MHz, Xubuntu 7.04), and the monitor refresh settings were all that I needed to change.

Just for clarity for other newbies (since I had to go elsewhere to look it up), to make the change (from the black screen):

[LIST=1]
[*]press **ctl-option-F1** to enter the terminal
[*]at the prompt, type ```
sudo nano /etc/X11/xorg.conf
```
[*]scroll to the section marked **"Monitor"**
[*]add ```
HorizSync 31-46
VertRefresh 50-70
```
[*]press **ctl-o**, then **Enter** to confirm, then **ctl-x** to exit nano
[*]at the prompt, type ```
sudo reboot
```
[/LIST]

If/when asked for your password, type the one you used when you created the account during installation (you may also need to log in with that username/password after the first step above).

---

