---
title: "booting problem"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by sujinge9 on 2008-02-03
I was having issues with the archive manager today (it wouldn't open any files), so I decided to reboot the computer. But when I did, it didn't give me the usual log in screen. Instead it was all black and and it said
Starting up....
Loading please wait...
kinit: name_to_dev_t (/dev.disk.by-uuid/ *a huge trail of numbers and letter*)
kinit:trying to resume from /dev.disk.by-uuid/ *a huge trail of numbers and letter*
kinit:no resume image doing normal boot
Ubuntu 7.1 name-desktop tty1

then it prompted me to log in dos style. 

Can someone help me get it back to normal? Thanks.

---

### Post by burnetbj on 2008-02-03
I had that same screen a few days ago and someone was kind enough to help me ....
Some how Ubuntu just changed my screen resolution to an out of range setup so ....after rerunning X it can back up as gui..

Think it was this 

 sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by sujinge9 on 2008-02-04
Hey, thanks for your help, but the code did not work. Is it possible for you to recheck it and make sure it is correct?
Thanks.

---

### Post by oedha on 2008-02-04
what if sudo-reconfigure xserver-xorg

---

### Post by sujinge9 on 2008-02-06
Evidently, sudo-reconfigure isn't a valid command.... Please help. If I can't get this fixed, I'm going to have to reinstall linux... I don't know if this will help, but I was trying to install GTK2+ and compiz before this issue. Thanks.

---

### Post by sujinge9 on 2008-02-07
*bump

Someone? Anyone? please help!

---

### Post by The Hunt For Ida Wave on 2008-02-16
I'm having this problem too. It usually happens when I click 'show desktop' (though not always). I'm prompted to log in again dos style, but before I can complete this, I'm redirected and prompted to log in via the GUI screen.

"kinit:no resume image doing normal boot" is also the typical error message I receive.

I should add that I have just re-installed Ubuntu 7.10, and had no similar problems to this on my previous install.

Any suggestions appreciated.

---

### Post by s1r_william on 2008-04-16
i used this:
```
sudo dpkg-reconfigure -phigh usplash
```

---

