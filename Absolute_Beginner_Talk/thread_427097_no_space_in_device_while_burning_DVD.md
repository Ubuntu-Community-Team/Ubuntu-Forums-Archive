---
title: "no space in device while burning DVD"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by lls_draco on 2007-04-29
Hi People,

I'm trying to burn a dvd using Nautilus, but unfortunately I the root directory ( / ) I have only 3.4 Gb left. I assume that in the burning process Nautilus uses the /tmp/ directory to store temporally the file you want to burn.

   My question is: Is there any way to set Nautilus in order to use another partition, lets say a external disk, to use as a temporally place?

Thanks in advance,

Cheers,

lls_draco.

---

### Post by MyR on 2007-04-29
> **lls_draco said:**
> Is there any way to set Nautilus in order to use another partition, lets say a external disk, to use as a temporally place?
sure!
```
gconf-editor
```
expand apps then click nautilus-cd-burner
edit the temp_iso_dir

peace

---

### Post by MyR on 2007-04-29
also, remember that fat32 partitions can only store files up to 4gb. i made this mistake :[
and you will probably have to restart nautilus for the change to take effect
```
nautilus -q
```

---

### Post by lls_draco on 2007-04-29
> also, remember that fat32 partitions can only store files up to 4gb. i made this mistake :[

Thank you ! :) You guys are very quick in answering !! 

I'll keep that, about the fize of the files in fat32, in mind.


Once MyR, thanks.

---

