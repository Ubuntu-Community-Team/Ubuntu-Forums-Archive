---
title: "Using gawk to extract infor from /proc directory"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by samsoft21 on 2007-08-24
Hi,
I am an absolute begginer and I need to write a bash script to extract information from the files in the /proc directory. For example The CPU vendor ID, The version of the kernel, the version of gc, the amount of time since the system was last booted, the amount of memory configured in the system and the amount of memory available etc. Can someone give me an example to get me started?
Thanx:(:(

---

### Post by Bachstelze on 2007-08-24
```
firas@Ana ~ $ cat /proc/version
Linux version 2.6.22-gentoo-r4-ana (root@Ana) (gcc version 4.1.1 (Gentoo 4.1.1-r3)) #3 SMP Tue Aug 21 15:08:57 CEST 2007
firas@Ana ~ $ cat /proc/version | awk '{print $3}'
2.6.22-gentoo-r4-ana

```

(the same result could be achieved with *cut -d ' ' -f 3*)

---

### Post by samsoft21 on 2007-08-24
Thanx,
I can see how that works on the /proc/version file, as there is basically only one line in the file, however, when I look at the cpuinfo file I have more that 1 line, how do I select the specific lines that I need i.e. vendor_id in line 2 or model name in line 5?
Thanx

---

### Post by Bachstelze on 2007-08-24
Two options. You can either use grep select only the lines that contain a given string :

```
firas@Ana ~ $ cat /proc/cpuinfo | grep vendor_id
vendor_id       : GenuineIntel
vendor_id       : GenuineIntel

```

... or use head and tail to select only the nth line :

```
firas@Ana ~ $ cat /proc/cpuinfo | tail -n+5 | head -n 1
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
```

---

