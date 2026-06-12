---
title: "Can't start KDE session manager - Ksmserver"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Ruslan Auroville on 2007-11-20
Hello!
I was trying to use KDE session manager called 'ksmserver' in order to add/remove startup programs. I found in Synaptic that ksmserver is already installed. But I can't find it in the list of installed applications. Does anyone know how can I start the program? 
Thanks.

My system: Kubuntu, KDE.

---

### Post by maybeway36 on 2007-11-20
What startup programs? Ksmserver is really more like a daemon, so it doesn't have an icon. If you look in ~/.kde/Autostart, thoguh, that might help.

---

### Post by Ruslan Auroville on 2007-11-20
Thank you for clarification. Is there a program for KDE similar to 'sessions' in Gnome? I would prefer to manage startups in the graphic user interface. I'm not so good in the shell.

---

### Post by .nedberg on 2007-11-20
KMenu->System Settings->Advanced tab->Session manager

Not sure what it is called in english...

---

### Post by Ruslan Auroville on 2007-11-20
I opened this Session Manager in Advance tab, but it does not show me what programs are there to start automatically. I'm not sure if it is the same thing as Sessions in the Gnome. Though I might be mistaken?

---

### Post by Ruslan Auroville on 2007-11-20
> **maybeway36 said:**
> What startup programs? Ksmserver is really more like a daemon, so it doesn't have an icon. If you look in ~/.kde/Autostart, thoguh, that might help.

I found in the Synaptic a program for KDE called 'kcontrol-autostart', by description it seemed to me to be the program I needed. I installed it, but again could not find in the list of installed programs. Is it the right one? How to find and start it? 
Thanks.

---

### Post by maybeway36 on 2007-11-20
Look to see if it's in the KDE Control Center (kcontrol.)

---

### Post by Ruslan Auroville on 2007-11-20
> **Ruslan Auroville said:**
> I opened this Session Manager in Advance tab, but it does not show me what programs are there to start automatically. I'm not sure if it is the same thing as Sessions in the Gnome. Though I might be mistaken?

Sorry .nedberg, I found what you meant - it is called Service Manager. But somehow it shows only KDE stuff which running, but not other programs. Anyway thanks for advice, it is already something, at least I can see a part of the total picture.

---

### Post by Ruslan Auroville on 2007-11-20
> **maybeway36 said:**
> Look to see if it's in the KDE Control Center (kcontrol.)

maybeway36, I am not able to find KDE Control Centre. Where do I look for it?
Thanks

---

### Post by fscodelaro on 2007-11-22
Run

```
kcontrol
```

That should make it.

---

### Post by Ruslan Auroville on 2007-11-22
Thank you, fscodelaro!
It worked.

---

