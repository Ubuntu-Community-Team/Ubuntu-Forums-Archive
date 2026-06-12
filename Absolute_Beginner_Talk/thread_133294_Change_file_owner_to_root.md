---
title: "Change file owner to root?"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by mclough on 2006-02-19
i was trying to fix my mtrr so my ati 9700 will work and i used this how to 
[http://ubuntuforums.org/showthread.php?t=115104&highlight=fglrx+mtrr](http://ubuntuforums.org/showthread.php?t=115104&highlight=fglrx+mtrr)
but when i made the fix_mtrr text file i must not have made it as root
so now it want load on startup what would be the best way to fix this 
when i was in failsafe boot my ati card worked for the first time 
but when i rebooted the mtrr whent back to the way it was 
i checked the ownership of the file and its set to me and not root
i like to get it fixed

---

### Post by mclough on 2006-02-20
ok i did sudo chown root /etc/init.d/fix_mtrr and it changed the owher to root 
but not the group so i restarted my laptop and still no go im stuck with the mesa
and this is still in my Xorg.0.log```
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-686-smp
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfcff0000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0bf0000 at 0xb7a75000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x04000000
(WW) fglrx(0): Failed to set up write-combining range (0xf0000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer -
```
i dont know what to do now im out of ideas and my head hurts im going to bed

---

### Post by kaamos on 2006-02-20
Try this:
```

sudo chown root:root /etc/init.d/fix_mtrr

```

---

