---
title: "Partition format using terminal"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by RajivNair on 2007-07-27
hello everyone ,

     can anyone tell me as to what is the command to format a partition to FAT32 file format using only the terminal in Ubuntu.

thnx in advance,
rajiv nair.

---

### Post by whizbaby on 2007-07-27
mke2fs -t vfat /dev/whatever_partition_u_have

lets say 2nd part on first ide hd

mke2fs -t vfat /dev/hda2

---

### Post by Bachstelze on 2007-07-27
Wrong. mke2fs is to make an ext2/3 filesystem.

```
sudo mkfs.msdos /dev/whatever
```

---

### Post by whizbaby on 2007-07-27
OMG sorry what was I thinking (looks like I put a part of 'mount' in it) koffees a killer...

of course mke2fs is wrong and you should use mkfs.msdos or mkfs.vfat

shame on me :oops:

*slaps himself silly*

---

### Post by mcduck on 2007-07-28
mkfs is front-end for all file system builders. Use that one and you don't have to remember names of all the different builders. You can run 'sudo mkfs -t vfat /dev/sdaX' and mkfs will call the actual program needed to create the file system you asked it to do (in this case, mkfs.msdos).

---

### Post by whizbaby on 2007-07-28
Ah k thx now I know how I could do this error...

---

### Post by RajivNair on 2007-07-30
hey y'all ,

    thnx a lot for ur help , well i dint wait to find out the command ... apparently the version of gparted on ubuntu 7.04 live cd is a bit messed up .. n would automatically mount the partition before its formatting would complete ... nywyz did it using an older version of ubuntu live cd ... once again thnx a lot for y'all help ...

regards ,
rajiv nair

---

### Post by gohanssjn on 2008-02-25
sorry, wrong one...

---

