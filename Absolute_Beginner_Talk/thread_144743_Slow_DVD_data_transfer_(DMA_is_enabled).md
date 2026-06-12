---
title: "Slow DVD data transfer (DMA is enabled)"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by Josh M on 2006-03-14
Hello, 

I have enabled DMA for my DVD drive (hdd) as per the instructions here:
[https://wiki.ubuntu.com/DMA]("https://wiki.ubuntu.com/DMA")

Data transfer from a DVD to the hard drive is slow, and utilizes the CPU 100%. I have searched these forums for posts about slow DVD drives and most problems seem to be fixed by enabling DMA. 

Here is my output when checking hdparm on hdd:

```

josh@ubuntu:~$ sudo hdparm /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

Does anyone have a fix or ideas about how to get the DVD drive to transfer data faster and stop using all CPU resources?
Thank you in advance.

---

### Post by Pragmatist on 2006-03-15
Please give more information so we can help you, such as:
 1.) What type of CPU (speed, brand, model)
 2.) How much RAM
 3.) Type of Hard Drive (speed, brand, model)
 4.) Type of DVD Drive (speed, brand, model)
 
 5.) Output of this command: ```
uptime
```  Take this a few times over several hours (preferably a day).  Do this WITHOUT doing the DVD-Hard Drive data transfer.  This will give us a baseline performance for your CPU.
 
 6.)  Run this command:  ```
top
``` before, during, and after a transfer.  Write down the distribution of CPU usage by process. **top** defaults to a descending sequence of processes with the top process (the top line) using the most CPU time.  Then give us the list.  We are only interested in the processes that are taking up the bulk of the 100%. Most processes take very little, so it should only be a few lines.
 
 7.) Output of this command: ```
free
```
 8.) Output of this command: ```
df
```
 
 Lets start with those.  It seems like alot but it really isn't.  If  your ambitous you can install the **sysstat **package which will give you the **sar** command which you could read about with ```
man sar
``` This will give you even more system statistics.  The above should be more than enough for now, though.

---

