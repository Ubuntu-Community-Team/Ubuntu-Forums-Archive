---
title: "Lost wireless on upgrade to feisty"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by reslider on 2007-08-15
I had my wireless working in 6.10 and lost it in the upgrade to feisty. I have a usb wireless adapter. It is the 2WIRE usb adapter, when I type lsusb it gives me 1630:005

I think it may be a problem with ndiswrapper, when I go to System-Administration-Windows Wireless Drivers. I see something installed it does not have a name and states that the driver is not present 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40729&d=1187195049[/IMG]


 however when I type
ndiswrapper -l in the terminal I get

```
tyler@ubuntu:~$ ndiswrapper -l
wlanuig : driver installed
        device (1630:0005) present

```

These are some other commands I typed in to try and help troubleshoot

```
tyler@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:5B:10:1A:E9
                    ESSID:"2WIRE243"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
``` 

```
tyler@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:47:5E:E4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89794 (87.6 KiB)  TX bytes:89794 (87.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:60:B3:49:84:A0  
          inet6 addr: fe80::260:b3ff:fe49:84a0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3191007 (3.0 MiB)  TX bytes:391076 (381.9 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:60:B3:49:84:A0  
          inet addr:169.254.7.210  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

```

```
tyler@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"2WIRE243"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1B:5B:10:1A:E9   
          Bit Rate=6 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I tired to blacklist bcm43xx, that changed nothing
I also read somewhere that someone had the same problem and installed "linux-386" from the Synaptic Package Manager, but when I tried to do that all the installs just falied. That link is here [URL="http://ubuntuforums.org/showthread.php?t=378477"]

I tried finding more info in other threads but im not sure where to start, any help would be awesome
Thanks, Tyler

---

### Post by 4KvRMU7Nnv on 2007-08-15
hmmm...You may need to make sure you have the ndiswrapper kernel drivers for the new kernel that is in feisty.  letssee...Well...I don't know how to do this...but i know that when you upgrade kernels, ndiswrapper won't work try reinstalling it i guess...

---

### Post by reslider on 2007-08-15
```
tyler@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@01:0d.0
       logical name: eth0
       version: 10
       serial: 00:0c:6e:47:5e:e4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:b400-b4ff iomemory:dc000000-dc0000ff irq:20
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:60:b3:49:84:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=2Wire,04/08/2004, 2.3.1.3 ip=192.168.1.69 link=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by reslider on 2007-08-15
> **d3br074 said:**
> hmmm...You may need to make sure you have the ndiswrapper kernel drivers for the new kernel that is in feisty.  letssee...Well...I don't know how to do this...but i know that when you upgrade kernels, ndiswrapper won't work try reinstalling it i guess...

I tried uninstalling all versions of ndiswrapper and then reinstalling only 1.9, still the same thing. It says the device is not present. Also in 6.10 the wireless network driver window would say that the driver is wlanuig my driver for my network card, where as now its doesn't really say anything

---

### Post by reslider on 2007-08-15
I don't want to double post this is there anyway I can delete this and move it to the networking forums?

---

### Post by reslider on 2007-08-15
*bump*

---

### Post by fredj on 2007-08-15
Start by uninstallng ndiswrapper since it's not working. Open a terminal and type
sudo modprobe -r ndiswrapper
Now in the same terminal check your version of ndiswrapper. Type ndiswrapper -v to get the 
version, post the output from that here. We need to know if you have the defective version of
ndiswrapper that is in the Feisty repositories.
.

---

### Post by jw5801 on 2007-08-15
Did you input ```
sudo modprobe ndiswrapper
``` to load the ndiswrapper kernel modules? You may or may not need to readd ndiswrapper to /etc/modules as well.

As for the moving the thread thing, just wait for a mod to come along and they'll move it since you asked nicely!

EDIT: Also see above!

---

### Post by reslider on 2007-08-16
I had it working, I went back to 6.10 then upgraded to 7.04 but this time I let it download instead of using the disk. Well for some reason my video card wasn't working. So as it was about to boot up I got the X error and had to reconfigure. To test it out, I did the command startx and everything started up fine. I did the command 'sudo modprobe ndiswrapper' and then opened firefox and I was connected. 
So I thought that fixed it. So I was still trying to make sure my video card would work I tried to open the restricted device manager, but it told me I needed to install the 'linux-restricted-modules-2.6.20-16-generic' so I installed it, got my graphics card working under the right driver and  when I rebooted it, my internet stopped working. 
I thought maybe that had something to do with the wireless, seeing as I didn't change anything else, so I tried to uninstall it, but had no luck. It still doesn't work.

I did not try the ndiswrapper version thing yet because I did get it working for a little bit. But if need to that will be my next step. 

Thanks for the help, Tyler

---

### Post by jw5801 on 2007-08-16
Check that ndiswrapper is on the kernel modules list ```
gksudo gedit /etc/modules
``` Otherwise you will need to run "modprobe ndiswrapper" every time you start up to get your wireless working. (So add it to the list :p)

That won't immediately get it working though, you'll need to run "sudo modprobe ndiswrapper" for this session, but it'll eliminate the need for it next time you reboot.

---

### Post by reslider on 2007-08-16
thanks for the help, but 'sudo modprobe ndiswrapper doesn't work any more. So I went back and the version I have is

```
tyler@ubuntu~$ ndiswrapper -v
utils Error: no version specified!
driver version:          1.38
vermagic:        2.6.20-16-generic SMP mod_unload 586
```

I't noticed '2.6.20-16-generic' this is the same thing I installed right before my wireless stopped working. Im not sure if this could have anything to do with it. 
When I tried to uninstall it though it didn't work.

---

### Post by jw5801 on 2007-08-16
2.6.20-16 is your kernel version. You're gonna need to reinstall ndiswrapper as your install of it isn't quite working correctly. It's probably best to get the newest version and compile it yourself. Follow [this](http://ubuntuforums.org/showthread.php?t=297092) howto for that. It's for a different wireless card but installing ndiswrapper is the same. Just ignore the stuff about downloading things from Dell (anything that mentions R151517.EXE) and anywhere it says bcmwl5, replace that with your driver.

Make sure you do all the "cleaning your system" parts at the start as that's the most important to you right now.

---

### Post by reslider on 2007-08-17
> **jw5801 said:**
> 2.6.20-16 is your kernel version. You're gonna need to reinstall ndiswrapper as your install of it isn't quite working correctly. It's probably best to get the newest version and compile it yourself. Follow [this](http://ubuntuforums.org/showthread.php?t=297092) howto for that. It's for a different wireless card but installing ndiswrapper is the same. Just ignore the stuff about downloading things from Dell (anything that mentions R151517.EXE) and anywhere it says bcmwl5, replace that with your driver.

Make sure you do all the "cleaning your system" parts at the start as that's the most important to you right now.


So I reinstalled 7.04, to make sure the system was clean, and I went through the instructions, and It didn't work for me.

I got stalled up on the 'sudo make uninstall' I did it for quite some time and never got it to say fully removed. I probably tried well over 50 times. So I figured maybe keep going on after that and my computer would freeze when trying to do the command 'sudo modprobe ndiswrapper'

```

tyler@ubuntu:~$ sudo ndiswrapper -l
wlanuig : driver installed
        device (1630:0005) present
```

```
tyler@ubuntu:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586
```

```
tyler@ubuntu:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by reslider on 2007-08-17
I just tried to install the driver using ndisgtk, when I it the install button to install my driver my computer froze up. I remember this happening another time I had feisty installed. Could it be I have a bad install, maybe try to download and re-burn a disk?

---

### Post by jw5801 on 2007-08-17
You could just run the disc-check on the the disc you already have to save yourself some trouble.
Also "make uninstall" never actually says "completely removed," it only gives you anything extra if it has files to delete that it can tell you about, so if it didn't say anything different that means it doesn't have anything to delete, ie it's uninstalled.

---

### Post by reslider on 2007-08-17
> **jw5801 said:**
> You could just run the disc-check on the the disc you already have to save yourself some trouble.
Also "make uninstall" never actually says "completely removed," it only gives you anything extra if it has files to delete that it can tell you about, so if it didn't say anything different that means it doesn't have anything to delete, ie it's uninstalled.

Well I did the check, and nothing was wrong. I guess I will go back to using 6.10. Seeing as everything works with that. Just curious if im having problems upgrading now to feisty, will I not be able to upgrade any farther past that?

---

