---
title: "Digital Clock Screensaver"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-09-26
Where can i get one? I NEED one!!!

---

### Post by dilaudid on 2007-10-16
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

