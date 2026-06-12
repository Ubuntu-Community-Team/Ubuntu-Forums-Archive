---
title: "/etc/fstab"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-08
Can someone please post their /etc/fstab file here.

Mine is all weird from feisty. I will edit your to replace mine. I can't even mount windows or install lilo because it is wrong.

---

### Post by ajmorris on 2007-01-08
also for some reason i have no hda block devices in /dev so i can't mount my windows partition when i get rid of the UUID code in my fstab file. What's with that? can i manually add the hda block devices?

---

### Post by moshuptrail on 2007-01-08
Here's a real simple one with no Windows partition.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by ajmorris on 2007-01-08
thanks

---

### Post by ajmorris on 2007-01-08
i reconfigured my fstab to mimic yours but with my config:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               reiserfs notail         0       1
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46        0       1
/dev/hda1	/media/hda1	ntfs defaults,nls=utf8,umask=007,gid=46 0	1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

now my only dilema is the fact that i have not hda block devices /dev.

That is why my old one looked like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#proc            /proc           proc    defaults        0       0
# /dev/hda6
#UUID=1cfc1c89-3f75-4887-a473-c75a6b8da416 /               reiserfs notail          0       1
# /dev/hda1 
#UUID=42E48EAFE48EA52F  /media/hda1           ntfs    defaults,nls=utf8,umask=007,gid=46 0       1 
# /dev/hda3
#UUID=8000-9CF6  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
#UUID=8cbbab28-d426-44e9-af29-953fa53272f8 none            swap    sw              0       0
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


except i had problems with the UUID entries.](*,) ](*,) ](*,) ](*,)

---

### Post by taurus on 2007-01-08
As I stated in your other thread, each time you format a partition, your UUID would change so you need to find out the new one or just use the old fashion way to include it in your /etc/fstab, /dev/hda1...

What happens when you run this command from a terminal?

```
ls -la /dev
```

---

### Post by ajmorris on 2007-01-08
crw-rw-rw-  1 root tty       2,  73 2007-01-10 00:21 ptyt9
crw-rw-rw-  1 root tty       2,  74 2007-01-10 00:21 ptyta
crw-rw-rw-  1 root tty       2,  75 2007-01-10 00:21 ptytb
crw-rw-rw-  1 root tty       2,  76 2007-01-10 00:21 ptytc
crw-rw-rw-  1 root tty       2,  77 2007-01-10 00:21 ptytd
crw-rw-rw-  1 root tty       2,  78 2007-01-10 00:21 ptyte
crw-rw-rw-  1 root tty       2,  79 2007-01-10 00:21 ptytf
crw-rw-rw-  1 root tty       2,  80 2007-01-10 00:21 ptyu0
crw-rw-rw-  1 root tty       2,  81 2007-01-10 00:21 ptyu1
crw-rw-rw-  1 root tty       2,  82 2007-01-10 00:21 ptyu2
crw-rw-rw-  1 root tty       2,  83 2007-01-10 00:21 ptyu3
crw-rw-rw-  1 root tty       2,  84 2007-01-10 00:21 ptyu4
crw-rw-rw-  1 root tty       2,  85 2007-01-10 00:21 ptyu5
crw-rw-rw-  1 root tty       2,  86 2007-01-10 00:21 ptyu6
crw-rw-rw-  1 root tty       2,  87 2007-01-10 00:21 ptyu7
crw-rw-rw-  1 root tty       2,  88 2007-01-10 00:21 ptyu8
crw-rw-rw-  1 root tty       2,  89 2007-01-10 00:21 ptyu9
crw-rw-rw-  1 root tty       2,  90 2007-01-10 00:21 ptyua
crw-rw-rw-  1 root tty       2,  91 2007-01-10 00:21 ptyub
crw-rw-rw-  1 root tty       2,  92 2007-01-10 00:21 ptyuc
crw-rw-rw-  1 root tty       2,  93 2007-01-10 00:21 ptyud
crw-rw-rw-  1 root tty       2,  94 2007-01-10 00:21 ptyue
crw-rw-rw-  1 root tty       2,  95 2007-01-10 00:21 ptyuf
crw-rw-rw-  1 root tty       2,  96 2007-01-10 00:21 ptyv0
crw-rw-rw-  1 root tty       2,  97 2007-01-10 00:21 ptyv1
crw-rw-rw-  1 root tty       2,  98 2007-01-10 00:21 ptyv2
crw-rw-rw-  1 root tty       2,  99 2007-01-10 00:21 ptyv3
crw-rw-rw-  1 root tty       2, 100 2007-01-10 00:21 ptyv4
crw-rw-rw-  1 root tty       2, 101 2007-01-10 00:21 ptyv5
crw-rw-rw-  1 root tty       2, 102 2007-01-10 00:21 ptyv6
crw-rw-rw-  1 root tty       2, 103 2007-01-10 00:21 ptyv7
crw-rw-rw-  1 root tty       2, 104 2007-01-10 00:21 ptyv8
crw-rw-rw-  1 root tty       2, 105 2007-01-10 00:21 ptyv9
crw-rw-rw-  1 root tty       2, 106 2007-01-10 00:21 ptyva
crw-rw-rw-  1 root tty       2, 107 2007-01-10 00:21 ptyvb
crw-rw-rw-  1 root tty       2, 108 2007-01-10 00:21 ptyvc
crw-rw-rw-  1 root tty       2, 109 2007-01-10 00:21 ptyvd
crw-rw-rw-  1 root tty       2, 110 2007-01-10 00:21 ptyve
crw-rw-rw-  1 root tty       2, 111 2007-01-10 00:21 ptyvf
crw-rw-rw-  1 root tty       2, 112 2007-01-10 00:21 ptyw0
crw-rw-rw-  1 root tty       2, 113 2007-01-10 00:21 ptyw1
crw-rw-rw-  1 root tty       2, 114 2007-01-10 00:21 ptyw2
crw-rw-rw-  1 root tty       2, 115 2007-01-10 00:21 ptyw3
crw-rw-rw-  1 root tty       2, 116 2007-01-10 00:21 ptyw4
crw-rw-rw-  1 root tty       2, 117 2007-01-10 00:21 ptyw5
crw-rw-rw-  1 root tty       2, 118 2007-01-10 00:21 ptyw6
crw-rw-rw-  1 root tty       2, 119 2007-01-10 00:21 ptyw7
crw-rw-rw-  1 root tty       2, 120 2007-01-10 00:21 ptyw8
crw-rw-rw-  1 root tty       2, 121 2007-01-10 00:21 ptyw9
crw-rw-rw-  1 root tty       2, 122 2007-01-10 00:21 ptywa
crw-rw-rw-  1 root tty       2, 123 2007-01-10 00:21 ptywb
crw-rw-rw-  1 root tty       2, 124 2007-01-10 00:21 ptywc
crw-rw-rw-  1 root tty       2, 125 2007-01-10 00:21 ptywd
crw-rw-rw-  1 root tty       2, 126 2007-01-10 00:21 ptywe
crw-rw-rw-  1 root tty       2, 127 2007-01-10 00:21 ptywf
crw-rw-rw-  1 root tty       2, 128 2007-01-10 00:21 ptyx0
crw-rw-rw-  1 root tty       2, 129 2007-01-10 00:21 ptyx1
crw-rw-rw-  1 root tty       2, 130 2007-01-10 00:21 ptyx2
crw-rw-rw-  1 root tty       2, 131 2007-01-10 00:21 ptyx3
crw-rw-rw-  1 root tty       2, 132 2007-01-10 00:21 ptyx4
crw-rw-rw-  1 root tty       2, 133 2007-01-10 00:21 ptyx5
crw-rw-rw-  1 root tty       2, 134 2007-01-10 00:21 ptyx6
crw-rw-rw-  1 root tty       2, 135 2007-01-10 00:21 ptyx7
crw-rw-rw-  1 root tty       2, 136 2007-01-10 00:21 ptyx8
crw-rw-rw-  1 root tty       2, 137 2007-01-10 00:21 ptyx9
crw-rw-rw-  1 root tty       2, 138 2007-01-10 00:21 ptyxa
crw-rw-rw-  1 root tty       2, 139 2007-01-10 00:21 ptyxb
crw-rw-rw-  1 root tty       2, 140 2007-01-10 00:21 ptyxc
crw-rw-rw-  1 root tty       2, 141 2007-01-10 00:21 ptyxd
crw-rw-rw-  1 root tty       2, 142 2007-01-10 00:21 ptyxe
crw-rw-rw-  1 root tty       2, 143 2007-01-10 00:21 ptyxf
crw-rw-rw-  1 root tty       2, 144 2007-01-10 00:21 ptyy0
crw-rw-rw-  1 root tty       2, 145 2007-01-10 00:21 ptyy1
crw-rw-rw-  1 root tty       2, 146 2007-01-10 00:21 ptyy2
crw-rw-rw-  1 root tty       2, 147 2007-01-10 00:21 ptyy3
crw-rw-rw-  1 root tty       2, 148 2007-01-10 00:21 ptyy4
crw-rw-rw-  1 root tty       2, 149 2007-01-10 00:21 ptyy5
crw-rw-rw-  1 root tty       2, 150 2007-01-10 00:21 ptyy6
crw-rw-rw-  1 root tty       2, 151 2007-01-10 00:21 ptyy7
crw-rw-rw-  1 root tty       2, 152 2007-01-10 00:21 ptyy8
crw-rw-rw-  1 root tty       2, 153 2007-01-10 00:21 ptyy9
crw-rw-rw-  1 root tty       2, 154 2007-01-10 00:21 ptyya
crw-rw-rw-  1 root tty       2, 155 2007-01-10 00:21 ptyyb
crw-rw-rw-  1 root tty       2, 156 2007-01-10 00:21 ptyyc
crw-rw-rw-  1 root tty       2, 157 2007-01-10 00:21 ptyyd
crw-rw-rw-  1 root tty       2, 158 2007-01-10 00:21 ptyye
crw-rw-rw-  1 root tty       2, 159 2007-01-10 00:21 ptyyf
crw-rw-rw-  1 root tty       2, 160 2007-01-10 00:21 ptyz0
crw-rw-rw-  1 root tty       2, 161 2007-01-10 00:21 ptyz1
crw-rw-rw-  1 root tty       2, 162 2007-01-10 00:21 ptyz2
crw-rw-rw-  1 root tty       2, 163 2007-01-10 00:21 ptyz3
crw-rw-rw-  1 root tty       2, 164 2007-01-10 00:21 ptyz4
crw-rw-rw-  1 root tty       2, 165 2007-01-10 00:21 ptyz5
crw-rw-rw-  1 root tty       2, 166 2007-01-10 00:21 ptyz6
crw-rw-rw-  1 root tty       2, 167 2007-01-10 00:21 ptyz7
crw-rw-rw-  1 root tty       2, 168 2007-01-10 00:21 ptyz8
crw-rw-rw-  1 root tty       2, 169 2007-01-10 00:21 ptyz9
crw-rw-rw-  1 root tty       2, 170 2007-01-10 00:21 ptyza
crw-rw-rw-  1 root tty       2, 171 2007-01-10 00:21 ptyzb
crw-rw-rw-  1 root tty       2, 172 2007-01-10 00:21 ptyzc
crw-rw-rw-  1 root tty       2, 173 2007-01-10 00:21 ptyzd
crw-rw-rw-  1 root tty       2, 174 2007-01-10 00:21 ptyze
crw-rw-rw-  1 root tty       2, 175 2007-01-10 00:21 ptyzf
brw-rw----  1 root disk      1,   0 2007-01-10 00:21 ram0
brw-rw----  1 root disk      1,   1 2007-01-10 00:21 ram1
brw-rw----  1 root disk      1,  10 2007-01-10 00:21 ram10
brw-rw----  1 root disk      1,  11 2007-01-10 00:21 ram11
brw-rw----  1 root disk      1,  12 2007-01-10 00:21 ram12
brw-rw----  1 root disk      1,  13 2007-01-10 00:21 ram13
brw-rw----  1 root disk      1,  14 2007-01-10 00:21 ram14
brw-rw----  1 root disk      1,  15 2007-01-10 00:21 ram15
brw-rw----  1 root disk      1,   2 2007-01-10 00:21 ram2
brw-rw----  1 root disk      1,   3 2007-01-10 00:21 ram3
brw-rw----  1 root disk      1,   4 2007-01-10 00:21 ram4
brw-rw----  1 root disk      1,   5 2007-01-10 00:21 ram5
brw-rw----  1 root disk      1,   6 2007-01-10 00:21 ram6
brw-rw----  1 root disk      1,   7 2007-01-10 00:21 ram7
brw-rw----  1 root disk      1,   8 2007-01-10 00:21 ram8
brw-rw----  1 root disk      1,   9 2007-01-10 00:21 ram9
crw-rw-rw-  1 root root      1,   8 2007-01-10 00:21 random
crw-rw----  1 root audio    10, 135 2007-01-10 00:21 rtc
brw-rw----  1 root floppy   11,   0 2007-01-10 00:21 scd0
brw-rw----  1 root disk      8,   0 2007-01-10 00:21 sda
brw-rw----  1 root root      8,   1 2007-01-10 00:21 sda1
brw-rw----  1 root root      8,   2 2007-01-10 00:21 sda2
brw-rw----  1 root root      8,   3 2007-01-10 00:21 sda3
brw-rw----  1 root root      8,   5 2007-01-10 00:21 sda5
brw-rw----  1 root root      8,   6 2007-01-10 00:21 sda6
crw-rw----  1 root audio    14,   1 2007-01-09 13:22 sequencer
crw-rw----  1 root audio    14,   8 2007-01-09 13:22 sequencer2
crw-rw----  1 root root     21,   0 2007-01-10 00:21 sg0
crw-rw----  1 root root     21,   1 2007-01-10 00:21 sg1
drwxrwxrwt  2 root root          40 2007-01-09 13:22 shm
crw-rw----  1 root root     10, 231 2007-01-10 00:21 snapshot
drwxr-xr-x  2 root root         220 2007-01-09 13:22 snd
lrwxrwxrwx  1 root root          24 2007-01-10 00:22 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx  1 root root           4 2007-01-10 00:22 sr0 -> scd0
drwxr-xr-x  3 root root          60 2007-01-10 00:21 .static
lrwxrwxrwx  1 root root          15 2007-01-10 00:22 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root root          15 2007-01-10 00:22 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root root          15 2007-01-10 00:22 stdout -> /proc/self/fd/1
crw-rw-rw-  1 root root      5,   0 2007-01-09 14:10 tty
crw-rw----  1 root root      4,   0 2007-01-10 00:21 tty0
crw-------  1 root root      4,   1 2007-01-09 13:22 tty1
crw-rw----  1 root root      4,  10 2007-01-10 00:21 tty10
crw-rw----  1 root root      4,  11 2007-01-10 00:21 tty11
crw-rw----  1 root root      4,  12 2007-01-10 00:21 tty12
crw-rw----  1 root root      4,  13 2007-01-10 00:21 tty13
crw-rw----  1 root root      4,  14 2007-01-10 00:21 tty14
crw-rw----  1 root root      4,  15 2007-01-10 00:21 tty15
crw-rw----  1 root root      4,  16 2007-01-10 00:21 tty16
crw-rw----  1 root root      4,  17 2007-01-10 00:21 tty17
crw-rw----  1 root root      4,  18 2007-01-10 00:21 tty18
crw-rw----  1 root root      4,  19 2007-01-10 00:21 tty19
crw-------  1 root root      4,   2 2007-01-09 13:22 tty2
crw-rw----  1 root root      4,  20 2007-01-10 00:21 tty20
crw-rw----  1 root root      4,  21 2007-01-10 00:21 tty21
crw-rw----  1 root root      4,  22 2007-01-10 00:21 tty22
crw-rw----  1 root root      4,  23 2007-01-10 00:21 tty23
crw-rw----  1 root root      4,  24 2007-01-10 00:21 tty24
crw-rw----  1 root root      4,  25 2007-01-10 00:21 tty25
crw-rw----  1 root root      4,  26 2007-01-10 00:21 tty26
crw-rw----  1 root root      4,  27 2007-01-10 00:21 tty27
crw-rw----  1 root root      4,  28 2007-01-10 00:21 tty28
crw-rw----  1 root root      4,  29 2007-01-10 00:21 tty29
crw-------  1 root root      4,   3 2007-01-09 13:22 tty3
crw-rw----  1 root root      4,  30 2007-01-10 00:21 tty30
crw-rw----  1 root root      4,  31 2007-01-10 00:21 tty31
crw-rw----  1 root root      4,  32 2007-01-10 00:21 tty32
crw-rw----  1 root root      4,  33 2007-01-10 00:21 tty33
crw-rw----  1 root root      4,  34 2007-01-10 00:21 tty34
crw-rw----  1 root root      4,  35 2007-01-10 00:21 tty35
crw-rw----  1 root root      4,  36 2007-01-10 00:21 tty36
crw-rw----  1 root root      4,  37 2007-01-10 00:21 tty37
crw-rw----  1 root root      4,  38 2007-01-10 00:21 tty38
crw-rw----  1 root root      4,  39 2007-01-10 00:21 tty39
crw-------  1 root root      4,   4 2007-01-09 13:22 tty4
crw-rw----  1 root root      4,  40 2007-01-10 00:21 tty40
crw-rw----  1 root root      4,  41 2007-01-10 00:21 tty41
crw-rw----  1 root root      4,  42 2007-01-10 00:21 tty42
crw-rw----  1 root root      4,  43 2007-01-10 00:21 tty43
crw-rw----  1 root root      4,  44 2007-01-10 00:21 tty44
crw-rw----  1 root root      4,  45 2007-01-10 00:21 tty45
crw-rw----  1 root root      4,  46 2007-01-10 00:21 tty46
crw-rw----  1 root root      4,  47 2007-01-10 00:21 tty47
crw-rw----  1 root root      4,  48 2007-01-10 00:21 tty48
crw-rw----  1 root root      4,  49 2007-01-10 00:21 tty49
crw-------  1 root root      4,   5 2007-01-09 13:22 tty5
crw-rw----  1 root root      4,  50 2007-01-10 00:21 tty50
crw-rw----  1 root root      4,  51 2007-01-10 00:21 tty51
crw-rw----  1 root root      4,  52 2007-01-10 00:21 tty52
crw-rw----  1 root root      4,  53 2007-01-10 00:21 tty53
crw-rw----  1 root root      4,  54 2007-01-10 00:21 tty54
crw-rw----  1 root root      4,  55 2007-01-10 00:21 tty55
crw-rw----  1 root root      4,  56 2007-01-10 00:21 tty56
crw-rw----  1 root root      4,  57 2007-01-10 00:21 tty57
crw-rw----  1 root root      4,  58 2007-01-10 00:21 tty58
crw-rw----  1 root root      4,  59 2007-01-10 00:21 tty59
crw-------  1 root root      4,   6 2007-01-09 13:22 tty6
crw-rw----  1 root root      4,  60 2007-01-10 00:21 tty60
crw-rw----  1 root root      4,  61 2007-01-10 00:21 tty61
crw-rw----  1 root root      4,  62 2007-01-10 00:21 tty62
crw-rw----  1 root root      4,  63 2007-01-10 00:21 tty63
crw-rw----  1 root root      4,   7 2007-01-10 00:21 tty7
crw-rw----  1 root root      4,   8 2007-01-09 13:22 tty8
crw-rw----  1 root root      4,   9 2007-01-10 00:21 tty9
crw-rw-rw-  1 root tty       3, 176 2007-01-10 00:21 ttya0
crw-rw-rw-  1 root tty       3, 177 2007-01-10 00:21 ttya1
crw-rw-rw-  1 root tty       3, 178 2007-01-10 00:21 ttya2
crw-rw-rw-  1 root tty       3, 179 2007-01-10 00:21 ttya3
crw-rw-rw-  1 root tty       3, 180 2007-01-10 00:21 ttya4
crw-rw-rw-  1 root tty       3, 181 2007-01-10 00:21 ttya5
crw-rw-rw-  1 root tty       3, 182 2007-01-10 00:21 ttya6
crw-rw-rw-  1 root tty       3, 183 2007-01-10 00:21 ttya7
crw-rw-rw-  1 root tty       3, 184 2007-01-10 00:21 ttya8
crw-rw-rw-  1 root tty       3, 185 2007-01-10 00:21 ttya9
crw-rw-rw-  1 root tty       3, 186 2007-01-10 00:21 ttyaa
crw-rw-rw-  1 root tty       3, 187 2007-01-10 00:21 ttyab
crw-rw-rw-  1 root tty       3, 188 2007-01-10 00:21 ttyac
crw-rw-rw-  1 root tty       3, 189 2007-01-10 00:21 ttyad
crw-rw-rw-  1 root tty       3, 190 2007-01-10 00:21 ttyae
crw-rw-rw-  1 root tty       3, 191 2007-01-10 00:21 ttyaf
crw-rw-rw-  1 root tty       3, 192 2007-01-10 00:21 ttyb0
crw-rw-rw-  1 root tty       3, 193 2007-01-10 00:21 ttyb1
crw-rw-rw-  1 root tty       3, 194 2007-01-10 00:21 ttyb2
crw-rw-rw-  1 root tty       3, 195 2007-01-10 00:21 ttyb3
crw-rw-rw-  1 root tty       3, 196 2007-01-10 00:21 ttyb4
crw-rw-rw-  1 root tty       3, 197 2007-01-10 00:21 ttyb5
crw-rw-rw-  1 root tty       3, 198 2007-01-10 00:21 ttyb6
crw-rw-rw-  1 root tty       3, 199 2007-01-10 00:21 ttyb7
crw-rw-rw-  1 root tty       3, 200 2007-01-10 00:21 ttyb8
crw-rw-rw-  1 root tty       3, 201 2007-01-10 00:21 ttyb9
crw-rw-rw-  1 root tty       3, 202 2007-01-10 00:21 ttyba
crw-rw-rw-  1 root tty       3, 203 2007-01-10 00:21 ttybb
crw-rw-rw-  1 root tty       3, 204 2007-01-10 00:21 ttybc
crw-rw-rw-  1 root tty       3, 205 2007-01-10 00:21 ttybd
crw-rw-rw-  1 root tty       3, 206 2007-01-10 00:21 ttybe
crw-rw-rw-  1 root tty       3, 207 2007-01-10 00:21 ttybf
crw-rw-rw-  1 root tty       3, 208 2007-01-10 00:21 ttyc0
crw-rw-rw-  1 root tty       3, 209 2007-01-10 00:21 ttyc1
crw-rw-rw-  1 root tty       3, 210 2007-01-10 00:21 ttyc2
crw-rw-rw-  1 root tty       3, 211 2007-01-10 00:21 ttyc3
crw-rw-rw-  1 root tty       3, 212 2007-01-10 00:21 ttyc4
crw-rw-rw-  1 root tty       3, 213 2007-01-10 00:21 ttyc5
crw-rw-rw-  1 root tty       3, 214 2007-01-10 00:21 ttyc6
crw-rw-rw-  1 root tty       3, 215 2007-01-10 00:21 ttyc7
crw-rw-rw-  1 root tty       3, 216 2007-01-10 00:21 ttyc8
crw-rw-rw-  1 root tty       3, 217 2007-01-10 00:21 ttyc9
crw-rw-rw-  1 root tty       3, 218 2007-01-10 00:21 ttyca
crw-rw-rw-  1 root tty       3, 219 2007-01-10 00:21 ttycb
crw-rw-rw-  1 root tty       3, 220 2007-01-10 00:21 ttycc
crw-rw-rw-  1 root tty       3, 221 2007-01-10 00:21 ttycd
crw-rw-rw-  1 root tty       3, 222 2007-01-10 00:21 ttyce
crw-rw-rw-  1 root tty       3, 223 2007-01-10 00:21 ttycf
crw-rw-rw-  1 root tty       3, 224 2007-01-10 00:21 ttyd0
crw-rw-rw-  1 root tty       3, 225 2007-01-10 00:21 ttyd1
crw-rw-rw-  1 root tty       3, 226 2007-01-10 00:21 ttyd2
crw-rw-rw-  1 root tty       3, 227 2007-01-10 00:21 ttyd3
crw-rw-rw-  1 root tty       3, 228 2007-01-10 00:21 ttyd4
crw-rw-rw-  1 root tty       3, 229 2007-01-10 00:21 ttyd5
crw-rw-rw-  1 root tty       3, 230 2007-01-10 00:21 ttyd6
crw-rw-rw-  1 root tty       3, 231 2007-01-10 00:21 ttyd7
crw-rw-rw-  1 root tty       3, 232 2007-01-10 00:21 ttyd8
crw-rw-rw-  1 root tty       3, 233 2007-01-10 00:21 ttyd9
crw-rw-rw-  1 root tty       3, 234 2007-01-10 00:21 ttyda
crw-rw-rw-  1 root tty       3, 235 2007-01-10 00:21 ttydb
crw-rw-rw-  1 root tty       3, 236 2007-01-10 00:21 ttydc
crw-rw-rw-  1 root tty       3, 237 2007-01-10 00:21 ttydd
crw-rw-rw-  1 root tty       3, 238 2007-01-10 00:21 ttyde
crw-rw-rw-  1 root tty       3, 239 2007-01-10 00:21 ttydf
crw-rw-rw-  1 root tty       3, 240 2007-01-10 00:21 ttye0
crw-rw-rw-  1 root tty       3, 241 2007-01-10 00:21 ttye1
crw-rw-rw-  1 root tty       3, 242 2007-01-10 00:21 ttye2
crw-rw-rw-  1 root tty       3, 243 2007-01-10 00:21 ttye3
crw-rw-rw-  1 root tty       3, 244 2007-01-10 00:21 ttye4
crw-rw-rw-  1 root tty       3, 245 2007-01-10 00:21 ttye5
crw-rw-rw-  1 root tty       3, 246 2007-01-10 00:21 ttye6
crw-rw-rw-  1 root tty       3, 247 2007-01-10 00:21 ttye7
crw-rw-rw-  1 root tty       3, 248 2007-01-10 00:21 ttye8
crw-rw-rw-  1 root tty       3, 249 2007-01-10 00:21 ttye9
crw-rw-rw-  1 root tty       3, 250 2007-01-10 00:21 ttyea
crw-rw-rw-  1 root tty       3, 251 2007-01-10 00:21 ttyeb
crw-rw-rw-  1 root tty       3, 252 2007-01-10 00:21 ttyec
crw-rw-rw-  1 root tty       3, 253 2007-01-10 00:21 ttyed
crw-rw-rw-  1 root tty       3, 254 2007-01-10 00:21 ttyee
crw-rw-rw-  1 root tty       3, 255 2007-01-10 00:21 ttyef
crw-rw-rw-  1 root tty       3,   0 2007-01-10 00:21 ttyp0
crw-rw-rw-  1 root tty       3,   1 2007-01-10 00:21 ttyp1
crw-rw-rw-  1 root tty       3,   2 2007-01-10 00:21 ttyp2
crw-rw-rw-  1 root tty       3,   3 2007-01-10 00:21 ttyp3
crw-rw-rw-  1 root tty       3,   4 2007-01-10 00:21 ttyp4
crw-rw-rw-  1 root tty       3,   5 2007-01-10 00:21 ttyp5
crw-rw-rw-  1 root tty       3,   6 2007-01-10 00:21 ttyp6
crw-rw-rw-  1 root tty       3,   7 2007-01-10 00:21 ttyp7
crw-rw-rw-  1 root tty       3,   8 2007-01-10 00:21 ttyp8
crw-rw-rw-  1 root tty       3,   9 2007-01-10 00:21 ttyp9
crw-rw-rw-  1 root tty       3,  10 2007-01-10 00:21 ttypa
crw-rw-rw-  1 root tty       3,  11 2007-01-10 00:21 ttypb
crw-rw-rw-  1 root tty       3,  12 2007-01-10 00:21 ttypc
crw-rw-rw-  1 root tty       3,  13 2007-01-10 00:21 ttypd
crw-rw-rw-  1 root tty       3,  14 2007-01-10 00:21 ttype
crw-rw-rw-  1 root tty       3,  15 2007-01-10 00:21 ttypf
crw-rw-rw-  1 root tty       3,  16 2007-01-10 00:21 ttyq0
crw-rw-rw-  1 root tty       3,  17 2007-01-10 00:21 ttyq1
crw-rw-rw-  1 root tty       3,  18 2007-01-10 00:21 ttyq2
crw-rw-rw-  1 root tty       3,  19 2007-01-10 00:21 ttyq3
crw-rw-rw-  1 root tty       3,  20 2007-01-10 00:21 ttyq4
crw-rw-rw-  1 root tty       3,  21 2007-01-10 00:21 ttyq5
crw-rw-rw-  1 root tty       3,  22 2007-01-10 00:21 ttyq6
crw-rw-rw-  1 root tty       3,  23 2007-01-10 00:21 ttyq7
crw-rw-rw-  1 root tty       3,  24 2007-01-10 00:21 ttyq8
crw-rw-rw-  1 root tty       3,  25 2007-01-10 00:21 ttyq9
crw-rw-rw-  1 root tty       3,  26 2007-01-10 00:21 ttyqa
crw-rw-rw-  1 root tty       3,  27 2007-01-10 00:21 ttyqb
crw-rw-rw-  1 root tty       3,  28 2007-01-10 00:21 ttyqc
crw-rw-rw-  1 root tty       3,  29 2007-01-10 00:21 ttyqd
crw-rw-rw-  1 root tty       3,  30 2007-01-10 00:21 ttyqe
crw-rw-rw-  1 root tty       3,  31 2007-01-10 00:21 ttyqf
crw-rw-rw-  1 root tty       3,  32 2007-01-10 00:21 ttyr0
crw-rw-rw-  1 root tty       3,  33 2007-01-10 00:21 ttyr1
crw-rw-rw-  1 root tty       3,  34 2007-01-10 00:21 ttyr2
crw-rw-rw-  1 root tty       3,  35 2007-01-10 00:21 ttyr3
crw-rw-rw-  1 root tty       3,  36 2007-01-10 00:21 ttyr4
crw-rw-rw-  1 root tty       3,  37 2007-01-10 00:21 ttyr5
crw-rw-rw-  1 root tty       3,  38 2007-01-10 00:21 ttyr6
crw-rw-rw-  1 root tty       3,  39 2007-01-10 00:21 ttyr7
crw-rw-rw-  1 root tty       3,  40 2007-01-10 00:21 ttyr8
crw-rw-rw-  1 root tty       3,  41 2007-01-10 00:21 ttyr9
crw-rw-rw-  1 root tty       3,  42 2007-01-10 00:21 ttyra
crw-rw-rw-  1 root tty       3,  43 2007-01-10 00:21 ttyrb
crw-rw-rw-  1 root tty       3,  44 2007-01-10 00:21 ttyrc
crw-rw-rw-  1 root tty       3,  45 2007-01-10 00:21 ttyrd
crw-rw-rw-  1 root tty       3,  46 2007-01-10 00:21 ttyre
crw-rw-rw-  1 root tty       3,  47 2007-01-10 00:21 ttyrf
crw-rw-rw-  1 root tty       3,  48 2007-01-10 00:21 ttys0
crw-rw----  1 root dialout   4,  64 2007-01-10 00:21 ttyS0
crw-rw-rw-  1 root tty       3,  49 2007-01-10 00:21 ttys1
crw-rw----  1 root dialout   4,  65 2007-01-10 00:21 ttyS1
crw-rw-rw-  1 root tty       3,  50 2007-01-10 00:21 ttys2
crw-rw----  1 root dialout   4,  66 2007-01-10 00:21 ttyS2
crw-rw-rw-  1 root tty       3,  51 2007-01-10 00:21 ttys3
crw-rw----  1 root dialout   4,  67 2007-01-10 00:21 ttyS3
crw-rw-rw-  1 root tty       3,  52 2007-01-10 00:21 ttys4
crw-rw-rw-  1 root tty       3,  53 2007-01-10 00:21 ttys5
crw-rw-rw-  1 root tty       3,  54 2007-01-10 00:21 ttys6
crw-rw-rw-  1 root tty       3,  55 2007-01-10 00:21 ttys7
crw-rw-rw-  1 root tty       3,  56 2007-01-10 00:21 ttys8
crw-rw-rw-  1 root tty       3,  57 2007-01-10 00:21 ttys9
crw-rw-rw-  1 root tty       3,  58 2007-01-10 00:21 ttysa
crw-rw-rw-  1 root tty       3,  59 2007-01-10 00:21 ttysb
crw-rw-rw-  1 root tty       3,  60 2007-01-10 00:21 ttysc
crw-rw-rw-  1 root tty       3,  61 2007-01-10 00:21 ttysd
crw-rw-rw-  1 root tty       3,  62 2007-01-10 00:21 ttyse
crw-rw-rw-  1 root tty       3,  63 2007-01-10 00:21 ttysf
crw-rw-rw-  1 root tty       3,  64 2007-01-10 00:21 ttyt0
crw-rw-rw-  1 root tty       3,  65 2007-01-10 00:21 ttyt1
crw-rw-rw-  1 root tty       3,  66 2007-01-10 00:21 ttyt2
crw-rw-rw-  1 root tty       3,  67 2007-01-10 00:21 ttyt3
crw-rw-rw-  1 root tty       3,  68 2007-01-10 00:21 ttyt4
crw-rw-rw-  1 root tty       3,  69 2007-01-10 00:21 ttyt5
crw-rw-rw-  1 root tty       3,  70 2007-01-10 00:21 ttyt6
crw-rw-rw-  1 root tty       3,  71 2007-01-10 00:21 ttyt7
crw-rw-rw-  1 root tty       3,  72 2007-01-10 00:21 ttyt8
crw-rw-rw-  1 root tty       3,  73 2007-01-10 00:21 ttyt9
crw-rw-rw-  1 root tty       3,  74 2007-01-10 00:21 ttyta
crw-rw-rw-  1 root tty       3,  75 2007-01-10 00:21 ttytb
crw-rw-rw-  1 root tty       3,  76 2007-01-10 00:21 ttytc
crw-rw-rw-  1 root tty       3,  77 2007-01-10 00:21 ttytd
crw-rw-rw-  1 root tty       3,  78 2007-01-10 00:21 ttyte
crw-rw-rw-  1 root tty       3,  79 2007-01-10 00:21 ttytf
crw-rw-rw-  1 root tty       3,  80 2007-01-10 00:21 ttyu0
crw-rw-rw-  1 root tty       3,  81 2007-01-10 00:21 ttyu1
crw-rw-rw-  1 root tty       3,  82 2007-01-10 00:21 ttyu2
crw-rw-rw-  1 root tty       3,  83 2007-01-10 00:21 ttyu3
crw-rw-rw-  1 root tty       3,  84 2007-01-10 00:21 ttyu4
crw-rw-rw-  1 root tty       3,  85 2007-01-10 00:21 ttyu5
crw-rw-rw-  1 root tty       3,  86 2007-01-10 00:21 ttyu6
crw-rw-rw-  1 root tty       3,  87 2007-01-10 00:21 ttyu7
crw-rw-rw-  1 root tty       3,  88 2007-01-10 00:21 ttyu8
crw-rw-rw-  1 root tty       3,  89 2007-01-10 00:21 ttyu9
crw-rw-rw-  1 root tty       3,  90 2007-01-10 00:21 ttyua
crw-rw-rw-  1 root tty       3,  91 2007-01-10 00:21 ttyub
crw-rw-rw-  1 root tty       3,  92 2007-01-10 00:21 ttyuc
crw-rw-rw-  1 root tty       3,  93 2007-01-10 00:21 ttyud
crw-rw-rw-  1 root tty       3,  94 2007-01-10 00:21 ttyue
crw-rw-rw-  1 root tty       3,  95 2007-01-10 00:21 ttyuf
crw-rw-rw-  1 root tty       3,  96 2007-01-10 00:21 ttyv0
crw-rw-rw-  1 root tty       3,  97 2007-01-10 00:21 ttyv1
crw-rw-rw-  1 root tty       3,  98 2007-01-10 00:21 ttyv2
crw-rw-rw-  1 root tty       3,  99 2007-01-10 00:21 ttyv3
crw-rw-rw-  1 root tty       3, 100 2007-01-10 00:21 ttyv4
crw-rw-rw-  1 root tty       3, 101 2007-01-10 00:21 ttyv5
crw-rw-rw-  1 root tty       3, 102 2007-01-10 00:21 ttyv6
crw-rw-rw-  1 root tty       3, 103 2007-01-10 00:21 ttyv7
crw-rw-rw-  1 root tty       3, 104 2007-01-10 00:21 ttyv8
crw-rw-rw-  1 root tty       3, 105 2007-01-10 00:21 ttyv9
crw-rw-rw-  1 root tty       3, 106 2007-01-10 00:21 ttyva
crw-rw-rw-  1 root tty       3, 107 2007-01-10 00:21 ttyvb
crw-rw-rw-  1 root tty       3, 108 2007-01-10 00:21 ttyvc
crw-rw-rw-  1 root tty       3, 109 2007-01-10 00:21 ttyvd
crw-rw-rw-  1 root tty       3, 110 2007-01-10 00:21 ttyve
crw-rw-rw-  1 root tty       3, 111 2007-01-10 00:21 ttyvf
crw-rw-rw-  1 root tty       3, 112 2007-01-10 00:21 ttyw0
crw-rw-rw-  1 root tty       3, 113 2007-01-10 00:21 ttyw1
crw-rw-rw-  1 root tty       3, 114 2007-01-10 00:21 ttyw2
crw-rw-rw-  1 root tty       3, 115 2007-01-10 00:21 ttyw3
crw-rw-rw-  1 root tty       3, 116 2007-01-10 00:21 ttyw4
crw-rw-rw-  1 root tty       3, 117 2007-01-10 00:21 ttyw5
crw-rw-rw-  1 root tty       3, 118 2007-01-10 00:21 ttyw6
crw-rw-rw-  1 root tty       3, 119 2007-01-10 00:21 ttyw7
crw-rw-rw-  1 root tty       3, 120 2007-01-10 00:21 ttyw8
crw-rw-rw-  1 root tty       3, 121 2007-01-10 00:21 ttyw9
crw-rw-rw-  1 root tty       3, 122 2007-01-10 00:21 ttywa
crw-rw-rw-  1 root tty       3, 123 2007-01-10 00:21 ttywb
crw-rw-rw-  1 root tty       3, 124 2007-01-10 00:21 ttywc
crw-rw-rw-  1 root tty       3, 125 2007-01-10 00:21 ttywd
crw-rw-rw-  1 root tty       3, 126 2007-01-10 00:21 ttywe
crw-rw-rw-  1 root tty       3, 127 2007-01-10 00:21 ttywf
crw-rw-rw-  1 root tty       3, 128 2007-01-10 00:21 ttyx0
crw-rw-rw-  1 root tty       3, 129 2007-01-10 00:21 ttyx1
crw-rw-rw-  1 root tty       3, 130 2007-01-10 00:21 ttyx2
crw-rw-rw-  1 root tty       3, 131 2007-01-10 00:21 ttyx3
crw-rw-rw-  1 root tty       3, 132 2007-01-10 00:21 ttyx4
crw-rw-rw-  1 root tty       3, 133 2007-01-10 00:21 ttyx5
crw-rw-rw-  1 root tty       3, 134 2007-01-10 00:21 ttyx6
crw-rw-rw-  1 root tty       3, 135 2007-01-10 00:21 ttyx7
crw-rw-rw-  1 root tty       3, 136 2007-01-10 00:21 ttyx8
crw-rw-rw-  1 root tty       3, 137 2007-01-10 00:21 ttyx9
crw-rw-rw-  1 root tty       3, 138 2007-01-10 00:21 ttyxa
crw-rw-rw-  1 root tty       3, 139 2007-01-10 00:21 ttyxb
crw-rw-rw-  1 root tty       3, 140 2007-01-10 00:21 ttyxc
crw-rw-rw-  1 root tty       3, 141 2007-01-10 00:21 ttyxd
crw-rw-rw-  1 root tty       3, 142 2007-01-10 00:21 ttyxe
crw-rw-rw-  1 root tty       3, 143 2007-01-10 00:21 ttyxf
crw-rw-rw-  1 root tty       3, 144 2007-01-10 00:21 ttyy0
crw-rw-rw-  1 root tty       3, 145 2007-01-10 00:21 ttyy1
crw-rw-rw-  1 root tty       3, 146 2007-01-10 00:21 ttyy2
crw-rw-rw-  1 root tty       3, 147 2007-01-10 00:21 ttyy3
crw-rw-rw-  1 root tty       3, 148 2007-01-10 00:21 ttyy4
crw-rw-rw-  1 root tty       3, 149 2007-01-10 00:21 ttyy5
crw-rw-rw-  1 root tty       3, 150 2007-01-10 00:21 ttyy6
crw-rw-rw-  1 root tty       3, 151 2007-01-10 00:21 ttyy7
crw-rw-rw-  1 root tty       3, 152 2007-01-10 00:21 ttyy8
crw-rw-rw-  1 root tty       3, 153 2007-01-10 00:21 ttyy9
crw-rw-rw-  1 root tty       3, 154 2007-01-10 00:21 ttyya
crw-rw-rw-  1 root tty       3, 155 2007-01-10 00:21 ttyyb
crw-rw-rw-  1 root tty       3, 156 2007-01-10 00:21 ttyyc
crw-rw-rw-  1 root tty       3, 157 2007-01-10 00:21 ttyyd
crw-rw-rw-  1 root tty       3, 158 2007-01-10 00:21 ttyye
crw-rw-rw-  1 root tty       3, 159 2007-01-10 00:21 ttyyf
crw-rw-rw-  1 root tty       3, 160 2007-01-10 00:21 ttyz0
crw-rw-rw-  1 root tty       3, 161 2007-01-10 00:21 ttyz1
crw-rw-rw-  1 root tty       3, 162 2007-01-10 00:21 ttyz2
crw-rw-rw-  1 root tty       3, 163 2007-01-10 00:21 ttyz3
crw-rw-rw-  1 root tty       3, 164 2007-01-10 00:21 ttyz4
crw-rw-rw-  1 root tty       3, 165 2007-01-10 00:21 ttyz5
crw-rw-rw-  1 root tty       3, 166 2007-01-10 00:21 ttyz6
crw-rw-rw-  1 root tty       3, 167 2007-01-10 00:21 ttyz7
crw-rw-rw-  1 root tty       3, 168 2007-01-10 00:21 ttyz8
crw-rw-rw-  1 root tty       3, 169 2007-01-10 00:21 ttyz9
crw-rw-rw-  1 root tty       3, 170 2007-01-10 00:21 ttyza
crw-rw-rw-  1 root tty       3, 171 2007-01-10 00:21 ttyzb
crw-rw-rw-  1 root tty       3, 172 2007-01-10 00:21 ttyzc
crw-rw-rw-  1 root tty       3, 173 2007-01-10 00:21 ttyzd
crw-rw-rw-  1 root tty       3, 174 2007-01-10 00:21 ttyze
crw-rw-rw-  1 root tty       3, 175 2007-01-10 00:21 ttyzf
drwxr-xr-x  4 root root         100 2007-01-09 13:22 .udev
crw-rw-rw-  1 root root      1,   9 2007-01-09 13:22 urandom
crw-rw----  1 root plugdev 254,   0 2007-01-10 00:21 usbdev1.1_ep00
crw-rw----  1 root plugdev 254,   1 2007-01-10 00:21 usbdev1.1_ep81
crw-rw----  1 root plugdev 254,   2 2007-01-10 00:21 usbdev2.1_ep00
crw-rw----  1 root plugdev 254,   3 2007-01-10 00:21 usbdev2.1_ep81
crw-rw----  1 root plugdev 254,   4 2007-01-10 00:21 usbdev3.1_ep00
crw-rw----  1 root plugdev 254,   5 2007-01-10 00:21 usbdev3.1_ep81
crw-rw----  1 root plugdev 254,   6 2007-01-10 00:21 usbdev4.1_ep00
crw-rw----  1 root plugdev 254,   7 2007-01-10 00:21 usbdev4.1_ep81
crw-rw----  1 root root      7,   0 2007-01-10 00:21 vcs
crw-rw----  1 root root      7,   1 2007-01-10 00:21 vcs1
crw-rw----  1 root root      7,   2 2007-01-09 13:22 vcs2
crw-rw----  1 root root      7,   3 2007-01-09 13:22 vcs3
crw-rw----  1 root root      7,   4 2007-01-09 13:22 vcs4
crw-rw----  1 root root      7,   5 2007-01-09 13:22 vcs5
crw-rw----  1 root root      7,   6 2007-01-09 13:22 vcs6
crw-rw----  1 root root      7,   7 2007-01-09 13:22 vcs7
crw-rw----  1 root root      7,   8 2007-01-10 00:21 vcs8
crw-rw----  1 root root      7, 128 2007-01-10 00:21 vcsa
crw-rw----  1 root root      7, 129 2007-01-10 00:21 vcsa1
crw-rw----  1 root root      7, 130 2007-01-09 13:22 vcsa2
crw-rw----  1 root root      7, 131 2007-01-09 13:22 vcsa3
crw-rw----  1 root root      7, 132 2007-01-09 13:22 vcsa4
crw-rw----  1 root root      7, 133 2007-01-09 13:22 vcsa5
crw-rw----  1 root root      7, 134 2007-01-09 13:22 vcsa6
crw-rw----  1 root root      7, 135 2007-01-09 13:22 vcsa7
crw-rw----  1 root root      7, 136 2007-01-10 00:21 vcsa8
crw-rw----  1 root root     10, 130 2007-01-09 13:22 watchdog
prw-r-----  1 root adm            0 2007-01-09 14:12 xconsole
crw-rw-rw-  1 root root      1,   5 2007-01-10 00:21 zero


there is more in that folder but for some reason the shell is only displaying up to 
ptyt9

---

### Post by moshuptrail on 2007-01-08
Isn't a UUID like a "label" ?  That is, could the same device be mounted without the UUID? (since it's giving you grief)

---

### Post by taurus on 2007-01-08
What about

```
sudo fdisk -l
```

---

### Post by ajmorris on 2007-01-08
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1848    14842880    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1849        3646    14442435    5  Extended
/dev/sda3            3647        3648       16033+   e  W95 FAT16 (LBA)
/dev/sda5            1849        1950      819252   82  Linux swap / Solaris
/dev/sda6            1951        3646    13623088+  bb  Boot Wizard hidden

But i have tried mount sda1 and it also didn't work. Also my menu.lst in /boot/grub is pointing at hda. and it can boot.

---

### Post by ajmorris on 2007-01-08
for some reason it works now with sda thanks so much. :)

---

