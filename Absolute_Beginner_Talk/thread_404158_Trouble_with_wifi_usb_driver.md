---
title: "Trouble with wifi usb driver"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-04-08
Hey folks,

I have been trying to follow the tutorial from 

[http://ubuntuforums.org/showthread.php?t=283254](http://ubuntuforums.org/showthread.php?t=283254)

The point is to be able to install a working zd1211 driver for my USB wifi adapter (the same one he lists here - Gigafast WF748-CUI).  It hasn't worked.
  	
J[COLOR="Sienna"]oin Date: Sep 2006
Beans: 2
Gigafast WF748 USB wifi adapter, Ubuntu Dapper, ndiswrapper \ HOWTO
This is a quick HOWTO on getting the Gigafast WF748-CUI USB2.0 wifi b/g adapter to work in Ubuntu Dapper using ndiswrapper. I tried a number of the zd1211 drivers and none of them worked (more info on this below), and ONLY the -b driver (zd1211b, that is) worked, as did ndiswrapper.

Installing the WF748 using the zd1211b driver
Ubuntu comes with a driver, zd1211.ko, which didn't work for me at all. It would load, but it wouldn't associate with the adapter. So you have to go get the source and compile it. I used the driver found at [http://zd1211.ath.cx/](http://zd1211.ath.cx/). Note that there are two drivers there: the zd1211 driver and the zd1211rw. The -rw is the rewrite project for the kernel (i.e. the one that comes with Ubuntu and doesn't work). Get the other one. I got release r83.

Untar the file and enter the directory
$ tar zxvf zd1211-driver-r83.tgz
$ cd zd1211-driver-r83
We have to modify the Makefile to reflect the kernel version and location, as well as to make the zd1211b module.
$ sudo vim Makefile
The following lines should be present:
KERN_26=y
KERNEL_SOURCE=/usr/src/linux
ZD1211REV_B=1 #default is 0, if present
[/COLOR]

Then, he instructs to makefile.  I tried that, but came back with errors - directories not found, etc.
 
Anyhow, this is very frustrating.  I need wifi access in order for me to be able to use ubuntu on this machine.

Please help.  

(Or, if you know a sure-fire wifi adapter that will work with ubuntu, let me know.  I may just go buy it.)

Cheers - 

L in AZ

---

### Post by siciliancasanova on 2007-04-08
I replied to your other related post, have you tried [this thread]("http://ubuntuforums.org/showthread.php?p=458488")?

---

### Post by Hieronymus on 2007-04-08
Can you post the output you get when trying to make the file?

Jeroen

---

### Post by awiggin on 2007-04-09
To all who know more than me:

I have now been trying to follow this step-by-step guide:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

I get hung up on Step 2 which says:

[COLOR="Navy"]user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`  [/COLOR]

When I type that in, I get this:

[COLOR="Navy"]E:  Couldn't find package linux-headers-uname-r[/COLOR]

Help!

---

### Post by awiggin on 2007-04-09
I typed in the command wrong, so I got past step 2.

However, at this step:

[COLOR="DarkSlateBlue"]sudo make both[/COLOR]

I get the following error:

[COLOR="DarkSlateBlue"]No rule to make target `modules'.  Stop.[/COLOR]

And then I am out, unable to go further.

Thanks in advance.

---

### Post by Hieronymus on 2007-04-09
I would suggest to start all over again with the step-by-step guide to make use you didn't make any error. When you arrived at the step with a make rule please use the -d options for debug information. If it again gives an error post the output of all the steps you made here. Maybe we can filter an mistake or problem out. 

Jeroen

---

### Post by awiggin on 2007-04-10
At the step where it asks me to type in:  

~$ sudo apt-get install linux-headers-`uname -r` 

I get the following:

```
 bash uname-r : command not found
Reading package lists...done
Building dependency tree
Reading state information...done
Package linux-headers is not installed so not removed 
```

I can't go past that step.

Any ideas?

Thanks,
Lance

---

### Post by awiggin on 2007-04-10
I tried putting a space where I didn't see one (`uname -r`) and I was able to get past that step, I think.

Then I got another error.  I downloaded the driver.  Then I typed in:

sudo make both and I got the following error:

```

make ZD1211REV_B=0
make[1]: Entering directory `/home/lance/zd1211-driver-r83'
/lib/modules/2.6.17-11-386/build
/home/lance/zd1211-driver-r83
-I/home/lance/zd1211-driver-r83/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/lance/zd1211-driver-r83 modules
make[2]: Entering directory `/lib/modules/2.6.17-11-386/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.17-11-386/build'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/lance/zd1211-driver-r83'
make: *** [both] Error 2

```

This is enormously frustrating.  Please let me know what I can do.

Thanks,
Lance

---

### Post by Hieronymus on 2007-04-12
Try this: 

```

apt-get autoclean
uname -r
apt-cache search linux-headers-[here the name you found with uname -r]
apt-get install linux-headers-[what you found with the above command]

```

Jeroen

---

### Post by AMDAthlonX2 on 2007-04-13
Is the ndiswrapper folder on your desktop? if so, move it to /root and try it again

---

### Post by augustose on 2008-01-03
I have the same problem with the same device 

[http://www.gigafast.com/products/product_drivers/WF748-CUI_drivers.htm](http://www.gigafast.com/products/product_drivers/WF748-CUI_drivers.htm)

Any help will be great !

---

