---
title: "Where is the location of the linux source directory or source tree?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by sheeep on 2006-11-28
I'm trying to install linux-wlan and get to the configuration point where it asks which builds it will install. 

After selecting them all it says:

> Linux source directory [/lib/modules/2.6.15-27-386/build]:

when I hit enter to that it says configuratoin failed.

I think I need to know the location of the linux source tree.

Anyone?

---

### Post by taurus on 2006-11-28
Source is in /usr/src while the headers are in /usr/lib/"kernel number".  Looks to me like you need to install the headers for the version of your kernel...

---

### Post by sheeep on 2006-11-28
I'm totally lost when it comes to kernel installation. I've made a few threads and read about it all over but every time I get no where.

Anyone have a link to an easy detailed tutorial?

---

### Post by taurus on 2006-11-28
Run this command from a terminal to see which version kernel you run.

```
uname -r
```
Then, open synaptic, System -> Administration -> Synaptic Package Manager -> Search, and type in the version of your kernel.  Install the headers from the list...

---

### Post by nickburns on 2006-11-28
To get the headers

sudo apt-get install linux-headers-`uname -r` 

then they can be found at

/usr/src/kernel/include

---

### Post by sheeep on 2006-11-29
Version 2.6.15-27-386, i'll try what nickburns said to get them.

---

### Post by sheeep on 2006-11-29
When I try

> sudo apt-get install linux-headers-`uname -r`

it returns:

> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-uname-r


---

### Post by taurus on 2006-11-29
Try

```
sudo aptitude update
sudo aptitude install linux-headers-2.6.15-27-386
```

---

### Post by sheeep on 2006-11-29
Annnd... I think I got it to work with taurus's method.

So now that the headers are installed, err. Well, whats next? 

What should I enter when the linux-wlan prompts me to enter the source directory?

---

### Post by taurus on 2006-11-29
What's the output of this command?

```
ls -la /usr/src
```

---

### Post by nickburns on 2006-11-29
/usr/src/kernel/include

or 

/usr/src/linux-headers-2.6.15-27-386

---

