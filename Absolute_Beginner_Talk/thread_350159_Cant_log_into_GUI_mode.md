---
title: "Cant log into GUI mode"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Which_one's_Pink on 2007-01-31
Hi,

I have Ubuntu dapper coexisting with windows xp on my laptop. Been using Ubuntu on and off without any problems. But today when I tried to log in it just didnt go to the usual GUI mode,instead it went straight to the text console. I do not know how on earth did this happen all of a sudden. The only thing i remember changing was the menu list for the boot up menu where i disabled the previous editions of Ubuntu on the boot up menu, but that was over a month ago and I could log in to the GUI mode then after changes had been made. Now suddenly this occurs, can anyone please find a solution 

thanks,
which ones pink

---

### Post by taurus on 2007-01-31
Log into a console and see what happens when you run this command at a prompt?

```
startx
```

---

### Post by Which_one's_Pink on 2007-01-31
Thanks a lot, it worked :D . But why doesnt it directly go on to the gui mode ?

---

### Post by taurus on 2007-01-31
Try this

```
sudo /etc/init.d/gdm start
```
Reboot and see if it boots you into GUI login screen.

---

### Post by Which_one's_Pink on 2007-02-01
I did what you told me and it still went to the console. this time though startx gives me a black screen , though i can hear the sound of logging in.:confused:.

Edit: I did " sudo /etc/init.d/gdm stop" and rebooted. This time  i could go into the gui from console without problem, but the basic problem is still present. I cannot log into GUI directly

---

### Post by suhaib on 2007-02-06
And I to have this problem, I was told to try, update-rc.d... but it didn't work.

---

