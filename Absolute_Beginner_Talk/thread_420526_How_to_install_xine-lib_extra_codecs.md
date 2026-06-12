---
title: "How to install xine-lib extra codecs?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Tispho on 2007-04-23
I need to install extra codecs for Amarok. 

I have the file zine-lib_1.1.4.org.tar.gz 

and I would like to install it, how would I do so?

---

### Post by taurus on 2007-04-23
Try something like

Applications -> Accessories -> Terminal
```
cd ~/Desktop  <-- assuming that's where you saved it to
tar xvzf zine-lib_1.1.4.org.tar.gz
cd zine-lib_1.1.4.org
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure
make
sudo make checkinstall
```

---

### Post by Tispho on 2007-04-26
Didn't work.

and I believe its xine not zine

after 
./configure 
make
sudo makecheckinstall

does not install. Wrong code. script, whatever you call it. 

I am so use to just double clicking on windows to install codecs.

---

### Post by Seisen on 2007-04-26
Did an error pop-up when you tried that?

---

