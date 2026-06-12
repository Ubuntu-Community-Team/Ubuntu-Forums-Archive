---
title: "Getting permissions outside of ubuntu"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by unrealmstr on 2006-11-13
You see, i configured my wireless network wrong so now it hangs when its trying to load the network interface on boot, so now i need to edit the interfaces file in /etc/networks/ and i cant get the correct permissions in the live ubuntu cd... is there some way around this?

---

### Post by taurus on 2006-11-13
You can do it from a terminal with the sudo command.  If you want to edit /etc/networks/interfaces, then open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/networks/interfaces
```

---

### Post by unrealmstr on 2006-11-13
ok, so how do i mount the drive so i can get in there? if i mount it as /root in the live cd, whats the directory of the file?

---

### Post by taurus on 2006-11-13
You have to mount the partition where / is resided.  Assuming you mount /dev/hda1 which is where / is on /mnt/ubuntu, then you would type

```
gksudo gedit /mnt/ubuntu/etc/networks/interfaces
```

---

### Post by unrealmstr on 2006-11-13
ohh i get it now, im starting to get the hang of ubuntu finally :p

---

### Post by taurus on 2006-11-13
It will take time but soon, you will know what to do in a terminal...

---

### Post by unrealmstr on 2006-11-13
yea i still like to lean towards a gui the terminal still intimidates me :p

---

