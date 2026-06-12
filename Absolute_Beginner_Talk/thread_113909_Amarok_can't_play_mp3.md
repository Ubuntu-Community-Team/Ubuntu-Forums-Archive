---
title: "Amarok can't play mp3"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by danne on 2006-01-07
hi,
Suddenly, Amarok isn't able to play mp3 files...(with Gstreamer)
how can I fix this?

kind regards,

Danne

---

### Post by noigeaR on 2006-01-07
you have to install the gstreamer0.8-mad package for mp3 support. it's in the universe repositories, so make sure it's enabled in your sources.list then use synaptic to install or from a terminal
```
sudo apt-get update
sudo apt-get install gstreamer0.8mad
```

---

### Post by danne on 2006-01-07
darn,
I installed the package and lame encoder but still he says the gst-engine can't play the file...

---

### Post by JimmyBEng on 2006-01-07
after installing the new gstreamer packages you need to register them.
```
gst-register-0.8
```

---

### Post by danne on 2006-01-07
thx...but prolly the reboot also did the trick for a newbie like me ;) 

....those f*cking windows habits aren't still out of my head I guess ;) 

byebye!

---

### Post by pressman157 on 2006-01-20
Thanks for the posts. Saved me hours.

---

### Post by wcks48 on 2006-03-25
beside using the code
sudo apt-get update
sudo apt-get install gstreamer0.8mad
to update and install gstreamer0.8mad, is there any other way? because, after the update, my knosole say could not founf the gstreamer0.8mad file, may i know what happen to me kubuntu? even i downloaded the gstreamer0.8mad, i can't make it successfully install in my kubuntu with the reason that lack of some other files such as libid... i forgot the names.. sorry. hopw could any one help me solve this problem. thanx.

---

