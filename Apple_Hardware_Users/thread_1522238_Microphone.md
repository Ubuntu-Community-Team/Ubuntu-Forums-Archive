---
title: "Microphone"
date: 2010-07-01
forum: Apple Hardware Users
---

### Post by what, what? on 2010-07-01
I just installed ubuntu alongside OSX and I want to set up my built in microphone on my macbook. I looked at the drivers thing but there were none to install. I tried to use the microphone on a voice chat program ut it didn't work. How do I do this? I have a macbook if that helps and Ubuntu 10.04

---

### Post by linuxopjemac on 2010-07-02
which MacBook?
```
sudo dmidecode -s system-product-name
```

---

### Post by what, what? on 2010-07-02
> **linuxopjemac said:**
> which MacBook?
```
sudo dmidecode -s system-product-name
```

MacBook 2,1

---

### Post by linuxopjemac on 2010-07-03
Maybe you need to unmute the mic channel

```
alsamixer
```

and unmute the channels with "m"

---

