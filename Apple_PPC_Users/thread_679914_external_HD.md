---
title: "external HD"
date: 2008-01-27
forum: Apple PPC Users
---

### Post by jtbrookreson on 2008-01-27
I have a G3 500 ibook running 6.10, and I am more or less happy with it (I do have sound issues, as in no sound, but that is for another thread). I also have a 40 gig external HD. How do I get Ubuntu to recognize the darn thing?

2nd Question: Someone suggested that I run Xubuntu instead due to my older hardware. Can I install it on the external drive, and test drive it there? If so, how?

-JTB

Thank you very much.

---

### Post by ajgreeny on 2008-01-27
```
sudo apt-get install xubuntu-desktop
```or a synaptic install of the same, will add xubuntu to your current ubuntu.  You just chose at logon.
As for the external drive, most are recognised and mounted when pluged in, but a few aren't.  If your has a CD of windows/mac drivers that came with it, it will be a problem, and needs a better person than me to help you further.

---

### Post by jtbrookreson on 2008-01-27
to be honest, I have no idea about what type of what I have, other than it is a 40 gig HD connected through firewire. I was never a MAC guy, but a PC guy who bought a Mac and installed Ubuntu on it because it was cheap. When I plugged in the HD earlier today, I couldn't find it or see it, but I might not have been looking in the right places.

Now about Xubuntu.... If I install it by the means you suggested, will it disturb the Ubuntu I already have, or need me to partition the disk? I am a total Noob who is trying to get away from the evil Microsoft Empire. The last thing I want to do is screw up what is working (ubuntu 6.10) in an attempt to get faster....

Thanks again.

---

### Post by ajgreeny on 2008-01-28
Xubuntu-desktop will just be an option at login.  If you click the options button on the login screen, you will get the chance to change session type.  Just chose xfce to see what you think of xubuntu.  It will do absolutely nothing to your ubuntu setup, which will still be there exactly as you left it.  If you decide xfce is not for you just go back to gnome again in the same option button procedure as I just described.

---

### Post by stream303 on 2008-01-28
And later if you feel that you like Ubuntu best and decide that you want to remove Xubuntu or Kubuntu to save hard drive space after removal, I found the following to be extremely handy:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

There are versions for fully removing these desktop environments for Dapper, Edgy, Feisty, and Gutsy.  It really helped me out when I installed Gutsy onto my PC from a magazine disk that installed all three environments at once.  All I wanted was Ubuntu. :)

Not tested on a Mac.

Could come in real handy for those with limited hard drive space.

---

