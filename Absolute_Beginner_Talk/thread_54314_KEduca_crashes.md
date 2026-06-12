---
title: "KEduca crashes"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by bk452 on 2005-08-04
KEduca has been crashing and these are the details:

> (no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1230587456 (LWP 11976)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb6ab5175 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb6ab67d8 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xbfffe650 in ?? ()
#8  0x00000000 in ?? ()
#9  0x00000020 in ?? ()
#10 0x00000000 in ?? ()
#11 0x00000000 in ?? ()
#12 0x00000000 in ?? ()
#13 0x00000000 in ?? ()
#14 0x00000000 in ?? ()
#15 0x00000000 in ?? ()
#16 0x00000000 in ?? ()
#17 0x00000000 in ?? ()
#18 0x00000000 in ?? ()
#19 0x00000000 in ?? ()
#20 0x00000000 in ?? ()
#21 0x00000000 in ?? ()
#22 0x00000000 in ?? ()
#23 0x00000000 in ?? ()
#24 0x00000000 in ?? ()
#25 0x00000000 in ?? ()
#26 0x00000000 in ?? ()
#27 0x00000000 in ?? ()
#28 0x00000000 in ?? ()
#29 0x00000000 in ?? ()
#30 0x00000000 in ?? ()
#31 0x00000000 in ?? ()
#32 0x00000000 in ?? ()
#33 0x00000000 in ?? ()
#34 0x00000000 in ?? ()
#35 0x00000000 in ?? ()
#36 0x00000000 in ?? ()
#37 0x00000000 in ?? ()
#38 0x00000000 in ?? ()
#39 0x00000000 in ?? ()
#40 0x00000000 in ?? ()
#41 0x08180c68 in ?? ()
#42 0xb75b4670 in ?? () from /usr/lib/libqt-mt.so.3
#43 0xbfffe6e8 in ?? ()
#44 0xb740adc1 in QGArray::deleteData () from /usr/lib/libqt-mt.so.3


There is a bug report that says it's missing libkeducapart.  There is a patch called kdeedu_3.4.0-0ubuntu1.diff but I don't know if this is the correct patch.

If it is, how do I install the patch?   ](*,)

---

