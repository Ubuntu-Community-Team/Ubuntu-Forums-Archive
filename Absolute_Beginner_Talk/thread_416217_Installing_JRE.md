---
title: "Installing JRE"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by bluewagon on 2007-04-20
how do i install the JRE, i've tried
sudo aptitude install sun-java6-jre sun-java6-plugin
but it says ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java6-jre"
Couldn't find any package whose name or description matched "sun-java6-plugin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```
and it when i do java -version it says its 1.4.2

---

### Post by igknighted on 2007-04-20
you need to enable the universe repository.  Open synaptic, click on the setting menu, then repositories and enable it from that menu.  Then update and install

---

### Post by jiminycricket on 2007-04-20
If it still doesn't work, try 'sudo update-alternatives &#8211;config java' and choose the Sun Java version.

---

### Post by bluewagon on 2007-04-20
thank you very much, that solved the problem

---

