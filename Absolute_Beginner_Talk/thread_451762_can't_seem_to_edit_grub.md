---
title: "can't seem to edit grub"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by muggins on 2007-05-22
When I open terminal and type in gksudo gedit /boot/grub/menu.lst nothing happens, I just get another prompt. Tried different searches, not sure what is or isn't going on.

---

### Post by earobinson on 2007-05-22
how about sudo ```
gedit /boot/grub/menu.lst
``` Also can you do ```
cd /boot/grub
cat menu.lst
```Please cut and paste any and all errors, thanks.

---

### Post by Ek0nomik on 2007-05-22
```
gksudo gedit /boot/grub/menu.lst
```

You just get another prompt as in the line is done, and it skips to another line saying xxx@yyy?

---

### Post by earobinson on 2007-05-22
> **Ek0nomik said:**
> ```
gksudo gedit /boot/grub/menu.lst
```

You just get another prompt as in the line is done, and it skips to another line saying xxx@yyy?
gksudo is the gui version (it will pop up a gui prompt, thats what I asked for sudo)

---

### Post by Ek0nomik on 2007-05-22
Why would someone want a GUI password prompt?

---

### Post by eldepeche on 2007-05-22
> **Ek0nomik said:**
> Why would someone want a GUI password prompt?
Well, if you're running administrator programs from the menu, it's pretty necessary. Some people like the screen-darkening thing as well.

---

### Post by Ek0nomik on 2007-05-22
> **eldepeche said:**
> Well, if you're running administrator programs from the menu, it's pretty necessary. Some people like the screen-darkening thing as well.

If you are already typing in the terminal, why not just stay in the terminal?  Doesn't make sense to me...

---

### Post by muggins on 2007-05-22
Problem was I didn't have gedit installed, am using xubuntu. Substituted mousepad in its place and presto it worked. Changed the timeout to 30 sec from 10 sec. How would I put windows xp as the first choice so other family won't have to worry about the bootup options? Thanks for all the help.

---

### Post by Ek0nomik on 2007-05-22
> **muggins said:**
> Problem was I didn't have gedit installed, am using xubuntu. Substituted mousepad in its place and presto it worked. Changed the timeout to 30 sec from 10 sec. How would I put windows xp as the first choice so other family won't have to worry about the bootup options? Thanks for all the help.

You should just be able to change the order of the Titles.

---

### Post by Patrick K on 2007-05-22
Don't change the order of the entries. Look at the line "default num". The install default is "0" (the first OS listed). Change this to the number you want to default to. When counting, the list starts at "0" and be sure to include the "Other operating systems:" when counting (as it counts as one of the OS's).

---

### Post by lurnin9 on 2007-05-23
I'm using the LiveCD from Ubuntu Linux Bible.  It has Edgy, with GNOME.

I'm trying to install to an external USB drive (to boot from), and the install has failed at a new point each time (but it always gets further along).

The last time, the only step that failed was installing grub.  And there's no 'grub' entry in /boot.  Is there a quick and dirty way to install grub only, without trying to redo the entire install from the LiveCD?

I hope this is related enough to the OP.

(My searching of the forum didn't seem to find any real matches to this question.)

---

