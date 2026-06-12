---
title: "[SOLVED] upgrade 8.10 wireless problem.Macbook 3,1  Broadcom Corporation BCM4328 802."
date: 2008-10-31
forum: Apple Hardware Users
---

### Post by mkgkg on 2008-10-31
Hi, i 've updated today to 8.10.Before under 8.04 wifi was working with the ndiswrapper.
after the boot with 8.10 my wifi didn't work. So, i followed again the tutorial about macbook removing before the ndsiwrapper bcmwl5.inf
<< sudo ndiswrapper -r bcmwl5.inf>>

then i'downloaded again the dell driver and then i cleaned this file /etc/modprobe.d/ndiswrapper.

so i reinstalled the driver with
<<sudo ndiswrapper /~/driver/DRIVER/bcmwl5.inf>>

<<sudo ndiswrapper -l>>
<<sudo ndiswrapper -m>>

then i typed 
<<sudo modprobe ndiswrapper>>

but after reboot wifi doesn t work...

Any idea..thank u

---

### Post by _mario_ on 2008-10-31
> **mkgkg said:**
> Hi, i 've updated today to 8.10.Before under 8.04 wifi was working with the ndiswrapper.
after the boot with 8.10 my wifi didn't work. So, i followed again the tutorial about macbook removing before the ndsiwrapper bcmwl5.inf
<< sudo ndiswrapper -r bcmwl5.inf>>
removing the driver is done with:
```
sudo ndiswrapper -r bcmwl5
```

> **mkgkg said:**
> then i'downloaded again the dell driver and then i cleaned this file /etc/modprobe.d/ndiswrapper.
so i reinstalled the driver with
<<sudo ndiswrapper /~/driver/DRIVER/bcmwl5.inf>>
installation is done with:
```
sudo ndiswrapper -i bcmwl5.inf
```

> **mkgkg said:**
> 
<<sudo ndiswrapper -l>>
<<sudo ndiswrapper -m>>
what does the 1st command output? it should be:
```

bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: wl)

```

> **mkgkg said:**
> 
then i typed 
<<sudo modprobe ndiswrapper>>
then you loaded the module. that means, if everything is fine, wifi should work now...

> **mkgkg said:**
> 
but after reboot wifi doesn t work...
... otherwise it won't work after a reboot too.

as a side note: why do you use a DELL driver, not the Apple provided one? that might cause the trouble. what about using the proprietary wl driver, contained in the package linux-restricted-modules-generic? the wl driver is reported provide better signal quality.

you might also have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=914697&highlight=broadcom").

ciao,
Mario

---

### Post by mkgkg on 2008-10-31
now i have also this problem..after removing ndisrapper by apt-get remove , i've installed th source from sourceforce.net and i have compiled it, but i had a problem during the make command. so i reinstalled by sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common and now doing:
<<sudo -s>>
<<ndiswrapper -i bcm2l5.inf>>
<<ndiswrapper -l>>
<<ndiswrapper -m>>

<< modprobe ndiswrapper >>
after this command i have this message

<<FATAL: Could not open '/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory>>

please help me! i need wifi for working...:(:(

---

### Post by mkgkg on 2008-10-31
ho postato mentre tu mi rispondevi..si i comandi di remove erano quelli li..avevo sbagliato a postare..ora guardo il link..grazie..

---

### Post by _mario_ on 2008-10-31
> **mkgkg said:**
> now i have also this problem..after removing ndisrapper by apt-get remove , i've installed th source from sourceforce.net and i have compiled it, but i had a problem during the make command. so i reinstalled by sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common and now doing:
<<sudo -s>>
<<ndiswrapper -i bcm2l5.inf>>
<<ndiswrapper -l>>
<<ndiswrapper -m>>

<< modprobe ndiswrapper >>
after this command i have this message

<<FATAL: Could not open '/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory>>

the packages ndiswrapper-utils-1.9 ndiswrapper-common only contain the userland (utility) programs. you cannot destroy your kernel module solely by removing these packages! however, the actual driver (from the linux point of view == ndiswrapper.ko) is in linux-image-2.6.27-7-generic, so reinstall:
```
sudo apt-get install --reinstall linux-image-2.6.27-7-generic
```
and reboot. you don't have to reinstall the windows driver files, if they were correctly installed before. (check with ndiswrapper -l).

one more question: do you really have a broadcom wifi device? i thought the 3rd generation used Atheros devices?

last but not least: you should really consider using the wl driver.

ciao,
Mario

---

### Post by dolman25 on 2008-10-31
I have the same wireless card to get mine working i didnt bother with ndisrapper, i just activated it in the "hardware drivers" located in system/administration

---

### Post by mkgkg on 2008-10-31
ahaha..it was easier than i tought...only using the hardware detect drivers and then only click on apply...thank u to all!
Problem solved!

---

### Post by kosumi68 on 2008-10-31
> **mkgkg said:**
> ahaha..it was easier than i tought...only using the hardware detect drivers and then only click on apply...thank u to all!
Problem solved!

Please switch the status of the thread to solved - it makes a tremendous difference to people scanning through the threads.

Thanks!

---

