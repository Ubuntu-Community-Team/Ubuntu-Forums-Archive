---
title: "boot into os"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by havic632 on 2006-09-05
on my computer I had windows vista beta 2 installed then I put open suse linux on it the dual boot way. now I just installed ubuntu on it and now in ubuntu's boot screen it shows me ubuntu and open suse. how can I get it to show me windows and boot into it? is there a work around this or can you only do 2 os's on a machine?

---

### Post by seshomaru samma on 2006-09-05
you can triple boot no problem
In the terminal put


```
sudo gedit /boot/grub/menu.lst
```


then add these 3 lines at the bottom of the document


```
title vista rootnoverify (hd0,2) chainloader +1
```

and save

you might need to adjut the (hd0,2) part of the second line according to where Vista is on your harddisk
If you dont know , i think running fdisk would help


```
sudo fdisk -l
```


hope this helps

---

