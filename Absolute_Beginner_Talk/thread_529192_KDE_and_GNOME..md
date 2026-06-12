---
title: "KDE and GNOME."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-08-18
I would like to run both KDE and GNOME.

But I have a few things worrying me, in places that describe what I'm wanting to do its worded to sound like I would be replacing GNOME - which I don't want to do.

Also, I want to know how installing KDE would effect GNOME, and vice-versa.

Thnx

---

### Post by taurus on 2007-08-18
You can have both Gnome and KDE on your machine at the same time.  You just install KDE if you already have Gnome.  At the GUI log in screen, you just pick which window manager you want to use for that session.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by Kitsun on 2007-08-18
Okay, another question.

Would it be possible to install kubuntu-desktop from my Kubuntu CD?

---

### Post by Bachstelze on 2007-08-18
Certainly. Just do

```
sudo apt-cdrom add
```

Then instert your CD and press Enter. When Apt is done scanning it, do

```
sudo aptitude update
sudo aptitude kubuntu-desktop
```

(For a faster KDE experience, if you don't need all the bells and whistles of Kubuntu, you can also use *kde-core*, which will give you a minimal KDE desktop. Of course, you can always add more applications afterwards.)

---

### Post by Sef on 2007-08-18
> Would it be possible to install kubuntu-desktop from my Kubuntu CD?

Do you want to dual boot Ubuntu and Kubuntu?

---

### Post by Bachstelze on 2007-08-18
> **Sef said:**
> Do you want to dual boot Ubuntu and Kubuntu?

I think he meant getting the KDE packages from a Kubuntu CD rather than from teh Interweb. Must have a slow connection.

---

### Post by kavon89 on 2007-08-18
I actually just installed KDE. Now I can easily boot into which ever one I want. CTRL+ALT+Backspace. Then go to Options -> Session. Choose KDE.

(I like KDE now. :D Time to install a fresh Kubuntu.)

---

### Post by taurus on 2007-08-18
> **HymnToLife said:**
> Certainly. Just do

```
sudo apt-cdrom add
```

Then instert your CD and press Enter. When Apt is done scanning it, do

```
sudo aptitude update
sudo aptitude kubuntu-desktop
```

(For a faster KDE experience, if you don't need all the bells and whistles of Kubuntu, you can also use *kde-core*, which will give you a minimal KDE desktop. Of course, you can always add more applications afterwards.)

Shouldn't that be

```
sudo aptitude install kubuntu-desktop
```

---

### Post by Sef on 2007-08-18
> I think he meant getting the KDE packages from a Kubuntu CD rather than from teh Interweb. Must have a slow connection.

I just like to check to make sure I clearly understand what the asker wants.

---

### Post by Kitsun on 2007-08-19
> **Sef said:**
> I just like to check to make sure I clearly understand what the asker wants.

Yeh, Ive gone over my downloads for the month, so its a 64kbs connection for the moment.

I don't want to dual boot because that would involve shutting the entire system down and starting it up again, Also the partition program yelled at me because I wanted more than 4 partitions, so dual booting Kubuntu and Ubuntu isn't possible.

---

