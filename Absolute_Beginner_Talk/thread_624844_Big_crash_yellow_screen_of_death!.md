---
title: "Big crash yellow screen of death!"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by andybleaden on 2007-11-27
DO others get this

I get random crashes/freezes on kubuntu where my system freezes and I have to restart  ( bit like windoze blue screen of death) 

Happens maybe once a day or if I am on alot maybe 5-6 times.

Usually on firefox but not always and not always when I am using lots of applications which I tend not too. 


Is there a way I can run a chack as to why and find out how to fix. It could be according to one matey video card stuff but as I said it can be with any programme??

It has been the same with dapper and feisty and now with gutsy

No one likes crashes pcs and it also drives wifey up the wall ( she does not like liniux ---linux = new etc so I need to fix this if I can

Let me know if I can post some info up at all

---

### Post by hyper_ch on 2007-11-27
if it just crashes at different things, it might be a problem with your RAM. Check your repositories if you have a "memcheck" or "memory check" program in there. I don't have access to my box right now.

---

### Post by andybleaden on 2007-11-27
oh ok I will look around to see what I can find thanks

Does anyone else know how to check this

By th way when I say it freezes the whole pc freezes ie crashes ie it is not this

[http://en.wikipedia.org/wiki/Yellow_Screen_of_Death](http://en.wikipedia.org/wiki/Yellow_Screen_of_Death)

---

### Post by FuturePilot on 2007-11-27
What are your system specs?

---

### Post by OffAxis on 2007-11-27
> and I have to restart

Do you mean the system (by using the Power or Reset button on the computer case) or the desktop (by using CTRL+ALT+BACKSPACE)?

---

### Post by andybleaden on 2007-11-27
no big button shut down 

ctrl al backspace?

Did not know that worked! Thought that was windows...or was that ctrl alt del...anyway it always needs the power button or reset 

As for specs

Is there a simple scan I can run on konsole and print on here?

---

### Post by andybleaden on 2007-11-27
perhaps there is something in the kinfo centre thing that would allow you to see?

---

### Post by roachk71 on 2007-11-27
Here's a safer method that allows you to restart the PC without potentially losing data or corrupting your file systems:

Hold down Alt-SysRq while issuing these keystrokes: R, E, I, S, U, and B.

Of course, sometimes the system might crash so badly that even this technique (known as the "Magic SysRq" sequence) may not work...

---

### Post by andybleaden on 2007-11-27
Well I tried the both of them and when the pc freezes neither work but thanks as they will have their uses elsewhere later

Back to the yellow screen of death/freeze/crash  is there something I can print here that can help show system set up as well as hard ware?

Let me know and I will do my best

---

### Post by OffAxis on 2007-11-27
Booting off the liveCD, you should have an option (at the bottom of the list) to run memtest, which will run your RAM through an endless series of writes/rewrites across about a dozen different tests.
 Let it run for a while and check to see if it's encountered any errors.
If it crashes at any point during the testing, then it's a hardware problem (RAM, power, possibly heat related) and not software.

And just to clarify, the Alt+tab+backspace will only reset your X server (the graphical desktop). It doesn't shutdown or reboot the running kernel.

---

### Post by andybleaden on 2007-11-28
thanks for all of your suggestions and help so far

I am afraid that I do not have a livecd. never had one I do not think

Is there a way I can run it in konsole or as a seperate programme.

As a clue it does not always happen when the pc is running hot and it can have just started up

Happened last night 3-4 times ( for my wife_ oh dear not popular!)

I am around most of today to work on this if I need to 

Let me know if I can run any listings which I can put up here

Andy

---

### Post by fenian on 2007-11-28
A few questions...

Is this a laptop or desktop computer?
Have you added any extra RAM to the computer?
Are you running desktop effects (compiz fusion)?
What type of graphics card is it?

---

### Post by andybleaden on 2007-11-28
As promised ...answers!

Is this a laptop or desktop computer?

Desktop


 Have you added any extra RAM to the computer?

Maybe a year ago ...I think I have 1.5 gb....can I check anywhere easily?

Are you running desktop effects (compiz fusion)?

Do not think so...is there a place I can check?

 What type of graphics card is it?

That I need to find out...again is there a script that I can run to list this info like that above?

---

### Post by andybleaden on 2007-11-28
_Here are some tests I just ran_

andy@andy-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1487       1457         30          0        218       1017
-/+ buffers/cache:        221       1266
Swap:         2047         34       2013


andy@andy-desktop:~$ free -t -m
             total       used       free     shared    buffers     cached
Mem:          1487       1456         31          0        218       1015
-/+ buffers/cache:        222       1265
Swap:         2047         34       2013
Total:        3535       1490       2044


_I ran lsdev and got this_

Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:09.0                 d000-d0ff
0000:00:0a.0                 d400-d407
0000:00:10.0                 d800-d81f
0000:00:10.1                 dc00-dc1f
0000:00:10.2                 e000-e01f
0000:00:11.0                 0400-047f 0500-050f
0000:00:11.1                 0170-0177 01f0-01f7 0376-0376 03f6-03f6 e400-e40f
0000:00:11.5                 e800-e8ff
0000:00:12.0                 ec00-ecff
acpi                      9
ACPI                           0400-0403   0404-0405   0408-040b   0410-0415   0420-0423
cascade             4
dma                          0080-008f
dma1                         0000-001f
dma2                         00c0-00df
ehci_hcd:usb4            16
eth0                     18
floppy              2     6  03f2-03f5 03f7-03f7
fpu                          00f0-00ff
i8042                  1 12
ide0                     14    01f0-01f7   03f6-03f6   e400-e407
ide1                     15    0170-0177   0376-0376   e408-e40f
keyboard                     0060-006f
parport0                  7  0378-037a
PCI                          0cf8-0cff
pic1                         0020-0021
pic2                         00a0-00a1
pnp                            0500-050f
rtc                       8  0070-0077
serial                       03f8-03ff
timer                     0
timer0                       0040-0043
timer1                       0050-0053
uhci_hcd                       d800-d81f   dc00-dc1f   e000-e01f
vga+                         03c0-03df
via-rhine                      ec00-ecff
VIA8233                  20    e800-e8ff
via@pci:0000:01:00.0         21
vt596_smbus                      0500-0507
wlan0                    19

I then ran lspci and go this

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: D-Link System Inc DWL-510 2.4GHz Wireless PCI Adapter (rev 20)
00:0a.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)


Any use?

---

### Post by OffAxis on 2007-11-28
a little bit.

KM400 is a chipset for an AMD processor.

A little more useful would be 

```
cat /proc/cpuinfo
```

As for not having a live cd, this would have been the disc that you installed from. If you don't have it you can download an .iso from here
[http://kubuntu.org/download.php]("http://kubuntu.org/download.php")
and burn it to disc.

---

### Post by andybleaden on 2007-11-28
Thanks for that. I ran that command and got this ?

Anything else needed?

andy@andy-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm)
stepping        : 0
cpu MHz         : 1262.579
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow ts
bogomips        : 2528.01
clflush size    : 32

---

### Post by andybleaden on 2007-11-28
again if you see any thing there that is alarming or switched off just holler

oh and cheers re the disk



Will sort that out in due course

---

### Post by andybleaden on 2007-11-28
Are you thinking there is a possible video card issue then with that read out above?

---

### Post by OffAxis on 2007-11-28
Video card is a possibility, as is a hard drive error, but the most likely culprit is the RAM or motherboard.
Typically when the video card driver crashes the kernel is able to recover immediately or restart the x server. A hardware issue with the video card will usually show up as artifacts on the screen, garbled images, etc as it deteriorates, or as a full-blown lockup on boot.

I think there's something more fundamental going on; ie RAM, power supply, or motherboard since it's system-wide and neither the x server reboot or Magic SysRq was able to reboot your system.

That being said, it could also be the interaction of the kernel with the hardware on some fundamental level.
You can check the syslog
```
less /var/log/syslog
```
or scan it for errors with something like
```
cat /var/log/syslog | grep error

```
but I doubt you'll come up with anything.

For my money, I'd say hardware, and the easiest thing to check is the RAM.
Running the memtest off the live CD, it'll tell you how each stick of RAM is performing (if I recall properly; it's been a while since I've used it). If you get lucky, you can pull the offending stick(s) and make the wife happy.
Otherwise, you've gotta keep digging.

With the live CD you can bypass the hard drive (and it's boot files) and run off it for a while and see if it crashes. It's got a web browser, word processor, etc. on there.

If you truly think it's a video card issue you can remotely ssh into your kubuntu install a run some programs over the terminal.
```
ssh username@ipaddress
```

(from windows you'd use a program called putty)
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html")

---

### Post by andybleaden on 2007-11-28
I am very grateful for that last help. I have just ren the error log checker thing and got these which do not look too good


I will look at the other possibilities tomorrow morning regarding hardware

Once again a huge thanks for looking into this and what ever help any of you can give would be gratefully recieved

cat /var/log/syslog | grep error

ov 28 13:51:30 andy-desktop kernel: [ 6360.560000] sd 4:0:0:0: scsi: Device off
lined - not ready after error recovery
Nov 28 13:51:30 andy-desktop kernel: [ 6360.560000] sd 4:0:0:0: SCSI error: retu
rn code = 0x00050000
Nov 28 13:51:30 andy-desktop kernel: [ 6360.560000] end_request: I/O error, dev
sdc, sector 48960
Nov 28 13:51:30 andy-desktop kernel: [ 6360.560000] sd 4:0:0:0: SCSI error: retu
rn code = 0x00010000
Nov 28 13:51:30 andy-desktop kernel: [ 6360.560000] end_request: I/O error, dev
sdc, sector 49200
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87003
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87004
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87005
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87006
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87007
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87008
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87009
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87010
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87011
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] Buffer I/O error on device s
dc1, logical block 87012
Nov 28 13:51:30 andy-desktop kernel: [ 6360.568000] lost page write due to I/O e
rror on sdc1
Nov 28 13:54:56 andy-desktop kernel: [ 6567.504000] sd 5:0:0:0: SCSI error: retu
rn code = 0x00050000
Nov 28 13:54:56 andy-desktop kernel: [ 6567.504000] end_request: I/O error, dev
sdc, sector 48864
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] sd 5:0:0:0: SCSI error: retu
rn code = 0x00010000
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] end_request: I/O error, dev
sdc, sector 49120
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] Buffer I/O error on device s
dc1, logical block 7
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] lost page write due to I/O e
rror on sdc1
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] Buffer I/O error on device s
dc1, logical block 123
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] lost page write due to I/O e
rror on sdc1
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] Buffer I/O error on device s
dc1, logical block 219
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] lost page write due to I/O e
rror on sdc1
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] Buffer I/O error on device s
dc1, logical block 11
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] lost page write due to I/O e
rror on sdc1
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] Buffer I/O error on device s
dc1, logical block 68
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] lost page write due to I/O e
rror on sdc1
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] Buffer I/O error on device s
dc1, logical block 72
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] lost page write due to I/O e
rror on sdc1
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] sd 5:0:0:0: SCSI error: retu
rn code = 0x00010000
Nov 28 13:55:05 andy-desktop kernel: [ 6576.640000] end_request: I/O error, dev
sdc, sector 49360
Nov 28 13:55:05 andy-desktop kernel: [ 6576.652000] Buffer I/O error on device s
dc1, logical block 7
Nov 28 13:55:05 andy-desktop kernel: [ 6576.652000] lost page write due to I/O e                                                             rror on sdc1
Nov 28 13:55:05 andy-desktop kernel: [ 6576.652000] Buffer I/O error on device s                                                             dc1, logical block 11
Nov 28 13:55:05 andy-desktop kernel: [ 6576.652000] lost page write due to I/O e                                                             rror on sdc1
Nov 28 13:55:05 andy-desktop kernel: [ 6576.652000] Buffer I/O error on device s                                                             dc1, logical block 12
Nov 28 13:55:05 andy-desktop kernel: [ 6576.652000] lost page write due to I/O e                                                             rror on sdc1
Nov 28 13:55:05 andy-desktop kernel: [ 6576.652000] Buffer I/O error on device s                                                             dc1, logical block 68
Nov 28 13:55:05 andy-desktop kernel: [ 6576.652000] lost page write due to I/O e                                                             rror on sdc1
Nov 28 13:55:07 andy-desktop kernel: [ 6577.552000] rndis_host: probe of 3-1:1.9                                                              failed with error -110
Nov 28 13:55:49 andy-desktop kernel: [ 6620.384000] rndis_host: probe of 3-1:1.9                                                              failed with error -110
Nov 28 14:08:23 andy-desktop kernel: [ 7374.876000] rndis_host: probe of 3-2:1.9                                                              failed with error -110
Nov 28 14:16:02 andy-desktop kernel: [ 7834.024000] rndis_host: probe of 3-2:1.9                                                              failed with error -110



The other system log through up some info from earlier today ...none of which do I know whether it is relevant

Nov 28 07:36:48 andy-desktop syslogd 1.4.1#21ubuntu3: restart.
Nov 28 07:36:48 andy-desktop anacron[7540]: Job `cron.daily' terminated
Nov 28 07:36:48 andy-desktop anacron[7540]: Normal exit (1 job run)
Nov 28 08:00:56 andy-desktop -- MARK --
Nov 28 08:17:01 andy-desktop /USR/SBIN/CRON[8947]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 08:40:56 andy-desktop -- MARK --
Nov 28 09:00:57 andy-desktop -- MARK --
Nov 28 09:17:01 andy-desktop /USR/SBIN/CRON[10024]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 09:25:22 andy-desktop kdm[5033]: X server for display :0 terminated unexpectedly
Nov 28 09:25:23 andy-desktop kernel: [48313.208000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Nov 28 09:25:23 andy-desktop kernel: [48313.208000] agpgart: Device is in legacy mode, falling back to 2.x
Nov 28 09:25:23 andy-desktop kernel: [48313.208000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Nov 28 09:25:23 andy-desktop kernel: [48313.208000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Nov 28 09:26:00 andy-desktop kernel: [48350.960000] rtl8180: Setting SW wep key
Nov 28 09:26:00 andy-desktop kernel: [48350.980000] Linking with fishpond
Nov 28 09:26:00 andy-desktop avahi-daemon[5253]: Withdrawing address record for 10.0.0.51 on wlan0.
Nov 28 09:26:00 andy-desktop avahi-daemon[5253]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.51.
Nov 28 09:26:00 andy-desktop avahi-daemon[5253]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov 28 09:26:00 andy-desktop avahi-daemon[5253]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.51.
Nov 28 09:26:00 andy-desktop avahi-daemon[5253]: New relevant interface wlan0.IPv4 for mDNS.
Nov 28 09:26:00 andy-desktop avahi-daemon[5253]: Registering new address record for 10.0.0.51 on wlan0.IPv4.
Nov 28 09:26:00 andy-desktop kernel: [48351.000000] Associated successfully
Nov 28 09:26:00 andy-desktop kernel: [48351.000000] Using B rates
Nov 28 09:26:01 andy-desktop dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519120
Nov 28 09:26:01 andy-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.5
Nov 28 09:26:01 andy-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov 28 09:26:01 andy-desktop dhclient: All rights reserved.
Nov 28 09:26:01 andy-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 28 09:26:01 andy-desktop dhclient:
Nov 28 09:26:01 andy-desktop dhclient: Listening on LPF/wlan0/00:0d:88:3f:2d:37
Nov 28 09:26:01 andy-desktop dhclient: Sending on   LPF/wlan0/00:0d:88:3f:2d:37
Nov 28 09:26:01 andy-desktop dhclient: Sending on   Socket/fallback
Nov 28 09:26:01 andy-desktop dhclient: DHCPRELEASE on wlan0 to 10.0.0.99 port 67
Nov 28 09:26:01 andy-desktop avahi-daemon[5253]: Withdrawing address record for 10.0.0.51 on wlan0.
Nov 28 09:26:01 andy-desktop avahi-daemon[5253]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.51.
Nov 28 09:26:01 andy-desktop avahi-daemon[5253]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov 28 09:26:01 andy-desktop avahi-daemon[5253]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.51.
Nov 28 09:26:01 andy-desktop avahi-daemon[5253]: New relevant interface wlan0.IPv4 for mDNS.
Nov 28 09:26:01 andy-desktop avahi-daemon[5253]: Registering new address record for 10.0.0.51 on wlan0.IPv4.
Nov 28 09:26:01 andy-desktop avahi-daemon[5253]: Withdrawing address record for 10.0.0.51 on wlan0.
Nov 28 09:26:01 andy-desktop avahi-daemon[5253]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.51.

---

### Post by OffAxis on 2007-11-28
looks like hard drive issues.

Like I mentioned before, you can bypass booting from the hard drive with the live cd (in which case it shouldn't crash while you're using it)
or you can run file system check
```

fsck /dev/sda1

```
or

```
e2fsck /dev/sda1
```

from the command line, although I think one of 'em is supposed to run on every startup.

You can also try

```
sudo apt-get install smartmontools
```

which (assuming that your system has S.M.A.R.T capability and that it's been enabled in the BIOS) will give you some tools to use.

```
sudo -i /dev/sdc1
```
will tell you if it's capable/enabled.

where 
sdc1 = your hard drive

some other useful functions:

```
smartctl -h
```
**h**elp

```
smartctl -H /dev/sdc1
```

**H**ealth of specified device

```
smartctl -t long /dev/sdc1
```

long **t**est for specified device

```
smartctl -a /dev/sdc1
```

**a**ll info for specified device.

I think you can also try a manufacturer's disc for scanning/repair tools, or something like Ultimate Boot CD
[http://ultimatebootcd.com]("http://ultimatebootcd.com")

---

### Post by andybleaden on 2007-11-29
wow 
great and thanks again mate for your input

Tried the smart tools thing but I could not get that to work I am afraid

I will burn the boot cd 

then run with that idea

The earlier commands gave this response

/dev/hda1: recovering journal
Clearing orphaned inode 162395 (uid=1000, gid=1000, mode=0100600, size=4112)
Clearing orphaned inode 795813 (uid=1000, gid=1000, mode=0140755, size=0)
Clearing orphaned inode 795792 (uid=1000, gid=1000, mode=0140755, size=0)
/dev/hda1: clean, 139452/1573728 files, 1266420/3146724 blocks


Does that mean anything?

I also ran this

ext3 recovery flag is clear, but journal has data.
Run journal anywayProject-Id-Version: e2fsprogs
Report-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>
POT-Creation-Date: 2007-07-07 17:42-0400
PO-Revision-Date: 2006-10-14 18:30+0000
Last-Translator: Malcolm Parsons <malcolm.parsons@gmail.com>
Language-Team: English (United Kingdom) <en_GB@li.org>
MIME-Version: 1.0
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 8bit
X-Launchpad-Export-Date: 2007-10-10 08:38+0000
X-Generator: Launchpad (build Unknown)
<y>? yes

/dev/hda1: recovering journal
e2fsck: Bad magic number in super-block while trying to re-open /dev/hda1

What pray tell is a bad magic number?

Andy

---

### Post by andybleaden on 2007-11-30
oh bugger that did it!.

Pc died just after that last post with fatal grub error 17 ...would not reload. MIght be the hard drive afterall ...now its being lokoed into by a kind matey and I get to use my daughterrs (windoze yuk!) machine



That las t command put pay to it ( probably) although maybe it was on the way out...I will be out of here for a while I guess

Thanks again for all your help

Looks like it was hardware after all!

Byyeee

---

### Post by OffAxis on 2007-11-30
Sorry to hear your drive got clobbered.

For anyone else out there (or for your own edification if you make it back this way) here's a link to a page on bellevuelinux.org that explains what a superblock is, what the error means, and most importantly some things to do to try and fix it
[http://www.bellevuelinux.org/superblock]("http://www.bellevuelinux.org/superblock")

using the commands 
**dumpe2fs** device_name | less
and 
**e2fsck** -f -b block_offset device

(the commands were originally for ext2 filesystem but work on ext3 as well)

The dumpe2fs command will give you the location of backup superblocks to use for the e2fsck block_offset command.

---

### Post by andybleaden on 2008-02-04
Well after a few months repair by a very kind neighbour I am back in kubuntu after three horris months using windoze again  YEK!

As for the big crash at the end of this post...it was caused by a partition issue which completely goosed but now I am up and running again at last and I forgot how good kubuntu was.

Thanks first of all to all the advice above on this issue which was very very helpful and I will go back to the last few bits and see where I am up to.

BTW how do I actually 'thank' the people above who posted in this.....is there a special button I am missing?

Andy

---

