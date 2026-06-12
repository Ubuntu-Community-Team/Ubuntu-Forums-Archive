---
title: "Swap Partition not being detected"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by omkarwagh on 2007-05-28
hey im a noob on linux so please help me out here.
i just installed java plugins using the command
sudo aptitude install sun-java6-plugin(or something of that sort)
after installing this successfully i am now able to use the java plugin but now however my swap partition has simply stopped being used. there is a whole 350 MB partition but when i open up system monitor it says 0bytes of 0bytes swap being used. 
since my RAM is very low, i depend on virtual memory very heavily both in ubuntu and in windows.

another observation:- for some arbitrary reason the numbering of the hard drives had changed i.e. grub was also reading the swap partition as the root directory. i fixed it using the live CD and changing the menu.lst file but now i dont know what has happened to the swap.

im not sure if it is due to the installation of java but im just giving as much info as i can give.
thanks in advance.
omkar

---

### Post by Lucifiel on 2007-05-28
What version of Ubuntu are you using?

---

### Post by omkarwagh on 2007-05-28
im using 6.06 LTS Dapper Drake.
ive been using it for nearly 4 months now.

---

### Post by taurus on 2007-05-28
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
free
```

---

### Post by pveith on 2007-05-28
please enter the following command in a terminal and post the resulting messages here.

```
sudo swapon -a -v
```

this should give us some lead to help you.

---

### Post by omkarwagh on 2007-05-28
TO TAURUS:-
sudo fdisk -l gives this
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        4863    28820610    f  W95 Ext'd (LBA)
/dev/hda5            1276        1276        8001    7  HPFS/NTFS
/dev/hda6            1277        4816    28435018+  83  Linux
/dev/hda7            4817        4863      377496   82  Linux swap / Solaris

my fstab is :-
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
#/dev/hda6       /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0     1
#/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0     1
/dev/hda7       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

free gives :-
             total       used       free     shared    buffers     cached
Mem:        247232     241968       5264          0       5060     113832
-/+ buffers/cache:     123076     124156
Swap:            0          0          0


TO PVEITH:-
your command gives me:-
swapon on /dev/hda7
swapon: /dev/hda7: Invalid argument

---

### Post by pveith on 2007-05-28
okay, that is strange. My suspect would be a wrong Filesystem on /dev/hda7. This is a guess, so it might be good to wait for Taurus opinion. To create a new filesystem on hda7 use:

```
sudo mkswap -c /dev/hda7 
```

And post the output. if no errors do a

```
sudo swapon -a
```

again.

---

### Post by taurus on 2007-05-28
```
sudo mkswap /dev/hda7
sudo swapon /dev/hda7
free
```

---

### Post by omkarwagh on 2007-05-28
AWESOME.
thanks a lot guys. ive been pretty frustrated all day today. cant seem to get my work done at all.

any idea as to why this may have happened? i mean both my grub menu.lst and the swap partition seem to have been corrupted. 

thanks a lot.

---

### Post by pveith on 2007-05-28
That a swap-fs gets corrupted is a rather irregular error (never had that one before) for me. I am a little paranoid when it comes to filesystem/harddisks and errors and therefore use the smartmontools to monitor harddisk erros. This gives me a hint, when to exchange the disk before it kisses the carpet.

But these tools do require some reading to understand the data given...

Here the link [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/) .

(Not to alert you to much: This is just really my first check to get to the error somehow. Working with servers, which ran for years (3+) on the same harddisk, gets admin very paranoid. And with this tool you will get a good overview of the status of your harddisk.)

---

### Post by omkarwagh on 2007-05-28
hmmm seems like a link i could use. thanks.

anyways all my systems seem to be working perfectly now. thanks guys.gotta catch up on missed time.

---

