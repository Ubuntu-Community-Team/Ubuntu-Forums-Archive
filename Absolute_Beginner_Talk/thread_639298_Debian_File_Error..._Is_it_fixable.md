---
title: "Debian File Error... Is it fixable?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by XtremeBlaze on 2007-12-13
I have downloaded many applications with .deb extension, but some applications come up with the error **[COLOR="Red"]Error: Dependency is not Satisfiable:[/COLOR]**. Is there a way to solve this error, or does it simply mean that the application is not compatiable?

---

### Post by Rocket2DMn on 2007-12-13
You should download anything you can using the repositories.  It makes it easy to get a version that you know will work and be auto updated.  Using Synaptic, or apt-get, or aptititude to access the repositories will automatically get dependent packages when you get a specific program.  If you have to download from a third party source, they should be able to tell you what the dependencies are so you can either get those from the repos or download them separately as well.
Your program is probably compatible, it just needs other programs or libraries to accompany it.

---

### Post by szymon_g on 2007-12-13
try:

sudo dpkg -i file.deb

get some errors

than :
sudo apt-get install -f

use it for your own risk

---

