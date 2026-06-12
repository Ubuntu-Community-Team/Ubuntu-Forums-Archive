---
title: "what is modprobe snd-bt-sco ?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-05-22
i was trying to make my bluetooth with the help of a thread.. and i stumbled upon this

modprobe snd-bt-sco

and it says FATAL: Module snd_bt_sco not found.

whats the problem ? how can i fix this ? thanks

---

### Post by HunkieChan on 2007-05-22
anyone ? what is it ? how can i fix it ?

---

### Post by HunkieChan on 2007-05-22
ugh, anyone ?

---

### Post by wormser on 2007-05-22
"[modprobe - program to add and remove modules from the Linux Kernel]("http://www.die.net/doc/linux/man/man8/modprobe.8.html")"

"[snd-bt-sco: a Bluetooth headset driver for ALSA]("http://64.233.167.104/search?q=cache:QSCwTDzZaGAJ:www.dcs.gla.ac.uk/~jp/snd-bt-sco/+snd-bt-sco&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")"

Modprobe adds or removes modules from the kernel.  It looks like there is no module to remove according to that error.  Try the following command to list your modules and see if it is in there.

```
modprobe -l
```

to make it easier pipe it into grep.

```
modprobe -l | grep snd-bt-sco
```

---

### Post by HunkieChan on 2007-05-22
when i try the second one, it doesnt show anything..how do i get it .. if its not there ?

---

### Post by angkor on 2007-05-22
Easy there Hunkie, stop bumping your thread every 10 minutes. ;)

AFAIK you don't need to modprobe the bluetooth module anymore in Feisty. Bluetooth btsco is in the repositories:

```
sudo aptitude install bluez-btsco
```

or use synaptic to install the package.

---

### Post by HunkieChan on 2007-05-22
but i did that.. it didnt help

---

### Post by wormser on 2007-05-22
> **HunkieChan said:**
> when i try the second one, it doesnt show anything..how do i get it .. if its not there ?

If the command returned nothing then it is not installed.  Did you try to search for bluez-btsco with apt-get?

```
apt-cache search bluez-btsco
bluez-btsco - Bluez Bluetooth SCO tool
```

Is it installed?  Did you run the command angkor gave you to install?  Post more details to help us help you.

---

### Post by HunkieChan on 2007-05-22
when i try the first one it says

bluez-btsco - Bluez Bluetooth SCO tool

what does that mean ? its same as the 2nd command.. how do install it if its not installed ?

---

### Post by Aetherius on 2007-05-23
```
sudo apt-get install bluez-btsco
```

and once you have bluez-btsco installed run

```
sudo modprobe snd_bt_sco
```

this will load the module.

You are trying to connect a bluetooth headset then?

After you've done the above you might be interested in looking at this
[URL="http://www.stgraber.org/category/gbtsco"]
Stephane Graber's gBTsco[/URL]

Aeth.

---

### Post by HunkieChan on 2007-05-23
i did what you told me to but i still get the error

> **Aetherius said:**
> ```
sudo apt-get install bluez-btsco
```

and once you have bluez-btsco installed run

```
sudo modprobe snd_bt_sco
```

this will load the module.

You are trying to connect a bluetooth headset then?

After you've done the above you might be interested in looking at this
[URL="http://www.stgraber.org/category/gbtsco"]
Stephane Graber's gBTsco[/URL]

Aeth.

---

### Post by alfirin on 2008-02-24
I face the same problem like you,too. I haven't found a solution yet...

---

### Post by HunkieChan on 2008-02-24
i dont know how i fixed it bro..  i think i re installed my ubuntu.. not that im asking you to .. keep looking for it.. you will get a solution

---

