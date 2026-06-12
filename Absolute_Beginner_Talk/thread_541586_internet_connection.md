---
title: "internet connection"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by penguino on 2007-09-03
I'm having trouble connecting to the internet via a wired connection on one of my laptop.  The wired connection is enable and is set to dhcp if a look at network tools, network device : Ethernet Interface (etho) chose me that it is not available. I know my router is working ok because I can connect to the internet using ubuntu on my mac (wireless or using the cable) connected to the router.  doe's any body have some advice for me?

---

### Post by anewguy on 2007-09-03
Post the output of the following back here:

lspci -C network

lspci

We need some information to see if we can help you.:)

---

### Post by Benjamin G on 2007-09-03
Penguino, funnily I was in a similar situation a couple of days ago ([http://ubuntuforums.org/showthread.php?t=540566](http://ubuntuforums.org/showthread.php?t=540566)).  It wasn't fun at the time!  It would save you time if you could post as much info as possible in addtion to the output from the command anewguy has pointed out to you.  Additional useful info would include, but is not limited to, card manufacturer and model (if you know it), and possibly the output of the following commands:
```
ifconfig
```
```
lshw
```

Benjamin

---

