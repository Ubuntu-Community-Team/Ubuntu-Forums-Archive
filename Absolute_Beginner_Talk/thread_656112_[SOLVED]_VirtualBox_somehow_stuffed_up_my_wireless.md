---
title: "[SOLVED] VirtualBox somehow stuffed up my wireless"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Xavieran on 2008-01-02
I installed virtualbox in synaptic and now my wireless network connection(that I painstakingly configured) does not work...it does not even say wireless networks in the network manager...I have a very long ethernet cable,but do not really want to use it...:)
Any ideas what caused the problem?I have no idea...

Sorry...can this be moved to the wireless and networking issues thread?
I just posted out of fright...

---

### Post by Delvien on 2008-01-02
Try the following code:

```
 sudo /etc/init.d/vboxdrv stop && sudo /etc/init.d/vboxnet stop 
```

See if that solves your problem.

---

### Post by Xavieran on 2008-01-02
Don't worry I managed to fix it...It somehow uninstalled the linux restricted modules package and hence support for my proprietary broadcom chip...I discovered this when I ran restricted drivers...thanks for your help though...

---

