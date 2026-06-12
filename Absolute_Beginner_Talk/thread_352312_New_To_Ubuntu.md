---
title: "New To Ubuntu"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by indianakid on 2007-02-03
Hello my name is paul and im super new to ubuntu im liking it so far...so let me get to my question



i have a small hard drive with both xp and ubuntu on it - dual booting

and i have a larger hard drive as a slave in ubuntu can you store files and programs and such on this slave drive like you and in windows.. if so please explain the process thank you...

---

### Post by Malta paul on 2007-02-03
Hi Welcome, yes you can use your second drive as you wish. Have a look at these very good references:   [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

If you still have problems their are lots of experts in this community to help you.
Have fun :)

---

### Post by hmLyons on 2007-02-03
Are you asking if you can access your second hard drive from Ubuntu to store files on and such? You should be able to. 

Is this a new hard disk or do you have files on it that you were using with XP? If you were using this disk previously with XP and it is formatted as NTFS you will be able to read it but I'm not sure about writing to it from Ubuntu. If you were using it with XP and it's formatted as FAT then you should be able to read and write to it from Ubuntu and XP. I've never tried this myself so I'm not exactly sure, but that is how I understand it.

If you click **Places > Computer** does the disk show up?

---

### Post by glabouni on 2007-02-03
put aside the slave fact. that doesn't matter. 
what matters is partition and filesystem.

I assume you want to use your larger drive as storage and would like to access it both from ubuntu and windows.

first you need to know how many partitions there is on that larger disk (I suppose there's only one) and what filesystem they're using.

typical ubuntu install filesystem is EXT3 
typical windows (from windows NT and higher:,2000,xp,vista)install filesystem is NTFS
typical dos and older windows install filesystem is FAT

EXT3 is not natively supported under windows, some software exists that can add read support under windows, or even read/write but writing to ext3 from windows might corrupt files or partition on some occasion.

NTFS read support is included into ubuntu, but writing to NTFS from ubuntu is considered experimental. 

FAT is natively supported (read/write) under ubuntu and windows but has some flaws as it waste some disk space, fragments over time, ....

now to get info about your current configuration, you can type in a terminal:
```
sudo fdisk -l
```

---

