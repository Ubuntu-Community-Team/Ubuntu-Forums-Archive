---
title: "Installing bcmw15 error"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by domiflichi on 2007-07-14
I followed some instructions for installing my Dell WLAN 1390 card here:
[http://pervasivecomputing.net/ubuntu_feisty_7_04_on_dell_inspiron_e1505]("http://pervasivecomputing.net/ubuntu_feisty_7_04_on_dell_inspiron_e1505")

And got all the way to the following line:
```
sudo ndiswrapper -i /path/to/bcmw15.inf
```

and that is where it gave me the following error:
```
installing bcmw15
couldn't open /home/jamie/delldrivers/wlan/bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.
```

So I don't know if it's obvious or not, but the actual command I entered for that line was:
```
sudo ndiswrapper -i /home/jamie/delldrivers/wlan/bcmw15.inf
```

What I did before I ran this command, is downloaded the drivers for my Dell laptop (Inspiron 6400) in my Windows OS, extracted the files, then I copied just the files in the directory that contained the bcmw15.inf file to '/home/jamie/delldrivers/wlan'...there were several other files outside this directory that I did not copy over.

One more thing that I'm not sure if it's obvious or not, but I'm a total Linux noob, so please be specific with me.

(I hope I posted this in the right category...it seemed like a general problem I'm having, not really a network-specific problem.)

Thanks!

---

### Post by bobplano on 2007-07-14
i think that you also need the package ndiswrapper-common unless ndiswrapper-utils-1.9 depends on it so make sure you have both installed```
sudo aptitude update
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by alex_anthony on 2007-07-14
the file is bcmwl5.inf, not bcmw15.inf
with an l(L), not a 1 (one)

---

### Post by domiflichi on 2007-07-14
Alex_Anthony...you're right! Boy do I feel silly right about now. I guess that's why I'm supposed to be wearing glasses. Once I issued the correct spelling, no errors!
Well hopefully I won't run into any more problems with this part. 
Thanks.

---

