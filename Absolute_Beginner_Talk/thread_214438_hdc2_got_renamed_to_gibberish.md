---
title: "hdc2 got renamed to gibberish?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Fridericus on 2006-07-12
Help.

I have been trying to rename the hdc2 volume. Before it was just naamed hdc2, but after I changed its icon to a different PNG icon and restarted the volume is now named  _PNG and some funny looking sign.

I have tried to unmount and remount but the problem remains, I also tried to change the icon but its still named _PNG plus the mysterious sign.

If I select Properties it says Name: _PNG then a line break and the funny looking sign underneath, it says the same under Volume.

Can I change the name back? Its annoying!
In /media/ the drive is still named hdc2.

Thanks for any help.

---

### Post by Fridericus on 2006-07-12
Here is what the it looks like

[IMG]http://files.upl.silentwhisper.net/upload7/iconGib.jpg[/IMG]

---

### Post by Fridericus on 2006-07-12
Where is the name stored? I want to FORCE it to change it, this is pissing me off right now.

I tried to rename it via Nautilus by sudo nautilus - however when in properties and trying to change the name it gave me an error saying I can not change the name.


[COLOR="Red"]It seems renaming the drive in Windows made everything OK. Linux cant rename FAT32 drives it seems.[/COLOR]

---

### Post by grim1234 on 2006-07-17
I'd like to know how to do this too. Anyone have an answer?

---

### Post by helvetica on 2006-07-21
I've got the same problem, what can be done to resolve it?

---

### Post by OU812 on 2006-07-22
I don't think I know how to fix it. But here are a couple of things that may give you some clues.

```
$ dmesg | grep -i cd
```

$ = as user. This searches for cd drives. Also find devices.txt and find out what it says about your ide interfaces.

john

---

