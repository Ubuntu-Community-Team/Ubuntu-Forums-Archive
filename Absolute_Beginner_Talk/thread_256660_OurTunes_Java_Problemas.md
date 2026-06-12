---
title: "OurTunes Java Problemas"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by elmique on 2006-09-13
Hi, I’m having some Java problems.
The first time I downloaded OT42.jar file it worked very well.
On the other hand, I downloaded the Nokia PC Suite, and it worked fine.
The problem was, when I tried to run OurTunes, the Nokia Java Installer ran instead.
It seemed that the Nokia Suite re-assigned the .jar extension to the installer.
So I uninstalled the Nokia Suite, but the .jar file was left with no program associated.
I downloaded the new Java Runtime Environment, but it doesn't work.
¿What should I do?
](*,) 

Thanks and regards.

elmique

---

### Post by mjsoccer1 on 2006-09-13
Make sure you are using the right Java VM:

sudo update-alternatives --config java

Select the java-xxx-sun package.

---

