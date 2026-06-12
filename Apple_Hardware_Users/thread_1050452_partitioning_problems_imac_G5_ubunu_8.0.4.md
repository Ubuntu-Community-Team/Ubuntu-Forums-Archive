---
title: "partitioning problems imac G5 ubunu 8.0.4"
date: 2009-01-25
forum: Apple Hardware Users
---

### Post by Lexwebb on 2009-01-25
i am having trouble partitioning my HD to put ubuntu onto it, i run the live cd, go threw the installer, use the default partition settings and it says at the end when i click install: unable to partition because G5 is still mounted. What to do??

can anyone help, give me custom partition settings or whatever, i just want to create a 10gb partition and put Ubuntu on it.

Im on iMac G5 ppc.

---

### Post by tiresia on 2009-01-25
Do you have MacOSX already installed on your HD?

---

### Post by Lexwebb on 2009-01-25
yes i do

---

### Post by tiresia on 2009-01-25
The FileSystem for OSX is HFS+
Before installing Linux on a partition you need to create some free space for it. This free space will be formatted as ext3 (the Linux File System). In addition to the Linux Partition a second Partition will be created (Apple Bootstrap) and a SWAP Partition.

Therefore I suggest you to give to Ubuntu at least 15GB. Anyway, to install Linux, follow this
1. Do not mount your HD (do not select the HD in Places, because the Live-CD will mount the HD)
2. Go to System > Administration > Partition Editor (GParted)
3. Resize your partition, leaving 10-15 GB free
4. Close the Partition Editor and click on Install
5. Choose the Option to install on the free space
Done

---

### Post by Lexwebb on 2009-01-25
ty, ill restart and try this, i will post again if it works :)

---

### Post by Dareajoe on 2009-01-26
I've noticed that my iMac G5 is working louder than when I first bought it - I guess the fan is working harder these days. I would love for it to be very quiet and am looking for a solutiong. Anyone?

---

### Post by Lexwebb on 2009-01-26
hey, i have got the same ting, that fan is going mad on ubuntu, is there a way to  turn the rpm down, its doesnt need to run that fast as there is minimal heat coming out the back

---

### Post by thomasthetug on 2009-01-26
> **Dareajoe said:**
> I've noticed that my iMac G5 is working louder than when I first bought it - I guess the fan is working harder these days. I would love for it to be very quiet and am looking for a solutiong. Anyone?

Although this doesn't have to do with ubuntu, but i have the same problem, you can either completely clean out the fans, and if its still loud then it could be the lower fan, and the bearing could have worn out and makes it loud mines like that too, its annoying i know.

---

