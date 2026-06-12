---
title: "fsck interval"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by John E on 2007-02-05
Each time I boot up, a check is done on any volumes which have been mounted more than 20 times since the last time they were checked. Interestingly, this includes being mounted by other OS's, such as Windows.

I have quite a few volumes on my system, some of which can be mounted both by Ubuntu & Windows. This means that a check is being forced on at least 1 volume, almost every time I boot up.

Is there a way to change the frequency between these fsck intervals? So far, it has never once found an error so I'd like to increase the checking interval to a more realistic figure.

---

### Post by Jussi Kukkonen on 2007-02-05
tune2fs is what you are looking for (see *man tune2fs*).

---

### Post by John E on 2007-02-05
Could you please give me an example of usage? I've tried typing various things into a terminal but every time I just get this output:-
```
Usage: tune2fs [-c max_mounts_count] [-e errors_behaviour] [-g group]
        [-i interval[d|m|w]] [-j] [-J journal_options]
        [-l] [-s sparse_flag] [-m reserved_blocks_percent]
        [-o [^]mount_options[,...]] [-r reserved_blocks_count]
        [-u user] [-C mount_count] [-L volume_label] [-M last_mounted_dir]
        [-O [^]feature[,...]] [-T last_check_time] [-U UUID] device
```

---

### Post by Jussi Kukkonen on 2007-02-05
```
jku@luna:~$ sudo umount /dev/hdd2
jku@luna:~$ sudo tune2fs -c 25 /dev/hdd2 
tune2fs 1.38 (30-Jun-2005)
Setting maximal mount count to 25
jku@luna:~$ sudo tune2fs -l /dev/hdd2

     #skipping output here...

Maximum mount count:      25

     #skipping output here...

```

---

### Post by John E on 2007-02-05
Thanks. I was forgetting to add the device name!! :oops:

---

