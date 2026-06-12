---
title: "Grub Default Question"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by BRuhling on 2006-02-08
I just got ubuntu up and running on my AMD X2 4200+ with dual SATA drives.  Windows is on one drive and ubuntu is on the other.  When I boot, the grub comes up and has ubuntu as the default os.  Because I primarily do games on the machine right now, I would prefer to have the default os as Win XP.  Is there a way to change this default in the grub?

---

### Post by welsh_spud on 2006-02-08
Yes you can change the order. Open up /boot/grub.conf and move the Windows entry above the Linux one. Do this with copy and paste, or drag and drop the text.

In terminal:
```
sudo gedit /boot/grub.conf
```

---

### Post by arctic on 2006-02-08
The file you need to edit is not grub.conf [-(  but /boot/grub/menu.lst.

---

### Post by Iowan on 2006-02-08
Rather than cut/paste in /boot/grub/menu.lst, you can change the default from "0" (which boots the first entry) to whichever one you prefer (remember, count from zero).

---

### Post by welsh_spud on 2006-02-08
> The file you need to edit is not grub.conf  but /boot/grub/menu.lst.

Whoops, I'm not at my Ubuntu laptop at the moment so that was all off the top of my head.

---

### Post by greeniearun on 2006-02-08
I tried to change, but it says I'm not the root. I installed ubuntu only hours before with the login name "arun". this is the only login name i've registered. how can i login as root? Now what should I do ?

---

### Post by Iowan on 2006-02-08
greeniearun:  Kinda hijacking a thread?  The password required is that of your user "arun" - if that's how you're logged in.

---

### Post by m.musashi on 2006-02-08
[QUOTE=greeniearun]I tried to change, but it says I'm not the root. I installed ubuntu only hours before with the login name "arun". this is the only login name i've registered. how can i login as root? Now what should I do ?[/QUOTE]

Cool, one I can answer. I'm new at this too.

Anyway, you need to use "sudo" which means something like super user do. It will ask for your password (the one for the first account you set up). This should do it for you.

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by TrendyDark on 2006-02-08
[QUOTE=greeniearun]I tried to change, but it says I'm not the root. I installed ubuntu only hours before with the login name "arun". this is the only login name i've registered. how can i login as root? Now what should I do ?[/QUOTE]

For future reference, to do anything from terminal as "root" use the command "sudo" (**su**per-user **do**) before the command you're about to run.

This command works for everything and if you ever recieve permission errors while installing, for example, a driver, use "sudo".:)

---

