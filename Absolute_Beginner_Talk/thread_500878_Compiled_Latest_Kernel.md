---
title: "Compiled Latest Kernel"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-07-14
Well, since im gretting no help in any other place.
i decide to post here.

as said, last night i compiled the latest Linux Kernel.
works great!

BUT, in Network, i ONLY have Wired or Dial Up.
there is no wireless, which i have

is tghere a way i can add it to the Kernel?

or is it more complicated?

---

### Post by wolfen69 on 2007-07-14
alot of people have to use ndiswrapper to get wireless working. there is plenty of documentation on it.

---

### Post by skymera on 2007-07-14
my wireless works!
in my older kernel

my freshly compiled kernel : in network admin i DONT have a choice to enable my wireless.
wired or dial up. rhats it.

---

### Post by walkerk on 2007-07-14
uh.. compiled the latest kernel for ubuntu? try this..

network manager:
```
sudo apt-get install network-manager network-manager-gnome wpa_supplicant
```

to run after install:
```
nmapplet --sm-disable
```

**or a better solution in my opinion is wicd**:
[download the .deb here]("http://wicd.sourceforge.net")
along with this you might need to install wpasupplicant in order to use wpa:
```
sudo apt-get install wpa_supplicant
```

to setup goto applications>internet>wicd

to run at boot include this in your systems>preferences>sessions:
```
/opt/wicd/tray-edgy.py
```

hope this helps

edit: now that i read your last post im not sure this will help..

---

### Post by skymera on 2007-07-14
i cant install with no connection.

all i  need to do is tyrn my connection on.
but i dont have an option in Network-Admin

the kernel is 2.6.22

---

### Post by walkerk on 2007-07-14
> **skymera said:**
> i cant install with no connection.

all i  need to do is tyrn my connection on.
but i dont have an option in Network-Admin

the kernel is 2.6.22

you cant use the wired connection? i guess its a desktop and its too far to run a cat5 cable..?

---

### Post by qamelian on 2007-07-14
When you configured your kernel options before compiling, did you remember to turn on support for you wireless? Did you build the new kernel based off you old config or did you do a new config from scratch?

---

### Post by skymera on 2007-07-14
my desktop is the other side of the house, 
upstairs

so a very long way to the router.

but thanks anyway

---

