---
title: "Mounting a iso help!"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by synt4xerr0r on 2006-12-16
I am trying to mount a iso onto a "virtual drive" how would i do this is there a program in ubuntu to do this?

---

### Post by taurus on 2006-12-16
Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop **filename**.iso /mnt/iso
```

---

### Post by bodhi.zazen on 2006-12-16
> **synt4xerr0r said:**
> I am trying to mount a iso onto a "virtual drive" how would i do this is there a program in ubuntu to do this?

No special program is needed:
```
sudo mkdir /media/ISO
sudo mount -o loop -t iso9660 filename.iso /media/ISO
```

Hi taurus :)

---

### Post by Bachstelze on 2006-12-16
```
sudo mount -o loop /path/to/file.iso /cdrom
```

---

### Post by taurus on 2006-12-16
> **bodhi.zazen said:**
> No special program is needed:
```
sudo mkdir /media/ISO
sudo mount -o loop -t iso9660 filename.iso /media/ISO
```

Hi Tarus :)
See, this time I typed out the whole thing!!!  ;)

---

### Post by synt4xerr0r on 2006-12-16
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop **filename**.iso /mnt/iso
```

Ok ive done this now should the cd/dvd not be able to be accessed now?

edit nvm thx bodhi.zazen

---

### Post by bodhi.zazen on 2006-12-16
> **taurus said:**
> See, this time I typed out the whole thing!!!  ;)

And fast I might add ;)

---

### Post by taurus on 2006-12-16
> **synt4xerr0r said:**
> Ok ive done this now should the cd/dvd not be able to be accessed now?

Not sure exactly what you mean here but if you want to see the contend of the ISO, run

```
ls -la /mnt/iso
```

---

### Post by synt4xerr0r on 2006-12-16
Now when i try to unmount it says im not root?!!>!>!>!>! ](*,)

---

### Post by taurus on 2006-12-16
```
sudo umount /mnt/iso
```

---

### Post by bodhi.zazen on 2006-12-16
LO: :lol: ```
sudo umount ...
```

---

### Post by synt4xerr0r on 2006-12-16
> **taurus said:**
> ```
sudo umount /mnt/iso
```

umount: /mnt/iso: not mounted

---

### Post by taurus on 2006-12-16
Where did you mount the ISO file then?  I had it on /mnt/iso while _bodhi.zazen_ had it on /media/ISO...

```
df -h
```

---

