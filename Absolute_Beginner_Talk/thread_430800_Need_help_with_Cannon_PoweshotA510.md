---
title: "Need help with Cannon PoweshotA510"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by totalnub on 2007-05-02
Well, I do know a fair amount about linux and ubuntu, (been using for about 3months now), but this one is really stumping me. My brother had a crap computer with Win98 on it. I told him i could install Xubuntu (since the system has only 128MB ram). Everything went rather smoothly. I installed Xubuntu 6.10 and when he wanted to import his pictures from his digital camera, nothing happened. No auto-mount and nothing even in fdisk -l. If anyone has any ideas, other than to get a card reader, please help me out.

---

### Post by phidia on 2007-05-02
After the camera has been plugged in you should open a terminal and type dmesg <enter>
usually there will be some output showing how the system "sees" the camera.
You will probably need to create a mount point for it after that-using the info obtained from dmesg.

---

### Post by totalnub on 2007-05-02
ok, now if i do get a result from that, should i just create a mountpoint via mkdir /media/whatever and then sudo mount whatever is the output from dmesg?

---

### Post by lamalex on 2007-05-02
pretty much! if you cant figure it out try posting your output of dmesg

---

### Post by totalnub on 2007-05-02
thanks guys. I am currently not at the computer, but i will give it a try when i am.

---

### Post by totalnub on 2007-05-08
when i plug it in, i get ```
new full speed USB device using uhci_hcd address 6
```
when it's unplugged, ```
USB disconnect, address 6
```
can someone point me in the right direction? thanks

---

### Post by totalnub on 2007-05-08
anyone? please, my bro is countin on me.

---

