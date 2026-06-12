---
title: "scanning for m4a in amarok"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-06-16
i can easily play m4a songs individually, but i can't get amarok to add them when it scans for my collection. it plays, but doesn't add to collection.

i saw this problem on an old post, but there was no response..thought i'd post a new thread and cross my fingers!

---

### Post by jeroen2 on 2006-06-16
I have searched Amarok for this myself and found nothing. I suggest asking the amarok folks at: [http://amarok.kde.org/](http://amarok.kde.org/) .  And if it's impossible right now, requesting the feature for a future release.

Btw, isn't m4a the itunes format? Hmm, guess I could start bitching about closed, DRM'ed formats but I doubt anyone would want me to ;) 


~Jeroen

---

### Post by shanepardue on 2006-06-16
oh yeah..i hate the format too..wish i could convert them to ogg and forget the whole thing!!

thanks for your help!

---

### Post by shanepardue on 2006-06-16
ok!! i figured out that the new amarok fixes this bug. i did all of what it said to update, but this command doesn't work...what's wrong with it?

deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main

---

### Post by Lunar_Lamp on 2006-06-19
It's not a command :)

You need to add that line to your apt sources list which is located at /etc/apt/source.list

You can do this several ways, but the way I would do it is this:
 - open a terminal
 - type:
```
sudo gedit /etc/apt/sources.list
```
 - enter password if prompted
 - add the following lines:

```
## I added this line myself to get amarok 1.4 working
deb http://kubuntu.org/packages/amarok-14 dapper main
```

However, I will warn you - I am using Ubuntu with gnome on 6.06, and I was having problems with it crashing (though I think it was to do with my own weird network situation).

---

