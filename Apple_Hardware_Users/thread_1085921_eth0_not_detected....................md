---
title: "eth0 not detected..................."
date: 2009-03-03
forum: Apple Hardware Users
---

### Post by ssanupam24 on 2009-03-03
hello everybody actually i hav installed ubuntu 8.10 n i am not able to config DHCP server n client. eth0 is also not detected in network tools(network device)... i am not able to connect to home network...
In /etc/network/interfaces only loopback interface is shown instead of eth0...
plz help me....
macbook pro 2.2, 120GB, core 2 duo..

---

### Post by cyberdork33 on 2009-03-03
is the sky2 module loaded?

---

### Post by ssanupam24 on 2009-03-04
no.... but i hv read in forums that people r facing probs by loading sky2 module so they r using sk98lin... hv u tested it?? if yes then how to load it??

---

### Post by cyberdork33 on 2009-03-04
you should use the sky2 module.

I have no idea what that other module is.

Can you link to some people reporting some of these so-called problems?

---

### Post by ssanupam24 on 2009-03-04
ya sure:-
[http://ubuntuforums.org/showthread.php?t=294642](http://ubuntuforums.org/showthread.php?t=294642)
[https://bugzilla.redhat.com/show_bug.cgi?id=487894](https://bugzilla.redhat.com/show_bug.cgi?id=487894)
if u hav not faced any prob then plz tel me how to load it....

---

### Post by cyberdork33 on 2009-03-04
> **ssanupam24 said:**
> if u hav not faced any prob then plz tel me how to load it....
```
sudo modprobe sky2
``` Though it should be loading automatically... If that works for you, then you should add 'sky2' to your /etc/modules file.

EDIT:

The first link is quite an old post, and when sky2 was very young. I don't think those problems are an issue anymore.

The second link appears to be a problem specifically with booting an image over ethernet. (it also refers to linux 2.6.29 which is not used by any release of Ubuntu, yet)

---

### Post by Elv13 on 2009-03-05
SKY2 broke yesterday in jaunty (at least for me) I am talking from OSX (...) right now. Both network are now broken (for 2 different reason). I don't know if it is related.

---

### Post by cyberdork33 on 2009-03-05
I did a fresh install with the alpha 5 cd yesterday and the sky2 module has been working fine with all updates on my MBP4,1 and my iMac5,1

---

### Post by ssanupam24 on 2009-03-07
sky2 module is not loading.... wen i give the above command it does nothing...plz tell me in detail...

---

### Post by cyberdork33 on 2009-03-08
> **ssanupam24 said:**
> sky2 module is not loading.... wen i give the above command it does nothing...plz tell me in detail...
the command will give no feedback... use 'lsmod' to list currently loaded modules. if it is not listed there, then check your dmesg for errors.

---

