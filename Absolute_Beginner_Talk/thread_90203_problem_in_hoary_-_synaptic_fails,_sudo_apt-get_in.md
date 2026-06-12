---
title: "problem in hoary - synaptic fails, sudo apt-get install -f doesn't work"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by |3lack|ce on 2005-11-14
Ok, I'm an absolute noob at Linux, having had a sco class 7 years ago and zero other exposure. Please be gentle. 

After much difficulty learning aptitude and installing what was necessary to get to the desktop after a new install, I finally got Hoary up and running last night where even I, the new guy, can work from it - now the problem.

I'm running an nvidia graphics card - and I'm trying to use Synaptic to install nvidia-glx, and it's not working. Locks up hard, tells me there's a problem. 

Ok, so I toodle on over to root terminal and try apt-get install -f.  It acts like nothing's wrong.   Synaptic still doesn't work. 

Now 2 other problems have popped up (actually these popped up before the synaptic thing - I was hoping the nvidia-glx install would fix them) - On boot, the 'setting sensors' check fails. Just after login, I get the message that Hal failed to initialize. 

How do I fix these problems?  Your help would be most appreciated!

---

### Post by Kyral on 2005-11-14
Setting sensors means that lm-sensors isn't properly configured.

So run```
sudo sensors-detect
``` and follow the directions there.

As for HAL.....I don't know

---

### Post by |3lack|ce on 2005-11-14
Thanks much for that one at least - Still hoping for feedback on Hal, and the synaptic problem.

---

