---
title: "What is that app that shows the CPU freq in real time?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-05-20
I had an app in my dapper install that resided on the panel and showed the scaled CPU frequency in real time and also allowed for manually setting the speed by clicking on it.

I don't remember if I got it from one of the repos or dl'd it from somewhere else.  I;m hoping somebody knows the name of it as I am old and senile -seriously!

TIA!

---

### Post by Kobalt on 2007-05-20
It's the cpu frq applet. Add it with a right click on your panel, then 'Add to the panel..'. Scroll down to Settings and System, here it is. 
To activate the possibility to change the frequency, you need to run this : ```
sudo dpkg-reconfigure gnome-applets
```
Answer yes when it asks if you want to give the root privilege to the cpu freq applet, and you're done.

---

### Post by Atomic Dog on 2007-05-20
That's it!  Thank you!!!

I have no memory...

---

