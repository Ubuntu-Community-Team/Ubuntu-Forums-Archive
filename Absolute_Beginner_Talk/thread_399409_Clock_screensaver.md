---
title: "Clock screensaver??"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Acupuncture Doc on 2007-04-02
Is there any way to get a clock screen saver for Gnome ?

I love the KDE analog clock screen saver, it would  be nice to have that one.

Thanks !!

---

### Post by Happy_Man on 2007-04-02
Have you searching Synaptic for the kde screensaver pack? They must be on there, and it'll have your screensaver in it, hopefully.

---

### Post by Pippa on 2007-04-12
Yes, that's a really great screensaver.  I've searched symaptic and had no luck.  Maybe I'm blind!  Hope someone can find it.

---

### Post by Sbarton on 2007-04-12
Have you looked at the KDE screensavers that are in synaptic?
regards

---

### Post by dilaudid on 2007-10-16
I posted this in a similar thread:
You can use the gltext screensaver in Feisty Fawn, like this:
```
#back it up in case
cp /usr/share/applications/screensavers/gltext.desktop ~/gltext.backup
# edit the file
sudo vi /usr/share/applications/screensavers/gltext.desktop
```
When you are in the file you need to change the line that says:
```
Exec=gltext -root
```
to:
```
Exec=gltext -root -front -text '%l:%M:%S %p'
```
for more options look at the man page:
```
man gltext
```

---

