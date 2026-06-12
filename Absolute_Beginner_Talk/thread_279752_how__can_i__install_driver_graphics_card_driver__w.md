---
title: "how  can i  install driver graphics card driver  without network"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by sugartown on 2006-10-18
i just install ubuntu on  my uncle's notebook pc 
but  just  can  not  install the Graphics card driver ( Intel GMA 950)without internet ,coz there is  no internet at his home .
is there any  other way to  get  through this situation ?
coz the  command  
```
sudo apt-get update
sudo apt-get install 915resolution
```
doesn't seem to  work ..

here is  some info of the chipset of  mainboard .
```
Field    Value
North Bridge Properties    
North Bridge    Mobile Intel Calistoga-G i945GM
Supported Memory Types    DDR2-400 SDRAM, DDR2-533 SDRAM, DDR2-667 SDRAM
Revision / Stepping    03 / A3
Package Type    1466 Pin FC-BGA
Package Size    3.75 cm x 3.75 cm
Core Voltage    1.05 V
In-Order Queue Depth    12
    
Memory Controller    
Type    Dual Channel  (128-bit)
Active Mode    Dual Channel  (128-bit)
    
Memory Timings    
CAS Latency (CL)    4T
RAS To CAS Delay (tRCD)    4T
RAS Precharge (tRP)    4T
RAS Active Time (tRAS)    12T
Row Refresh Cycle Time (tRFC)    28T
Refresh Period (tREF)    7.8 us
    
Error Correction    
ECC    Not Supported
ChipKill ECC    Not Supported
RAID    Not Supported
ECC Scrubbing    Not Supported
    
Memory Slots    
DRAM Slot #1    256 MB  (DDR2-533 DDR2 SDRAM)
DRAM Slot #2    256 MB  (DDR2-533 DDR2 SDRAM)
    
Integrated Graphics Controller    
Graphics Controller Type    Intel GMA 950
Graphics Controller Status    Enabled
Graphics Frame Buffer Size    8 MB
    
Chipset Manufacturer    
Company Name    Intel Corporation
Product Information    [http://www.intel.com/products/chipsets](http://www.intel.com/products/chipsets)
Driver Download    [http://support.intel.com/support/chipsets](http://support.intel.com/support/chipsets)
Driver Update    [URL="http://driveragent.com?ref=59"]http://driveragent.com?ref=59
```[/URL]

---

### Post by xpod on 2006-10-18
How about taking the laptop to yours or wherever you got a net connection?
I dont think you can "apt-get" without one.
Im not sure if you could burn what you needed and then take it to your uncles machine...thats what ive done before.

Other than that you`ll need someone who knows better than i what your options are...good luck

---

### Post by bulldog on 2006-10-18
Well to install anything to upgrade your Ubuntu,you need an internet connection.

Or you must have a driver cd with the linux drivers on it.

See no other option.

---

### Post by PriceChild on 2006-10-18
You can download the ubuntu packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and burn them to a cd to install later.

---

### Post by sugartown on 2006-10-18
> **PriceChild said:**
> You can download the ubuntu packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and burn them to a cd to install later.

it seems there is  no packg for  intel graphics card  
all ATI ...

---

### Post by sugartown on 2006-10-18
> **xpod said:**
> How about taking the laptop to yours or wherever you got a net connection?
I dont think you can "apt-get" without one.
Im not sure if you could burn what you needed and then take it to your uncles machine...thats what ive done before.

Other than that you`ll need someone who knows better than i what your options are...good luck

I  have my  dvd-rw ,but  just  cannot find the  driver cd online 
.
all  i  do  is  trying not to let the  old man feel helpless when  he try to reinstall the  ubuntu  himself.it is  his  recent hobby after his retirement,and  the  notebook pc is his  birthday  present (from  me  :)).now he  is  got 75 :-D

---

### Post by sugartown on 2006-10-18
> **bulldog said:**
> Well to install anything to upgrade your Ubuntu,you need an internet connection.

Or you must have a driver cd with the linux drivers on it.

See no other option.

the  fact is that i  have  problem  finding the  dirver cd ...

---

### Post by CatKiller on 2006-10-18
> **sugartown said:**
> it seems there is  no packg for  intel graphics card  
all ATI ...

You already know the name of the package you wanted. You included it in your apt-get command in the first post. It's not that difficult to find when you've been given the address where it's stored and you already know the name. Crikey.

---

### Post by podunk on 2006-10-18
i *think* this page has a link and a bunch of instructions for your driver in a .tar file which you can download and compile on your Uncles machine:
[http://support.intel.com/support/graphics/intel945gm/](http://support.intel.com/support/graphics/intel945gm/)

Of course - you will need to download build essential and gosh only knows what else.

Why don't you get the Ubuntu DVD? I think it's got the free repositories on it - it would help you resolve dependencies. You can order it from Amazon  or download it.  The link is here:
[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/dapper/release.1/](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/dapper/release.1/)

---

### Post by DRPend on 2008-01-21
> **PriceChild said:**
> You can download the ubuntu packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and burn them to a cd to install later.

Thanks, I copied in the main libraries I needed form your link. I've got about 2 dozen GLX110 systems to fix. I donated them to a local school (My employer dumped them) and just turned off the add-on cards when they went blank at login. I discovered later that I needed to load legacy drivers (They were old nvidia Model 64 pros) and got a few working. There may be other cards as well and the school won't opt for an internet connect. So I'm going to peruse the packages and build a driver base for old ATI's as well. My only concern is how best to implement the upgrade. Online I just used apt-get, but I'm guessing that won't work here, so I'll have to copy the (untared)  files directly into the system, but I'm not certain at this point which directories to copy these in to.

I'll play around with this for a while before resorting to a post, but if you  pick up my reply on the thread, I'd appreciate any more advice.

Thanks again for the link.

---

