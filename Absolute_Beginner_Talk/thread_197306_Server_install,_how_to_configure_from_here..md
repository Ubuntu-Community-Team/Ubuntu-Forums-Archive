---
title: "Server install, how to configure from here."
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-15
All I want is icewm (with rox filter), dillo, abiword, gaim, and xine.  I have completed the base install, how can I only install the things I want from here?  Can I start from xubuntu's cd?

---

### Post by bruce89 on 2006-06-15
```
sudo aptitude
``` is a package manager you can use to install more programs, although you might need to uncomment the Universe lines is /etc/apt/sources.list with nano to get some of these programs.

---

### Post by WADemosthenes on 2006-06-15
This code installs icewm and minimal components: 

sudo apt-get install gdm x-window-system-core xterm icewm menu mozilla-firefox abiword synaptic 

(found: [https://wiki.ubuntu.com/Installation/LowMemorySystems)](https://wiki.ubuntu.com/Installation/LowMemorySystems)).

Can I substitute firefox for dillo and opera? and add xine? so:

sudo apt-get install gdm x-window-system-core xterm icewm menu dillo opera abiword synaptic xine

?? Also, what other aplications may I need?

Edit: I'm new at this, so I'm going to install xubuntu first and add from there.  It will be easier, and I won't need as much help.

---

### Post by bruce89 on 2006-06-15
Opera is not in the repository, so that won't work.

---

### Post by WADemosthenes on 2006-06-15
I'll have to get that from the opera web site later.  

About xubunut, on base install it has stalled right at 78% two times in a row.  I'm going to try again, what could be the problem though?

---

### Post by WADemosthenes on 2006-06-15
Okay, install is working now.  If I'm going to use icewm should I remove the other window manager?  If so, how can I do this?

And how can I get icewm to be the defalt window manager, for the computer to boot into it?

---

### Post by muep on 2006-06-15
You don't need to remove xfce, but if it bothers you, you can of course remove it.

To get icewm running, just select it in the login screen. It then asks you if you want to set it as default or just for one time.

---

### Post by WADemosthenes on 2006-06-15
Okay, I got in, and I installed the Rox filer.  But there are no icons!  How can I get the icons to work (and Rox, if it isn't working) in icewm.

For that matter how do you get them to work in the other desktop? (the one that comes with xubuntu)

---

