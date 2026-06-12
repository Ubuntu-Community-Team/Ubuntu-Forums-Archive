---
title: "gnome-panel issue"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by raymondm on 2007-11-05
Sometimes when I boot up I don't get my gnome-panel 

then I type this into the terminal 

 gnomePid=`ps -e | grep 'gnome-panel' | awk '{print $1}'`


and get the process Id of the panel 

then I type this into the terminal 

kill -9 $gnomePid

after I type the kill command the panel shows up

why does this happen from time to time?

---

