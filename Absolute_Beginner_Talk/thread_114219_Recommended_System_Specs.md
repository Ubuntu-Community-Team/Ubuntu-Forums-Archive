---
title: "Recommended System Specs"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by The Pinny Parlour on 2006-01-08
I notice that when application load, the whole system is / feels sluggish.  What are the recommended system specs?

I'm running:
Athlon 2400+
MB: SIS all in one
RAM 256 DDR 400Mhz
HDD 40 gig
CD-R/RW

I think that extra ram may help but would like others opinions.

Thank you

---

### Post by Mustard on 2006-01-08
256mb  is ok, but I've always felt better with 512mb.  Have you got a swap partition set up?

---

### Post by Madpilot on 2006-01-08
The only thing you're lacking is RAM - get at least another 256 in there, or up to a full 1Gb if possible.

I've got an AMD XP-M 2500+ w/ 1Gb RAM, and Gnome itself only feels sluggish when I've got the system running really, really hard - all eight virtual desktops full of apps, say.

---

### Post by poofyhairguy on 2006-01-08
Its the RAM. Gnome hates less than 512.

If you want you can try Xfce. It will be faster.

[https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29](https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29)

But with less features. It like RAM less.

---

### Post by The Pinny Parlour on 2006-01-08
[QUOTE=Mustard]256mb  is ok, but I've always felt better with 512mb.  Have you got a swap partition set up?[/QUOTE]


I'm not sure Mustard, I have the default ubuntu setup from the iso/disc.

---

### Post by Mustard on 2006-01-08
[QUOTE=The Pinny Parlour]I'm not sure Mustard, I have the default ubuntu setup from the iso/disc.[/QUOTE]

In all likelyhood you have in that case.  

This command in terminal would display your partions...

```
sudo fdisk -l
```

That should display all your partitions and one of them will have 'Linux swap'  at the end of it.

---

### Post by The Pinny Parlour on 2006-01-08
[QUOTE=Mustard]In all likelyhood you have in that case.  

This command in terminal would display your partions...

```
sudo fdisk -l
```

That should display all your partitions and one of them will have 'Linux swap'  at the end of it.[/QUOTE]


Yes, I have a Linux Swap.  :)

---

### Post by estel on 2006-01-08
Agree with what was said above, try another, more lightweight WM and see if you like it - some of them will definitely run faster.

---

### Post by The Pinny Parlour on 2006-01-08
[QUOTE=estel]Agree with what was said above, try another, more lightweight WM and see if you like it - some of them will definitely run faster.[/QUOTE]


But more RAM will hopefully help?

---

### Post by estel on 2006-01-08
More RAM always helps with everything :)

---

### Post by jobezone on 2006-08-22
> **The Pinny Parlour said:**
> But more RAM will hopefully help?

After getting the ram, look at the swappiness performance trick here : [http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/).
I have 512 M, but the system used too much swap too early, when there was enough free RAM to spare. This tweak helped things, and it's alot smoother using the system.

---

