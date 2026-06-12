---
title: "RealPlayer 10 -- install"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by SCHagin on 2006-09-03
How can I install RealPlayer 10? I an new please give detailed instructions or point me to a URL that can give me detailed instructions.

Thanks for your help!

---

### Post by Miademora on 2006-09-03
I think [Automatix]("http://www.getautomatix.com/") can do that for you.

---

### Post by croak77 on 2006-09-03
Open a terminal and type;
```
sudo apt-get install libstdc++5
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb
sudo dpkg -i realplayer_10.0.7-0.0_i386.deb
```

---

### Post by SCHagin on 2006-09-03
When I type:
" sudo dpkg -i realplayer_10.0.7-0.0_i386.deb"

I get the following response
"dpkg: status database area is locked by another process"

What am I to do?

---

### Post by Omnios on 2006-09-03
> **SCHagin said:**
> When I type:
" sudo dpkg -i realplayer_10.0.7-0.0_i386.deb"

I get the following response
"dpkg: status database area is locked by another process"

What am I to do?

 Means that you probably had synaptic open when you tryed dpkg this locks it so all you have to do is close synaptic when you do dpkg

---

