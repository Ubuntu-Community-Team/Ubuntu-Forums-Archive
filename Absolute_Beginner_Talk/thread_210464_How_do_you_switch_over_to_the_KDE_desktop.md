---
title: "How do you switch over to the KDE desktop?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by leebrendalee on 2006-07-06
Hello, 

I think I'm using the desktop that came with ubuntu.  How does one get into KDE desktop.  Is it like windows?

---

### Post by lime4x4 on 2006-07-06
u have to install it. Then when u log in you can select your session

type this in a command window 

sudo apt-get install kubuntu-desktop

---

### Post by nalmeth on 2006-07-06
If you think you may want to remove it later, use 

sudo aptitude install kubuntu-desktop

For meta-packages with a lot of dependencies, aptitude will make life easier for you.

Otherwise apt-get is fine and dandy for single apps.

---

### Post by T700 on 2006-07-06
I'd very strongly suggest using the aptitude command rather than apt-get.  Aptitude will allow you to MUCH more easily remove a massive package like KDE, should you ever need to do so.

One line at a time: ```
 [SIZE=3]sudo aptitude update
sudo aptitude install kubuntu-desktop[/SIZE]
``` 
kubuntu-desktop rather than kde-desktop will give you a Ubuntu specific version of KDE.  See _[here]("http://www.psychocats.net/ubuntu/kde.html")_ for more details.

Paul

---

### Post by lime4x4 on 2006-07-06
forgot about that and kubuntu desktop is a huge package

---

