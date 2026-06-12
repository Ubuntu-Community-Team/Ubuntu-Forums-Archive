---
title: "A question bout updating..."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-14
So we all agree that regular updates for Ubuntu arent that small, so I figure, if I regularly update my system; each week bout 20-30mb, that would be bot 100mb a week, and more than 1gb a year right?But this is what interests me...if I had e.g. updated ''x'' from version 1.00 to 1.10, and a week later I updated ''x'' from 1.10 to 1.20 does that mean that the 1.10 version file was deleted and replaced with the new version, and so it doesnt take up more space on hard disk.

Hope U get what I mean...actually, if I done updates regularly for 10years would I or not hve used up over 10gbs on my hard drive

---

### Post by kpkeerthi on 2008-03-14
Packages are downloaded (when you update ubuntu) as deb files and are stored in /var/cache/apt/archives. This folder will grow in size if you keep downloading updates. So it is recommended you do ```
sudo aptitude clean
``` once in a while.

---

### Post by kpkeerthi on 2008-03-14
A newer version of a package is installed in-place of the last version of the same space. So the **installed size** of a package does not drastically change if you continue to receive updates for it over time (say 10 years). But, like I said above, the **downloaded** size of a package may grow if you do not 'clean' the apt cache regularly.

---

