---
title: "have to 'sudo modprobe ndiswrapper' after every reboot"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Djbb on 2008-01-26
I recently installed a NetGear 311g wireless card and I got it up and running. The only problem is, whenever I reboot the computer, I have to type "sudo modprobe ndiswrapper" into the terminal for it to turn the internet back on. Is there a way to keep it permanently up?

---

### Post by doorknob60 on 2008-01-26
```
sudo ndiswrapper -m
```

---

### Post by cmnorton on 2008-01-26
I believe you have to do more with ndiswrapper, as the reply that mine followed indicates.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Djbb on 2008-01-26
> **doorknob60 said:**
> ```
sudo ndiswrapper -m
```

tony@tony-desktop:~$ sudo ndiswrapper -m
[sudo] password for tony:
module configuration already contains alias directive

tony@tony-desktop:~$ 


Still the same problem after reboot

---

### Post by kevdog on 2008-01-26
Do this:

echo ndiswrapper | sudo tee -a /etc/modules

Reboot and it should work.

---

### Post by 4i4a on 2008-06-18
Thanks guys,

echo ndiswrapper | sudo tee -a /etc/modules

works for Ubuntu 8.04

BTW what does it mean?:
tee -a

---

