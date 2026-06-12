---
title: "Mint shutsdown randomly"
date: 2013-01-02
forum: Any Other OS
---

### Post by conradin on 2013-01-02
HI All,
I have installed Linux Mint14 recently, and it works decently, but it shutsdown randomly. Im certain its not a hardware issue, how can i find out why this is happening?
```

$ last -x
s        pts/1        :0.0             Wed Jan  2 21:57   still logged in   
s        tty8         :0               Wed Jan  2 21:52   still logged in   
runlevel (to lvl 2)   3.5.0-17-generic Wed Jan  2 21:51 - 22:02  (00:10)    
reboot   system boot  3.5.0-17-generic Wed Jan  2 21:51 - 22:02  (00:10)    
s        pts/1        :0.0             Wed Jan  2 13:11 - crash  (08:40)    
s        tty8         :0               Wed Jan  2 13:00 - crash  (08:51) 

```

heres last, noting a system crash.

---

### Post by vasiliscnisrok on 2013-01-03
you check your computer's memory with MemTest?

---

### Post by xenopeek on 2013-01-03
Is it shutting down (i.e., powering down), or is it freezing the image on the screen and becoming unresponsive?

To give us some background, please share the output of the following command. It will give us some details about your hardware and such.
```
inxi -Fxz
```

---

### Post by conradin on 2013-01-03
This is flat out, full shut down. no warning. shutsdown instantly, seems to happen when Im watching hulu or youtube, but that could be coinscience. 

```

$inxi -Fxz

System:    Host: x Kernel: 3.5.0-17-generic x86_64 (64 bit, gcc: 4.7.2) Desktop: N/A Distro: Linux Mint 14 Nadia
Machine:   System: Gateway product: GM5472 version: 910
           Mobo: ELITE model: MCP61PM-AM version: 1.0 Bios: Phoenix version: 6.00 PG date: 04/27/2007
CPU:       Dual core AMD Athlon 64 X2 5000+ (-MCP-) cache: 1024 KB flags: (lm nx sse sse2 sse3 svm) bmips: 10447.1 
           Clock Speeds: 1: 2600.00 MHz 2: 2600.00 MHz
Graphics:  Card-1: NVIDIA C61 [GeForce 6150SE nForce 430] bus-ID: 00:0d.0 
           Card-2: NVIDIA GF104 [GeForce GTX 460 SE] bus-ID: 02:00.0 
           X.Org: 1.13.0 driver: nvidia Resolution: 1680x1050@60.0hz 
           GLX Renderer: GeForce GTX 460 SE/PCIe/SSE2 GLX Version: 4.3.0 NVIDIA 310.19 Direct Rendering: Yes
Audio:     Card-1: NVIDIA GF104 High Definition Audio Controller driver: snd_hda_intel bus-ID: 02:00.1
           Card-2: NVIDIA MCP61 High Definition Audio driver: snd_hda_intel bus-ID: 00:05.0
           Card-3: Tenx driver: USB Audio usb-ID: 1130:1620
           Card-4: Logitech Webcam C310 driver: USB Audio usb-ID: 046d:081b
           Sound: Advanced Linux Sound Architecture ver: 1.0.25
Network:   Card: Marvell 88E8039 PCI-E Fast Ethernet Controller driver: sky2 ver: 1.30 port: 9c00 bus-ID: 03:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 500.1GB (15.1% used) 1: id: /dev/sda model: ST3500413AS size: 500.1GB 
Partition: ID: / size: 455G used: 71G (17%) fs: ext4 ID: swap-1 size: 4.16GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A gpu: 0.0:35C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 160 Uptime: 25 min Memory: 1588.5/3828.1MB Runlevel: 2 Gcc sys: 4.7.2 Client: Shell inxi: 1.8.4

```

---

### Post by xenopeek on 2013-01-03
Thanks for sharing the inxi output. You might need a different graphics card driver, but that's just a wild guess and I'm not familiar enough with AMD or Nvidia. Having two graphics cards sets of an alarm bell though; is that well supported by Nvidia's driver? Else you might want to look into any option to switch the one or the other off.

Temperature seems fine; insufficient cooling is sometimes the cause.

So you'll have to dig a little deeper. After the next crash, note the time of the crash and to make it more clear leave the computer off for some minutes. After loggin in again, look at your /var/log/syslog or /var/log/syslog.1 file and see if there are any errors in the minute running up to the crash. You can read these files with Gedit or other text editor, and the beginning of the line has a timestamp for you to match up to the moment of the crash.

---

### Post by tgalati4 on 2013-01-03
Set up some temperature monitors with alarms in your panel.  Check your BIOS thermal limits.  Temperature shutdowns tend to quick and without warning.

Also, video streaming tends to put strain on the IO bridge which on some motherboards contains the memory controller and the ethernet controller AND the sound controller.  Video streaming is the perfect storm to cause that chip to heat up and cause an instant crash.

Failing video cards can also cause the system to crash with no warning.

---

### Post by Habitual on 2013-01-03
> **tgalati4 said:**
> set up some temperature monitors with alarms in your panel.  Check your bios thermal limits.  Temperature shutdowns tend to quick and without warning....

+1

---

### Post by #1udancqSHv% on 2013-01-04
> **tgalati4 said:**
> Set up some temperature monitors with alarms in your panel.  Check your BIOS thermal limits.  Temperature shutdowns tend to quick and without warning.

Also, video streaming tends to put strain on the IO bridge which on some motherboards contains the memory controller and the ethernet controller AND the sound controller.  Video streaming is the perfect storm to cause that chip to heat up and cause an instant crash.

Failing video cards can also cause the system to crash with no warning.

+1 all this.

Both my wife and I have had problems with no-warning shutdowns due to overheating. It's worth tracking it to see whether you need to make any hardware or software tweaks (for example if video is causing overheating on Linux Mint, but not on Windows).

Have you tried posting in the Linux Mint forums too? I've found them to be a friendly bunch too - [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

Good luck with sorting this out.

---

### Post by #1udancqSHv% on 2013-01-04
> **xenopeek said:**
> Thanks for sharing the inxi output. You might need a different graphics card driver, but that's just a wild guess and I'm not familiar enough with AMD or Nvidia. Having two graphics cards sets of an alarm bell though; is that well supported by Nvidia's driver? Else you might want to look into any option to switch the one or the other off.

Temperature seems fine; insufficient cooling is sometimes the cause.

So you'll have to dig a little deeper. After the next crash, note the time of the crash and to make it more clear leave the computer off for some minutes. After loggin in again, look at your /var/log/syslog or /var/log/syslog.1 file and see if there are any errors in the minute running up to the crash. You can read these files with Gedit or other text editor, and the beginning of the line has a timestamp for you to match up to the moment of the crash.

This is all excellent advice too, and well worth trying. I'm not directly familiar with the particular hardware you listed, but the two graphics cards jumped out at me too.

The syslog advice is good stuff as well.



(OT just noticed your Alizée avatar too=D>   )

---

