---
title: "ati wont work tryed everything help please"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by mclough on 2006-02-21
i have wipe my harddrive 8 times now and started over and i cant get my ati mobility 9700
i have been doing this for 5 days now 
no matter what i did istill get this error in my Xorg log
```
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-686
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfcff0000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0bf1000 at 0xb7acc000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x04000000
(WW) fglrx(0): Failed to set up write-combining range (0xf0000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 800)
```
i tried fixing the mtrr using this how to [http://ubuntuforums.org/showthread.php?t=115104&highlight=fglrx+mtrr](http://ubuntuforums.org/showthread.php?t=115104&highlight=fglrx+mtrr)
and still cant get it to work my mtrr looks like this```
nice@dell9100:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=983552MB: write-back, count=2
reg01: base=0xfeda0000 (4077MB), size=983040MB: write-combining, count=1
nice@dell9100:~$


``` i dont know what to do now ?:???:

---

### Post by mclough on 2006-02-21
anybody have any ideas this driving me nuts

---

### Post by TrendyDark on 2006-02-21
9700 and 9200 have a lot of problems from what I've seen. I use a 9600 Pro and got my drivers installed in less than 10 minutes, but when I try it with my little brother's 9200, no go, doesn't work.

---

### Post by mclough on 2006-02-21
but with a laptop i change the video card

---

### Post by mindwarp on 2006-02-21
I also have a laptop with a 9700 card and am having the same problem.

---

