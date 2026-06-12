---
title: "ATI Driver... Not working"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-10-14
Hey..

I was using the ubuntu guide..to install the ATI driver, once i did that... i restarted my comp, and when it loaded up to ubuntu all i could see a split page one side black the other one brown.and nothin else to see...

could someone tell me how to remove the driver ,using the recovery mode,?  what are the codes for it ?

---

### Post by dbd on 2006-10-19
what guide did you use, was it the ubuntu wiki?

---

### Post by ReaderRat on 2006-10-19
Was it this guide: ATI - How to install the drivers
          **[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)**

---

### Post by Bravo on 2006-10-19
Well, I followed this guide and had some troubles also, the kernel completely crashed at boot, so I had to reboot with Crtl+Del (?)
A roommate found an error, I wonder: "Can I post it here or is this 'Topic stealing'?":confused:
edit: Maybe some usefull information, I followed the second methode of the guide mentioned above

---

### Post by Chaffar on 2006-10-19
Did you first check whether or not your particular ATi card was supported ?

In any case what you want to do is revert to the Xorg driver, which you should do by typing in:

```
sudo dpkg-reconfigure xserver-xorg
```

When unsure, read what the recommended setting is...

You might also have to reinstall libgl1

```
sudo apt-get install --reinstall libgl1-mesa
```

---

### Post by Bravo on 2006-10-19
> **Chaffar said:**
> Did you first check whether or not your particular ATi card was supported ?

In any case what you want to do is revert to the Xorg driver, which you should do by typing in:

```
sudo dpkg-reconfigure xserver-xorg
```
 This has already been done > 

When unsure, read what the recommended setting is...

You might also have to reinstall libgl1

```
sudo apt-get install --reinstall libgl1-mesa
```

This is the error I got:

```

Backtrace:
0:  /usr/bin/X(xf86SigHandler+0x95) [0x477055]
1:  /lib/libc.so.6 [0x2aaaab4271b0]
2:  /usr/lib/xorg/modules/driversfglrx_drv.so(swlDalHelperValidateModeFromDal+049e) [0x2aaaac95267e]
3:  /usr/lib/xorg/modules/drivers/fglrx_drv.so [0x2aaaac934c7d]
4:  /usr/lib/xorg/modules/drivers/fglrx_drv.so(atiddxPreInit+0x6cc) [0x2aaaac921c]
5:  /usr/bin/X(InitOutput+0x9b4) [0x45fe34]
6:  /usr/bin/X(main+0x2fb) [0x4302ab]
7:  /lib/libc.so.6(__libc_start_main+0xdb) [0x2aaaab41449b]
0:  /usr/bin/X(FonFileCompleteXLFD+0x9a) [0x42f95a]

Fatal Server error:
                                                           765,0-1      99%

```

I also want to say that the ati kernel module crashes while it is starting X11
Can anybody help me? :-k

---

### Post by Bravo on 2006-10-20
Nevermind, I did a reinstall, and it seems to work now, thanks to the HowTo from: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI ](https://help.ubuntu.com/community/BinaryDriverHowto/ATI )

---

