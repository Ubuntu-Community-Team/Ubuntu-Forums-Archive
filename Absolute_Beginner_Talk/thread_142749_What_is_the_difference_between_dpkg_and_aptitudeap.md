---
title: "What is the difference between dpkg and aptitude/apt-get?"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-11
When installing a software via 'dpkg -i packageA.deb', will the dependencies required by packageA be downloaded and installed automatically (aka aptitude/apt-get ) or are all the required dependencies already built into packageA.deb package?

Thanks !

---

### Post by RJMacReady on 2006-03-11
When you **sudo apt-get**, if any of the packages are .debs, Aptitude calls **dpkg -i** to install them anyway. So, mix and match.

---

### Post by transactionlogfiller on 2006-03-11
You normally have to resolve dependancies manually with dpkg. Or use apt-get :)

---

### Post by Klaidas on 2006-03-11
More info if you're interested: [http://www.linux.org/lessons/interm/c191.html#INSTALL-STUFF](http://www.linux.org/lessons/interm/c191.html#INSTALL-STUFF)

---

### Post by BoyOfDestiny on 2006-03-11
[QUOTE=transactionlogfiller]You normally have to resolve dependancies manually with dpkg. Or use apt-get :)[/QUOTE]

This is solved in dapper, thanks to gdebi

[http://www.ubuntu.com/testing/flight5#head-84659e4a45b7a0e1147bb068022f6f3a04a22f8d](http://www.ubuntu.com/testing/flight5#head-84659e4a45b7a0e1147bb068022f6f3a04a22f8d)

Now I'll start putting dependencies in my debs (yay for checkinstall and manually entering dependencies...)

---

### Post by RJMacReady on 2006-03-11
[QUOTE=BoyOfDestiny]Now I'll start putting dependencies in my debs[/QUOTE]

Finally, someone thinking straight! \\:D/

---

### Post by engla on 2006-03-11
[QUOTE=BoyOfDestiny]This is solved in dapper, thanks to gdebi

[http://www.ubuntu.com/testing/flight5#head-84659e4a45b7a0e1147bb068022f6f3a04a22f8d](http://www.ubuntu.com/testing/flight5#head-84659e4a45b7a0e1147bb068022f6f3a04a22f8d)

Now I'll start putting dependencies in my debs (yay for checkinstall and manually entering dependencies...)[/QUOTE]
This is absolutely good news to ubuntuforums and all the users seeking help on installing 3rd party software!

---

### Post by Akhran on 2006-03-11
1) Will all dependencies installed automatically by gdebi be marked as 'automatically installed'?

2) When aptitude uninstalled a package, will aptitude also uninstalled all the dependencies installed by gdebi automatically?

Thanks!

---

