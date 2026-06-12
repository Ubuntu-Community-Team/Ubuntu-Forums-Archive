---
title: "Beep Beep"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-19
I get more beeps than i normally would on windows.  If i backspace too far, the computer screams at me. How do i get rid of this beep?

---

### Post by taurus on 2007-11-19
Are you using gnome-terminal?

Right button on gnome-terminal.  Then, pick Edit Current Profile... and uncheck Terminal bell.

---

### Post by jordank on 2007-11-19
thank you :)

---

### Post by Dr Small on 2007-11-19
And I just got a new case today and was glad that I had an internal speaker :p Oh, the dreaded months without it!

---

### Post by teryowen on 2007-11-19
for other people intrested i did it another way:

i edited the file
/etc/modprobe.d/blacklist

and appanded this line to it:
```

blacklist pcspkr
```

---

### Post by jordank on 2007-11-20
hrmm. the terminal profile didnt fix the problem i'm having. for example, if i'm in pidgin, and i backspace more characters than there are typed (eg, if i am backspacing at the beginning of my message) then i am beeped at by my computer. how do i fix this?

---

### Post by teryowen on 2007-11-20
Try my method above where you append that black list line it worked for me. and reboot after

---

### Post by natehatewindows on 2007-11-20
why do you backspace more that the amount of letters? ;)

---

### Post by Dr Small on 2007-11-20
> **jordank said:**
> hrmm. the terminal profile didnt fix the problem i'm having. for example, if i'm in pidgin, and i backspace more characters than there are typed (eg, if i am backspacing at the beginning of my message) then i am beeped at by my computer. how do i fix this?
System > Preferences > Sound > System Beep
Uncheck [Enable System Beep]

Dr Small

---

### Post by jordank on 2007-11-20
thanks :)

---

### Post by MickeWR on 2008-05-12
teryowen's solution got me thinkin, I got rid of the "Beep" when backspacing in the login menu by muting the "PC Speaker" in volume control.

---

