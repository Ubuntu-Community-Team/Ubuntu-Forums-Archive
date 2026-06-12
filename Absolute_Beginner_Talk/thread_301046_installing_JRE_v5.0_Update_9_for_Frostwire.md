---
title: "installing JRE v5.0 Update 9 for Frostwire"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by luvinit on 2006-11-16
I am trying to install JRE v5.0 Update 9, which I believe is required to make  Frostwire to work. I have followed the exact instructions in the offical edgy guide. I have downloaded jre-1_5_0_09-linux-i586.bin to the desktop, but when I use the "fakeroot make-jpkg jre-1_5_0_09-linux-i586.bin" it says the file doesn't exist. It is definitely there. Any ideas what the problem is? Thanks.

---

### Post by taurus on 2006-11-16
Why not move it to /opt and unpack it from there!!!

```
sudo mv jre-1_5_0_09-linux-i586.bin /opt
sudo chmod 755 jre-1_5_0_09-linux-i586.bin
sudo ./jre-1_5_0_09-linux-i586.bin
```
Otherwise, use automatix to install java on your machine...

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by happy-and-lost on 2006-11-16
To get Frostwire working, you need to type in...

sudo dpkg-reconfigure dash

And select "no".
Worked for me on my automatxally-installed frostwire.

---

### Post by luvinit on 2006-11-16
OK thanks a lot for the tip on frostwire, it has installed fine now. However, I find it very strange that the file is not recognised. I cannot move it via the terminal commands that you suggested because it doesn't see it, but it is there sitting on my desktop if I want to cut and paste it. Thanks all.

---

### Post by taurus on 2006-11-16
It means that you installed frostwire on your ~/Desktop directory!!!

---

### Post by luvinit on 2006-11-16
I have no idea why jre-1_5_0_09-linux-i586.bin isn't seen by the terminal, but I will forget about it, my head hurts. :p

---

### Post by SirShaggy on 2006-11-17
> **luvinit said:**
> I have no idea why jre-1_5_0_09-linux-i586.bin isn't seen by the terminal, but I will forget about it, my head hurts. :p

Just a thought here, try cd ~/Desktop/ first, then the mv command to get it into /opt

SirShaggy

---

