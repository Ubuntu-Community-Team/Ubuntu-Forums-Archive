---
title: "Turn Ubuntu back into Debian"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by manofsteel on 2006-02-26
Is there a way to Ubuntu back into Debian?

---

### Post by John.Michael.Kane on 2006-02-27
Get the right debian source list, and you should be able to apt get your way to debian..
```
#Debian
deb ftp://ftp.no.debian.org/debian/ sarge main contrib non-free
deb-src ftp://ftp.no.debian.org/debian/ sarge main contrib non-free

#Debian Non-US
deb http://non-us.debian.org/ sarge/non-US main contrib non-free
deb-src http://non-us.debian.org/ sarge/non-US main contrib non-free

#Debian security updates
deb ftp://security.debian.org/debian-security/ sarge/updates main contrib non-free
deb ftp://security.debian.org/debian-security/ stable/updates main contrib non-free
deb-src ftp://security.debian.org/debian-security/ sarge/updates main contrib non-free
deb-src ftp://security.debian.org/debian-security/ stable/updates main contrib non-free

deb http://ftp.no.debian.org/debian/ stable main non-free contrib
deb-src http://ftp.no.debian.org/debian/ stable main non-free contrib

#mplayer, xine
deb ftp://ftp.nerim.net/debian-marillat/ sarge main
#backports, uoffisielle pakker
deb http://www.backports.org/debian/ sarge-backports main
deb http://ftp.debian-unofficial.org/debian/ sarge contrib main non-free restricted
#Libranet
deb http://libranetlinux.com/ updates/2.8/
deb http://libranetlinux.com/ security/2.8/

# The Libranet archive must be the last entry:
# deb http://archive.libranet.com/archive/libranet/ cedar main
# deb-src http://archive.libranet.com/archive/libranet/ cedar main
coyopil is offline 	Reply With Quote
```

---

### Post by engla on 2006-02-27
Is this possible all the way?
I imagine you have to replace virtually every package on the system with the debian version -- what if binary incompatibility problems stops the installation tools when the replace is made half-way?

---

### Post by xhie on 2006-02-27
If you want Debian why not just go download the 12 cd's and install Debian?

---

### Post by loupy on 2006-02-27
You do not need to download all 12cd's in order to install Debian - the first CD will do just fine and then you can apt-get (or synaptic) anything else you need.  You can also download just the netinst CD which is ~100MB and do the install that way as well (as long as you have an internet connection).

---

### Post by xhie on 2006-02-27
Even easier, why try to morph ubuntu back into debian then?

---

### Post by loupy on 2006-02-27
I'm not sure why anyone would try to "morph" back to debian.  Personally I think    it's a bad idea and would most likely break things as ubuntu is debian derived but not 100% debian compatible.  

My advice would be to save your /home settings and data and do a fresh install

---

