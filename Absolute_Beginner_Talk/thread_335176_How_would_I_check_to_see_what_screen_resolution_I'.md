---
title: "How would I check to see what screen resolution I'm using?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2007-01-09
Hello, what command should I type into terminal to check what screen resolution my notebook is using.

I have a hp pavilion dv4230us that use the 910GML chipset. I am wondering if I need to change my screen resolution like I've read about in the edgy wiki and some other posts.

---

### Post by ajmorris on 2007-01-09
i'm not sure how to do it from the shell but if you go to system > preferences and then screen resolution you can change it from there.

---

### Post by jimrz on 2007-01-09
> **crimesaucer said:**
> Hello, what command should I type into terminal to check what screen resolution my notebook is using.

I have a hp pavilion dv4230us that use the 910GML chipset. I am wondering if I need to change my screen resolution like I've read about in the edgy wiki and some other posts.

if you are using Gnome (Ubuntu), on top panel go to System > Preferences > Screen Resolution. For XFCE (Xubuntu) right click on your desktop and select Settings > Display

---

### Post by crimesaucer on 2007-01-10
Hey thanks, I had just assumed I would have to use terminal for that. 

Does anybody know the size of the xubuntu Default screen resolution?

There was only Default and 1024 x 768 @ 60 listed.

My hp screen size is 1280 x 768, do I need to install 915resolutions?

---

### Post by crimesaucer on 2007-01-10
So, I'm still hoping someone knows what the exact Default screen resolution is for xubuntu.

---

### Post by MkfIbK7a on 2007-01-10
well it is defaulted to the highest your monitor can handle...

---

### Post by crimesaucer on 2007-01-10
See, I would think that except that I've read that there is an issue with the intel 910/915 chipsets and wide screens. I know 15.4 inches isn't really that wide but the only size shown was 1024 x 768 @ 60.

...and then 5 seconds latter

You know what...lol...I was just about to put a link to the wiki page about intel resolution, and I saw that it was talking about screens larger than 20 inches.

My bad. Thanks for the info and help.

---

### Post by MkfIbK7a on 2007-01-10
no prob

---

### Post by mtron on 2007-01-10
for others:

```
cat /var/log/Xorg.0.log | grep -i "Setting mode"
```

---

### Post by Pobega on 2007-01-10
I use 915 resolution, works well on my monitor. Not sure on the exact size though, I think it's 14 in.

---

### Post by CujoQuarrel on 2007-01-12
I tried the command 

cat /var/log/Xorg.0.log | grep -i "Setting mode"

and got nothing? Anyone know what this means?

I'm also trying to get diff resolutions on this Inspiron 6000. The only choice I 
get is 1600x1200 in the pref option. 

I've modified the xorg.conf file but it seems to be ignoring it.

---

