---
title: "Is there a recovery on ubuntu"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by samarthancha on 2007-08-03
i have mistakenly deleted by desktop settings. I want them back. IS there a recovery or do i have to reinstall ubuntu. plz. answer.

---

### Post by splintercellguy on 2007-08-03
Desktop settings? Please clarify. Do you mean that you are unable to get to desktop?

---

### Post by samarthancha on 2007-08-03
actually. the desktop effects are deleted. the desktop is visible, but without the wobbly and cube effects. also, o cannot move or close windows. i have to use alt+f4.

---

### Post by splintercellguy on 2007-08-03
I'm not quite understanding your question, can you clarify?

---

### Post by Repent on 2007-08-03
Go to System/Preferences/Desktop Effects to see if you disabled them if so just enable them.

Hope this helps.
Repent

---

### Post by samarthancha on 2007-08-03
i tried to install compliz fusion. it said that it had broken files and need to be deleted. along with compliz, i also deleted 'desktop effects' found in SYSTEM-PREFERENCES. now, i no longer have the wobbly effect or the cube effect in my fiesty fawn. also, i cannot move or close windows. i hav to use alt+f4. is there a way to do a recovery? or do i need to reinstall ubuntu.

---

### Post by st33med on 2007-08-03
I believe there might be a soultion. Go to terminal and try this:
```
compiz --replace ccp
```

Does that work? Automate it so it starts on start-up by going to System>>Preferences>>Sessions. Add a startup program named "Compiz fusion" and put below it the code I gave you.

EDIT: YEA! 250th post!!! :D :D :D

---

### Post by asmoore82 on 2007-08-03
create a new username and login as that new user...
this will tell you/us if you have broken the system or if just your personal config is hosed.

---

### Post by Mr.Ganja on 2007-08-03
Yes there is a recovery in ubuntu. All i know is how to access it. reboot and in the GRUB boot loader select "recovery mode" This will just be a prompt, so someone else who knows how to fix your problem is going to have to tell how. That's all i know, hope it helps :)

---

