---
title: "ipods"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by daz4126 on 2006-12-07
Hi everybody,

I know this is a total noob question, but I have only just yesterday got one of those ipod things and am a bit stuck....

How do I get songs on the damn thing in ubuntu?

I have tried gtkpod and keep pressing sync, but nothing seems to happen.

It is only a small ipod nano, so won't hold many songs. For this reason I can't sync it with all my music, so would like to set up a folder where I keep songs that I want it to sync with. So if I add some songs to this folder then plug my ipod in, these songs will go onto the ipod automatically. I would also like to subsribe to some podcasts and when they are updated have them automatically put onto my ipod. Is any of this possible? If it is, what would anybody recommend as the best software to use?

I really really don't want to have to go into windows just to use this thing, so please help.

DAZ

---

### Post by szf on 2006-12-07
Is the nano mounted?

In a Terminal (Applications -> Accessories -> Terminal) with it plugged in and turned on:
```

$ mount

```

Also see if the summary device drivers are loaded:
```

$ modprobe usb-storage

```

sidebar: I have a 2nd-gen iPod (firewire interface), so device drivers like ohci1394 and sbp2 is what I modprobe.

As for integrated apps: Gtkpod, Rhythmbox, Banshee, I suppose Amarok, too.

---

### Post by Obor on 2006-12-07
[This page should give you some answers.]("http://doc.gwos.org/index.php/IPod") Hope it helps.

---

### Post by Seine on 2006-12-07
After a little while, if you find the native iPod firmware troublesome, try giving RockBox firmware a try. You can then just treat it like a USB disk and move files back and forth manually.

---

### Post by daz4126 on 2006-12-28
Thanks for all the replies to this everybody. Just thought I'd say that after trying lots of different solutions, I settled on Banshee - it recognises my ipod, transfers songs (and converts formats, but struggles with wma), has a podcast plugin and is in active development. It also rips and burns CDs and has a good search facility.

DAZ

---

