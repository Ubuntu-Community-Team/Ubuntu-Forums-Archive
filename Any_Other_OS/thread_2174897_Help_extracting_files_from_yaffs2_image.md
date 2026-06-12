---
title: "Help extracting files from yaffs2 image"
date: 2013-09-16
forum: Any Other OS
---

### Post by vertago1 on 2013-09-16
I need to extract a yaffs2 image and I was not able to do it using yaffs2utils. It sees 6 files but won't extract them. I read that unyaffs2 only works with images created using mkyaffs2 and not images copied directly from hardware.

```
unyaffs2 0.2.9: image extracting tool for YAFFS2.
warning: non-root users.
warning: image size (12583168)is NOT a multiple of (2048 + 64).

scanning image 'xxxxxxxxxxx.img'... [done]
scanning complete, total objects: 6

building fs tree ... [done]
building complete, total objects: 1

extracting image into 'mnt/'
[===========================================================================================================================] 1/1 100%

modify files attributes... [done]

operation complete,
files were extracted into 'mnt/'.
```

I tried yaffey and it said:
Warning:
Incomplete page found at end of file

Lastly I compiled the yaffs2 kernel module and tried to install it but I get this error:
```
~/Downloads/yaffs2$ sudo make mi
make -C /lib/modules/3.8.0-30-generic/build M=/home/vertago1/Desktop/Downloads/yaffs2 modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-30-generic'
  INSTALL /home/vertago1/Downloads/yaffs2/yaffs2multi.ko
Can't read private key
  DEPMOD  3.8.0-30-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-30-generic'
```

Next I am going to try padding the file to a multiple of 2048 + 64 to see if that works.

Any help would be appreciated.

---

