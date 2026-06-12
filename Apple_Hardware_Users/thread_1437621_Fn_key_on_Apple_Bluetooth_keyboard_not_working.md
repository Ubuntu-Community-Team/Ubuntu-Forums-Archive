---
title: "Fn key on Apple Bluetooth keyboard not working"
date: 2010-03-24
forum: Apple Hardware Users
---

### Post by marlun on 2010-03-24
Hello,

I'm trying to use an Apple wireless keyboard with Ubuntu 9.10 (Karmic) but the fn key is not working at all. If I start up xev and hit the fn key it generates no event. What do I need to do for it to work. It seems as if it should work when viewing pages like

[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

Thanks in advance!

---

### Post by amvapor on 2010-03-24
Bump, I love the keyboard but I'm having a heck of a time figuring out a solution.

---

### Post by linuxopjemac on 2010-03-24
maybe you find a solution [here ]("http://www.mabishu.com/blog/2009/12/27/install-ubuntu-karmic-koala-on-a-macbook/")

---

### Post by amvapor on 2010-03-24
no, his fn key seems to work out of the box, 
my function key does nothing at all, the F# keys all work as F# keys (which is the way I want them to, but the fn key does not work to modify them which leaves me without home/end/pg_up/pg_dwn/ins/del keystrokes as well

curiously, many people mention the /etc/modprobe.d/hid_apple.conf file, however I don't have one on my machine...

---

### Post by marlun on 2010-03-24
> **amvapor said:**
> no, his fn key seems to work out of the box, 
my function key does nothing at all, the F# keys all work as F# keys (which is the way I want them to, but the fn key does not work to modify them which leaves me without home/end/pg_up/pg_dwn/ins/del keystrokes as well

curiously, many people mention the /etc/modprobe.d/hid_apple.conf file, however I don't have one on my machine...

My F1-F12 all work as F1-F12 and not as volume up/down etc. I also can't use home/end/delete etc.

And I also am missing the hid files like /etc/modprobe.d/hid_apple.conf

---

### Post by linuxopjemac on 2010-03-25
did you install pommed ?

```
sudo apt-get install pommed
```

---

### Post by xvila on 2010-03-25
> **linuxopjemac said:**
> did you install pommed ?

```
sudo apt-get install pommed
```

Yes, I even compiled the latest version (1.32) from the pommed project page.
In my new iMac pommed won't start. The error message is

DMI vendor name: [Apple Inc.]
DMI product name: [iMac10,1]
E: Unknown Apple machine: iMac10,1
E: Unknown Apple machine

So, it is not supported yet.

Pommed works perfectly on my MacBook 5.1 though

---

### Post by linuxopjemac on 2010-03-25
Just wait for pommed to work, you have a very new machine. You can't expect to have the same support as Apple gives you. A new release of pommed might solve these issues. I would just file a bug report upstream (to the pommed maintainers).

---

### Post by marlun on 2010-03-25
> **linuxopjemac said:**
> did you install pommed ?

```
sudo apt-get install pommed
```

I've not, I'll have to try it when I get home later today. However I've got a normal pc but an Apple Wireless Bluetooth Keyboard, is pommed still for me? Thanks!

---

### Post by xvila on 2010-03-25
> **linuxopjemac said:**
> Just wait for pommed to work, you have a very new machine. You can't expect to have the same support as Apple gives you. A new release of pommed might solve these issues. I would just file a bug report upstream (to the pommed maintainers).

You are right. My concern, though, is that looking at the CHANGELOG file and other files in the sources of pommed, one finds that they only contain descriptions for MacBooks (of different flavors), nothing related to iMac(s) of any sort (neither newer nor older).
As you suggest, I will contact the developers asking about iMac(s)

Thanks,
Xavi

---

### Post by linuxopjemac on 2010-03-25
[http://www.technologeek.org/projects/pommed/index.html](http://www.technologeek.org/projects/pommed/index.html)

---

### Post by amvapor on 2010-06-16
noticed this is one of the first hits on google when searching for this problem, I ended up moving my home directory to a seperate partition and installing ubuntu 10.04 from scratch, when I did, the mac keyboard came up with all it's features.

---

