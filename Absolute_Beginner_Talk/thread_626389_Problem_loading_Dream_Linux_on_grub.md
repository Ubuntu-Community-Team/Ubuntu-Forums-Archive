---
title: "Problem loading Dream Linux on grub"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-29
I am currently trying to dual boot Ubuntu and Dream linux.  Everything goes well until after installation when I'm going through grub it goes strait to ubuntu without even acknowledging dream linux.  When i restart and press esc, it says dream linux but when I click it it gives me the error "disk does not exist" or something like that.  When looking at the partition in ubuntu, Everything is on that partition, but GRUB still won't boot to it

---

### Post by Dapman01 on 2007-11-29
bump

---

### Post by meierfra on 2007-11-29
Open a terminal (Applications ->Accessories->Terminal) and post the  output of

```
sudo fdisk  -l
```

and 

```
cat /boot/grub/menu.lst
```
(both "l" are lowercase L)

---

