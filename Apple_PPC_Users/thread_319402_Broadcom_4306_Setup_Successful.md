---
title: "Broadcom 4306 Setup Successful"
date: 2006-12-15
forum: Apple PPC Users
---

### Post by wildabeast on 2006-12-15
I am relieved to report that I successfully set up my iBook G4 12” with an Airport Extreme card with the Broadcom 4306 chipset.  I installed Dapper 6.0.6.1 with an ethernet connection, restarted (after doing all of the necessary updates) and installed bcm43xx-fwcutter.  I also located and downloaded the file that had the firmware I thought I might want.  Although many firmware options (bcmwl5.sys, wl_x etc.) may work for the same purpose, the one I used was

  filename :  wl_apsta.o
  version  :  3.130.20.0
  MD5      :  e08665c5c5b66beb9c3b2dd54aa80cb3

I then unplugged the ethernet connection and restarted.  Then I typed:

sudo bcm43xx-fwcutter -w /lib/firmware /(path to firmware to be extracted)/

sudo modprobe bcm43xx

sudo ifconfig eth1 down

sudo ifconfig eth1 up

sudo iwconfig eth1 (your key)

sudo iwconfig (your essid)

sudo iwconfig (your ap)

sudo dhclient eth1

and it connected, just like that.  In fact it is just like the procedure for the Broadcom 4318 chipset, but I had done some research before trying it myself and found very little information on this particular setup procedure, and in fact some walk throughs that said it wouldn't be possible without ndiswrapper (which of course is not an option for those of the PPC persuasion.)  Now I guess I'll try installing Edgy....

-Will

---

