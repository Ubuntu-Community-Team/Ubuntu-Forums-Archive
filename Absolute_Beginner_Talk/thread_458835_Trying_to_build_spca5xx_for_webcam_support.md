---
title: "Trying to build spca5xx for webcam support"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-05-30
A friend was trying to help me get my webcam working, and after trying easycam2 and having it not detect anything, he came to the conclusion that i should install spca5xx, however when i try to build it( with sudo m-a a-i spca5xx-source
), it fails and gives me this on the last page of the log
```
                                   &#9474;   CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o                   &#8593;                                    
                                   &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:               &#9618;                                    
                                   &#9474; linux/config.h: No such file or directory                                  &#9618;                                    
                                   &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function                &#9618;                                    
                                   &#9474; ‘spca50x_init_isoc’:                                                       &#9618;                                    
                                   &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment   &#9618;                                    
                                   &#9474; from incompatible pointer type                                             &#9618;                                    
                                   &#9474; make[4]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1      &#9618;                                    
                                   &#9474; make[3]: *** [_module_/usr/src/modules/spca5xx] Error 2                    &#9618;                                    
                                   &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'      &#9618;                                    
                                   &#9474; make[2]: *** [default] Error 2                                             &#9618;                                    
                                   &#9474; make[2]: Leaving directory `/usr/src/modules/spca5xx'                      &#9618;                                    
                                   &#9474; make[1]: *** [binary-modules] Error 2                                      &#9618;                                    
                                   &#9474; make[1]: Leaving directory `/usr/src/modules/spca5xx'                      &#9646;                                    
                                   &#9474; make: *** [kdist_build] Error 2                                            &#8595;                                    

```

any ideas? I'm so lost.

Edit: He said I should include this information

```
lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 045e:001d Microsoft Corp. Natural Keyboard Pro
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0545:8088 Xirlink, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

and that we've tried ibmcam with no luck.

---

### Post by loell on 2007-05-30
you might be out of luck with this webcam :(

[http://xirlinkwebcam.sourceforge.net/]("http://xirlinkwebcam.sourceforge.net/") this project would have been useful to you, but the project seems to be not active any more.

---

### Post by virgilnilson on 2007-05-30
> **loell said:**
> you might be out of luck with this webcam :(

[http://xirlinkwebcam.sourceforge.net/]("http://xirlinkwebcam.sourceforge.net/") this project would have been useful to you, but the project seems to be not active any more.

Hmm, is there perhaps not another problem since I cannot build the sca5xx package?

---

### Post by luctor on 2007-05-30
For recent kernels you need the gspca package ([http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html))
but any it looks like your webcam isn't supported by the gspca (former scpa5xx) package.
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by loell on 2007-05-30
> **virgilnilson said:**
> Hmm, is there perhaps not another problem since I cannot build the sca5xx package?

building the fresh spca5xx package would seem pointless anyway because if 

you search the device id , in spca5xx maxhard's page.

```
ID 0545:8088 Xirlink, Inc. 
```

you'll never see this device id.

---

