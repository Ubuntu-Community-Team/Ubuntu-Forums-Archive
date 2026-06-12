---
title: "Broadcom 4328 v3 issue"
date: 2009-12-15
forum: Apple Hardware Users
---

### Post by Noob37S on 2009-12-15
I have a broadcom 4328 v3 wireless card on my macbook and I was able to activated it under the Hardware Manager as a proprietary driver. But I don't see the wireless connection option under the network connection icon. I see VPN connections and a WIRED but not wireless.
 
I am doing dual boot OS X and Ubuntu 9.10.
 
Any ideas? Thanks guys

---

### Post by linuxopjemac on 2009-12-16
do you have a wireless connection at all? Post me the result of:
```
sudo iwconfig
```
If you see some wireless entry there, you might want to try wicd instead of networkmanager.
Just give me the result of that iwconfig first.

---

### Post by techie99 on 2009-12-16
Try unloading the module (sudo modprobe -r wl) then reload the module (sudo modprobe wl).  You should now connect, however it may freeze... the broadcom module is a PITA and I had consistent, yet random system lock ups.

After days of frustration, and the realization that the bcmwl-source package has been out of date for months, I decided to take matters into my own hands.  The instructions below will compile the most current version of the bcmwl driver and replace the currently supplied version.

This method has the advantage that in the event there is a update, your newer file will simply be replaced during the upgrade.  Keep in mind however that in the event there is a kernel update you will have to repeat the process as the update will overwrite your custom wl.ko.

Also keep in mind that since this a closed source binary "blob" YMMV.

1) [Download]("http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz") the driver from broadcom (  )

2) Make a directory and extract the files in the archive
```

mkdir bcmwl 
tar xvf 'hybrid-portsrc-x86_32-v5.10.91.9.3.tar (1).gz' -C bcmwl

```3) Compile the source:

         3a) You will need to install the build-essential and kernel headers packages
    ```
[URL="apt://build-essential,kernel-header-%60uname,-r%60,
```,3b%29,To,Compile,the,driver"]sudo apt-get install build-essential kernel-header-`uname -r` [/code]    3b) To Compile the driver[/URL]
    ```
cd bcmwl
make clean
make
```4) replace the current driver file with the one that you just compiled.
```
sudo mv ./wl.ko /lib/modules/`uname -r`/updates/dkms/wl.ko
```Good Luck!!!

---

### Post by jb1299 on 2009-12-18
I have a Broadcom 4328 in my iMac which has given me problems too.

In the end installing this driver worked for me:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I know on that page it doesn't list the 4328 explicitly, but the driver works. Since I'm using it right now to connect.

Hope it helps.

---

### Post by Noob37S on 2009-12-18
> **techie99 said:**
> Try unloading the module (sudo modprobe -r wl) then reload the module (sudo modprobe wl). You should now connect, however it may freeze... the broadcom module is a PITA and I had consistent, yet random system lock ups.
 
After days of frustration, and the realization that the bcmwl-source package has been out of date for months, I decided to take matters into my own hands. The instructions below will compile the most current version of the bcmwl driver and replace the currently supplied version.
 
This method has the advantage that in the event there is a update, your newer file will simply be replaced during the upgrade. Keep in mind however that in the event there is a kernel update you will have to repeat the process as the update will overwrite your custom wl.ko.
 
Also keep in mind that since this a closed source binary "blob" YMMV.
 
1) [Download]("http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz") the driver from broadcom ( )
 
2) Make a directory and extract the files in the archive
```

mkdir bcmwl 
tar xvf 'hybrid-portsrc-x86_32-v5.10.91.9.3.tar (1).gz' -C bcmwl

```3) Compile the source:
 
3a) You will need to install the build-essential and kernel headers packages
```
[URL="apt://build-essential,kernel-header-%60uname,-r%60,
```,3b%29,To,Compile,the,driver"]sudo apt-get install build-essential kernel-header-`uname -r` [/URL][/code][,3b%29,To,Compile,the,driver"] 3b) To Compile the driver]("apt://build-essential,kernel-header-%60uname,-r%60,[/code)
```
cd bcmwl
make clean
make
```4) replace the current driver file with the one that you just compiled.
```
sudo mv ./wl.ko /lib/modules/`uname -r`/updates/dkms/wl.ko
```Good Luck!!!
 
When I try to do step 3a, it gives me an error of "Couldn't find package kernel-header-uname -r"....
 
i am new to ubuntu so not sure what to do.... thanks for your help

---

### Post by Noob37S on 2009-12-18
> **jb1299 said:**
> I have a Broadcom 4328 in my iMac which has given me problems too.
 
In the end installing this driver worked for me:
 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
 
I know on that page it doesn't list the 4328 explicitly, but the driver works. Since I'm using it right now to connect.
 
Hope it helps.
 
The driver is the same as what techi99 told me to download.  I installed the one in the Proprietary List and it doesn't list the 4328 either. Neither works for me though...not sure why

---

### Post by Noob37S on 2009-12-18
> **linuxopjemac said:**
> do you have a wireless connection at all? Post me the result of:
```
sudo iwconfig
```
If you see some wireless entry there, you might want to try wicd instead of networkmanager.
Just give me the result of that iwconfig first.
 
 
I managed to get it to display the wireless card now with the code I found in Ubuntu Docs and the code I used;
 
sudo apt-get install bcmwl-kernel-source
 
However, I couldn't get it to connect to my network at home, it kept on TRYING TO CONNECT but could not established.  I got it to work on my desktop but not the MAC....

---

### Post by jb1299 on 2009-12-19
Have you got WPA security on your network?

---

### Post by Noob37S on 2009-12-21
> **jb1299 said:**
> Have you got WPA security on your network?
 
 
Yeah I do have WPA 2 Personal Security On ... Ubuntu does not work with WPA 2?

---

### Post by techie99 on 2009-12-21
`uname -r` needs to be the "tick" mark (the same key as "~")

---

### Post by brijith on 2009-12-21
Hey Guys,
Will it fix the mobile broadband connection issues?

---

### Post by Noob37S on 2009-12-22
> **techie99 said:**
> `uname -r` needs to be the "tick" mark (the same key as "~")
 
oh oops, I thought it is a single quotation mark. I will try it later when I get home. Thanks techie99

---

### Post by mcdjork on 2009-12-22
I decided to update the STA driver because my 64 bit system was frequently freezing up while using it. When I switched to the bwfcutter, the problem stopped. The trade-off, however, was the firmware driver was not able to connect to my PEAP network at work. 

I've followed the instructions here to update the STA driver. Immediately upon connecting with it though, my system froze up (caps lock blinking etc). How can I verify that my update was successful and that I am indeed using the updated STA driver?

---

### Post by techie99 on 2009-12-23
Honestly your best bet is instead of chasing down what is/isn't loaded is to start clean. so here goes.....

bwfcutter is a broadcom firmware extractor that is used in conjunction with the b43 driver and other derivatives. if you have both loaded I could definitely see an issue arising.  I would unload the 3rd party broadcom driver and the wl driver (to be safe) first then try to reload it.  Like so:

```
sudo modprobe -r b43
sudo modprobe -r b43legacy
sudo modprobe -r ssb
sudo modprobe -r bcm43xx
sudo modprobe -r wl
sudo modprobe wl
```Then try to connect.  If that works you need to add the other broadcom drivers to your blacklisted driver file and add wl to your modules file. This will make the temporary modifications we made stick.

**Blacklist b43 (and the like): **
```
sudo gedit /etc/modprobe.d/blacklist.conf
```append this to the end of the file:
```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
```[B]Add wl to list of modules to automatically load at startup:
[/B]```
sudo gedit /etc/modules
```append this to the end of the file

```
wl
```That should take care of it.  Good Luck!!

---

