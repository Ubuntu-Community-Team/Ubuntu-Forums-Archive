---
title: "can't update a ubuntu pkg."
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by harryliddic on 2008-03-30
I am trying to update <b>amaya</b> an html editor from W3C. Version 9.55 is in the synaptic but I have gotten used to ver. 10 in windows. Ver. 10 comes in a ubuntu pkg so updating it I thought would be a slam dunk. I used <b>apt-get upgrade</b> but it said then I had I higher version in play. I tried <b>apt-get install</b> but it returned the same message. How do I either upgrade or kill the old amaya so that I can install the newer amaya

---

### Post by spydon on 2008-03-30
First do:
```
sudo apt-get remove amaya
```
and then just click this link and download and run the package [http://www.w3.org/Amaya/Distribution/amaya_10.0.1-0ubuntu1_i386.deb]("http://www.w3.org/Amaya/Distribution/amaya_10.0.1-0ubuntu1_i386.deb")

---

### Post by harryliddic on 2008-03-30
thanks alot

---

### Post by spydon on 2008-03-30
np, you can always press the star to thank me ;)

---

