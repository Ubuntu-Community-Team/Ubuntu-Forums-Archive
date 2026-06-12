---
title: "Failing to install java"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by DeltaDog on 2007-06-02
ok, this is basicly my first post ever. Anyway. my brother an i play runescape (:cry: say what you want...) and point is, everytime when we try to install java, it fails. Is java even compatable with ubuntu? if it or if theres something im missing, can anyone help me?

---

### Post by jonward0690 on 2007-06-02
Well I had lots of trouble like you did I tried installing it and broke my synaptic manager like three time.I would recomend installing automatix for this one plus you can install other usefull thing with them like frostwire.Here is the link [www.getautomatix.com/wiki/index.php?title=Installation](www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by kernel tom on 2007-06-02
do it thru the terminal

sudo apt-get install sun-java6-bin

you will be asked to agree to their licensing 

press F12
select Yes

then it should install

then do
sudo apt-get install sun-java6-plugin
sudo apt-get install sun-java6-jdk

then 
sudo update-alternatives --all

and make all ur paths point to java6 directories

---

### Post by DeltaDog on 2007-06-02
kinda helpful, but fails first step
"Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-bin
"

---

### Post by zvacet on 2007-06-02
Chek that you have all repositories open.**system>administration<software properties>chek all boxes and reload**

In synaptic in search box type** sun** and after that select wich java you want to install.

---

