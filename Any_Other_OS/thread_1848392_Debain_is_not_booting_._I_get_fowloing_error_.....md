---
title: "Debain is not booting . I get fowloing error ...."
date: 2011-09-22
forum: Any Other OS
---

### Post by asifnaz on 2011-09-22
Debian is failing to boot I get this error . I am a new user and have  absolutely no idea what this error is and how to solve it .

I use ubuntu on my other PC so I am asking here .Kindly help me to solve it 

here is link to screenshot of the error 

[http://picpaste.com/Image0022-UGtCS6gB.jpg](http://picpaste.com/Image0022-UGtCS6gB.jpg)

I have an Ubuntu CD so I can boot live that CD . If that can be used to restore my system...? if yes how...???

I am new user i will really appreciate if you suggest me some step by step solution ...?

thank you

---

### Post by sffvba[e0rt on 2011-09-22
*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by el_koraco on 2011-09-22
There's some filesystem inconsistencies. Boot a live CD, and run  

```
e2fsck -f -y -v /dev/sdax
```

Where x is the number for your root partition (I'm guessing sda1, in case Debian is the only distro installed.

---

### Post by asifnaz on 2011-09-23
> **el_koraco said:**
> There's some filesystem inconsistencies. Boot a live CD, and run  

```
e2fsck -f -y -v /dev/sdax
```Where x is the number for your root partition (I'm guessing sda1, in case Debian is the only distro installed.


thank you . I took a hint from your answer and run

sudo fsck /dev/sda6 (using Ubuntu live CD)

everythingis fine now

---

### Post by el_koraco on 2011-09-23
Sweet!

---

