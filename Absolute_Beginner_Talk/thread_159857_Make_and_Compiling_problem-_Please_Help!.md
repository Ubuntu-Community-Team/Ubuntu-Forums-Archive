---
title: "Make and Compiling problem- Please Help!"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by mantrasu on 2006-04-13
Hello all,

I am trying to compile a driver for a DLINK G122 Wireless Adapter and am encountering a problem when I run the "make" command.  :( 

The error was 
```

sethman@SethKubuntu:~/rt2570-cvs-2006041119/Module$ sudo make
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
rt2570.ko failed to build!
make: *** [module] Error 1

```

I went onto IRC and got some help, but the person left before the problem was fixed. I was messing around with "/lib/modules/2.6.12-9-386/build" and "/usr/src/linux-source-2.6.12". I untarred "/usr/src/linux-source-2.6.12" and then made "/lib/modules/2.6.12-9-386/build" a soft link to "/usr/src/linux-source-2.6.12", which was what the person who was helping me thought might work, but then left before I tested it. Before,  "/lib/modules/2.6.12-9-386/build" was just an empty folder.
Here are the commands he/she had me use:
```

cd /usr/src
tar -jxvf linux-source-2.6.12.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux

ls -ld /lib/modules/2.6.12-9-386/build
rm -rf /lib/modules/2.6.12-9-386/build
ln -s /usr/src/linux-source-2.6.12 /lib/modules/2.6.12-9-386/build

```

It got rid of the first set of errors and now generates thousands of errors, but it does look like" make" is doing something this time. Here is the end of the error messages it generated:
```

{standard input}:3939: Error: symbol `security' is already defined
{standard input}:3969: Error: symbol `data' is already defined
{standard input}:4069: Error: symbol `destructor' is already defined
{standard input}:4075: Error: symbol `open' is already defined
{standard input}:4093: Error: symbol `poll' is already defined
{standard input}:4195: Error: symbol `dev' is already defined
{standard input}:4219: Error: symbol `func' is already defined
{standard input}:4225: Error: symbol `data' is already defined
{standard input}:4297: Error: symbol `driver' is already defined
{standard input}:4303: Error: symbol `version' is already defined
{standard input}:4368: Error: symbol `data' is already defined
{standard input}:4374: Error: symbol `version' is already defined
{standard input}:4386: Error: symbol `data' is already defined
{standard input}:4602: Error: symbol `reserved' is already defined
{standard input}:5069: Error: symbol `nlink' is already defined
{standard input}:5075: Error: symbol `size' is already defined
{standard input}:5099: Error: symbol `owner' is already defined
{standard input}:5105: Error: symbol `next' is already defined
{standard input}:5111: Error: symbol `parent' is already defined
{standard input}:5123: Error: symbol `data' is already defined
{standard input}:5435: Error: symbol `release' is already defined
{standard input}:5459: Error: symbol `dev' is already defined
{standard input}:5543: Error: symbol `context' is already defined
{standard input}:5549: Error: symbol `complete' is already defined
{standard input}:5561: Error: symbol `pipe' is already defined
{standard input}:5591: Error: symbol `complete' is already defined
{standard input}:5627: Error: symbol `u' is already defined
{standard input}:6659: Error: symbol `KeyMaterial' is already defined
{standard input}:6719: Error: symbol `Ssid' is already defined
{standard input}:6773: Error: symbol `Bssid' is already defined
{standard input}:6851: Error: symbol `data' is already defined
{standard input}:7402: Error: symbol `Bssid' is already defined
{standard input}:7534: Error: symbol `Ssid' is already defined
/home/sethman/rt2570-cvs-2006041119/Module/rt2570sw.h:1510: error: storage size of `iw_stats' isn't known
/home/sethman/rt2570-cvs-2006041119/Module/rt2570sw.h:1571: error: storage size of `SendTxWaitQueue' isn't known
{standard input}:8097: Error: symbol `KeyLength' is already defined
{standard input}:8163: Error: symbol `Len' is already defined
{standard input}:8523: Error: symbol `BSSID' is already defined
{standard input}:8613: Error: symbol `WirelessPacket' is already defined
{standard input}:9015: Error: symbol `Key' is already defined
{standard input}:9063: Error: symbol `SupportedRates' is already defined
{standard input}:9537: Error: symbol `AvgRssi' is already defined
{standard input}:10076: Error: symbol `next' is already defined
{standard input}:10454: Error: symbol `next' is already defined
{standard input}:10472: Error: symbol `head' is already defined
{standard input}:10478: Error: symbol `tail' is already defined
{standard input}:10496: Error: symbol `head' is already defined
{standard input}:10502: Error: symbol `tail' is already defined
{standard input}:10520: Error: symbol `head' is already defined
{standard input}:10526: Error: symbol `tail' is already defined
{standard input}:11646: Error: symbol `Input' is already defined
{standard input}:11658: Error: symbol `data' is already defined
{standard input}:11712: Error: symbol `signal' is already defined
make[2]: *** [/home/sethman/rt2570-cvs-2006041119/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/home/sethman/rt2570-cvs-2006041119/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
rt2570.ko failed to build!
make: *** [module] Error 1

```


Any suggestions/corrections you can give me about how to fix this or what  "/lib/modules/2.6.12-9-386/build" should really be (a folder with contents or a soft link) or what to look into next?

Thank you for any help,

mantrasu

---

