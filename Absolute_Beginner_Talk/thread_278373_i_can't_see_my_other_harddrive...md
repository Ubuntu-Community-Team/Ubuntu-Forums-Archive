---
title: "i can't see my other harddrive.."
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by akiwanker on 2006-10-16
ok i just installed ubuntu 6.06 LTS. i never tried linux before and i suck at computers anyway. but still i got everything else to work. music, videos etc. BUT my second hd cant be used.. it shows in disks etc but i cant partition it  or access it. 

Ps. sorry about my english and explanation. i'm finnish.:-D

---

### Post by Kateikyoushi on 2006-10-16
Lets begin with listing your current partitions.

```
sudo fdisk -l
```

---

### Post by akiwanker on 2006-10-16
Levy /dev/hda: 20.0 Gt, 20020396032 tavua
255 päätä, 63 sektoria/ura, 2434 sylinteriä
Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit

    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Laajennettu
/dev/hda5            2331        2434      835348+  82  Linux / Solaris heittova ihtotiedosto

Levy /dev/hdb: 203.9 Gt, 203928109056 tavua
255 päätä, 63 sektoria/ura, 24792 sylinteriä
Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit

    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä


sorry it's in finnish.. nut i suppose that it's the hdb that's ****** up.. it was working earlier on my winxp machine but then i tried suse on it and it didn't install and i changed that hd on this now..](*,)

---

### Post by IRISHPETE on 2006-10-16
Are U Blind How The **** Cant You See Your Hard Drive You Cock Nose Mother Fucker

Go Suck Ur Brothers Scotum U Ginger Fuckarse 8) 

I Done Your Mother Last Night :D

---

### Post by Bartender on 2006-10-16
Hey, IRISH, how did you get past the Ubuntu Forums moron filter?

---

### Post by Kateikyoushi on 2006-10-16
akiwanker, I can't understand exactly the output in finnish but I think the drive is not partitioned.
Install gparted which a nice graphical partitioning tool and use it to create the partition(s).

This should install it for you.
```
sudo aptitude install gparted
```

If you do not know how to, just ask.

---

### Post by akiwanker on 2006-10-16
Thank you!!!:KS  it was partioning what was not working.. i used that gparted and now i have it perfectly eorking..:-D  thanks again for quick helping..

---

