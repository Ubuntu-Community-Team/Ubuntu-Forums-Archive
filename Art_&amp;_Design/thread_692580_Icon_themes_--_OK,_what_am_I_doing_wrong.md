---
title: "Icon themes -- OK, what am I doing wrong?"
date: 2008-02-09
forum: Art &amp; Design
---

### Post by fredbird67 on 2008-02-09
There's an icon theme on GNOME-Look.org I downloaded since I like the color scheme of these icons.  Basically, they kinda copy the Human icon theme, but instead of the folder icons being orange, these are a very rich shade of green, which I happen to like.

However, there is something else about this icon theme I do NOT like one little bit.  Where the Ubuntu Human theme uses the Ubuntu logo, the creator of this green icon theme I've found replaces it with a marijuana leaf, and as a Christian, illegal drugs are something I take a pretty dim view of.

I tried taking matters into my own hands by going into the /usr/share/icons/Cassandra folder (I'm running Linux Mint, BTW) and found the corresponding icons that have the Linux Mint logo, and I tried a simple copy, paste, and replace of the marijuana-leaf icons with the Cassandra icons (they have the same filenames, BTW).

I was hoping that that would do the trick, but instead, I ended up with a malfunctioning icon theme that displayed nothing but a black screen for its icon in the icon theme list, and selecting that one instead gives me the next theme in line, so there's obviously something I'm not doing right...

Again, I like the shade of green used on the folder icons in this icon theme, but as a Christian, I want nothing whatsoever to do with the marijuana leaf icons.  Does anyone know how to properly do this?  If someone could help me out here, I'd really appreciate it.

Thanx in advance,
Fred in St. Louis, MO USA

---

### Post by exploder on 2008-02-09
There is a hidden folder in your Home directory that has the icons. Replace the offending icons there first, then copy this folder and as root place the folder in /usr/share/icons/, so they will be availible when you use root privileges.

---

### Post by fredbird67 on 2008-02-10
Yup, you're right -- it sounds like a permissions issue.  I remember something similar to this happening once when downloading some themes for K3B back when I was a KDE user (didn't like what I saw in KDE4, and so I decided to switch to either GNOME or Xfce, ultimately going with GNOME), and they wouldn't show up -- came back to trip me up again and I didn't realize it! LOL

Many thanks, Exploder.

PS -- copying the Linux Mint logo files to something in my home folder, sudoing to that and changing the permissions or ownership on them will also work, right?

---

