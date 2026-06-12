---
title: "Need help with SPCA533 Based webcam... no video"
date: 2007-04-03
forum: Apple PPC Users
---

### Post by caseyaberhart on 2007-04-03
Hi all... its been a while since i last posted (2006). I've learned a lot since then.


I have a crappy Sunplus SCPA533 based webcam i want to use with gnome meeting.

I compiled drivers correctly and inserted the modules correctly... but Video4Linux wont see my video device. Linux can see the cameras audio however.

i did a 'dmesg' and got this:

[21184.534187] usbcore: deregistering driver spca5xx
[21184.811947] drivers/usb/media/spca5xx/spca5xx-core.c: driver spca5xx deregist ered
[21297.242921] Linux video capture interface: v1.00
[21298.138846] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX c amera found. ApexDigital Digitrex 2110 spca533
[21298.138899] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_prob e:5480] Camera type JPEG
[21298.173491] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getc apability:1765] maxw 464 maxh 480 minw 176 minh 144
[21298.188419] usbcore: registered new driver spca5xx
[21298.188459] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx drive r 00.60.00 registered
[21512.539360] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21512.759268] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21513.275121] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21513.275158] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21513.275169]
[21513.429012] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21513.446029] ohci_hcd 0000:00:14.0: leak ed c191e600 (#81) state 2
[21513.712906] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21514.225768] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21514.225802] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21514.225814]
[21542.789739] usb 1-1.2: USB disconnect, address 18
[21542.789781] ohci_hcd 0000:00:14.0: leak ed c191e640 (#81) state 2
[21558.662666] usb 1-1.2: new full speed USB device using ohci_hcd and address 1 9
[21558.761075] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX c amera found. ApexDigital Digitrex 2110 spca533
[21558.761132] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_prob e:5480] Camera type JPEG
[21558.762733] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getc apability:1765] maxw 464 maxh 480 minw 176 minh 144
[21558.930252] usb 1-1.2: 400mA over 100mA budget!
[21558.930282] hub 1-1:1.0: 280mA over power budget!
[21612.637930] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21612.854843] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21613.365730] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21613.365765] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21613.365776]
[21618.598164] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21618.613649] ohci_hcd 0000:00:14.0: leak ed c191e680 (#81) state 2
[21618.799585] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21619.320397] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21619.320432] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21619.320444]
[21619.426332] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21619.443335] ohci_hcd 0000:00:14.0: leak ed c191e6c0 (#81) state 2
[21619.645406] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21620.167120] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21620.167165] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21620.167176]
[21625.492993] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21625.509994] ohci_hcd 0000:00:14.0: leak ed c191e700 (#81) state 2
[21625.692920] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21626.211749] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21626.211787] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21626.211799]
[21626.315677] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21626.332704] ohci_hcd 0000:00:14.0: leak ed c191e740 (#81) state 2
[21626.542591] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21627.056427] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21627.056463] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21627.056475]
[21627.802103] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21627.819170] ohci_hcd 0000:00:14.0: leak ed c191e780 (#81) state 2
[21628.087997] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21628.603831] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21628.603868] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21628.603880]
[21628.707762] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21628.724761] ohci_hcd 0000:00:14.0: leak ed c191e7c0 (#81) state 2
[21628.936690] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21629.450507] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21629.450543] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21629.450555]
[21629.693817] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21629.712241] ohci_hcd 0000:00:14.0: leak ed c191e800 (#81) state 2
[21629.884370] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21630.423136] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21630.423173] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21630.423185]
[21630.527062] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21630.544061] ohci_hcd 0000:00:14.0: leak ed c191e840 (#81) state 2
[21630.755997] /home/casey/spca5xx-20060501/drivers/usb/sp5xxfw2.h: [spca50x_Get Firmware:662] FirmWare : 80 0 0 21 4
[21631.271808] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: us b_submit_urb(0) ret -28
[21631.271844] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open :2437]  DEALLOC error on init_Isoc
[21631.271856]
[21663.191517] usb 1-1.2: USB disconnect, address 19
[21663.191558] ohci_hcd 0000:00:14.0: leak ed c191e880 (#81) state 2
[21895.397423] usb 1-1.2: new full speed USB device using ohci_hcd and address 2 0
[21895.513644] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX c amera found. ApexDigital Digitrex 2110 spca533
[21895.513696] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_prob e:5480] Camera type JPEG
[21895.516099] /home/casey/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getc apability:1765] maxw 464 maxh 480 minw 176 minh 144
[21895.684362] usb 1-1.2: 400mA over 100mA budget!
[21895.684394] hub 1-1:1.0: 280mA over power budget!


is my usb bus overloaded??? or is my crappy cam just not gonna work for me... like most windows hardware? why are companies making life a hassle for linux users???

i will also include a device manager screenie too to help anyone diagnose the problem.

i think it lies with v4l.

I am running Breezy on a 333MHz REV D iMac (Dont you dare laugh!)

thanks in advance people!

---

