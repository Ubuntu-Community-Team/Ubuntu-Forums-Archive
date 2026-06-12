---
title: "How do you make a .deb file ?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2007-03-19
I'm wondering if it's possible to make a .deb file for someone which consists of a network card driver ? This is for bigbabydaddy, whom is trying to get his internet connection working, so obviously he can't compile the driver himself since essential-build isn't included by default. I've installed it myself, and was about to compile it when I figured that doing so might screw my own driver configuration. 

In lieu of this, I thought I might be able to make a .deb file for him, so that Ubuntu could just install the driver automagically. Is this possible, and if so, how do I go about doing it ? When I installed essential-build, I also saw .deb maker packages there, and installed those too. But I'd still like an essential list of things I'd need, and how to make the package, if it is indeed possible. 

For the record: [This is the driver in question](http://downloadfinder.intel.com/scripts-df-external/download.aspx?url=/9180/eng/e1000-7.4.27.tar.gz&DwnldId=9180&ProductID=839&lang=eng)

TIA. 

Doug

---

### Post by BigBabyDaddy1968 on 2007-03-19
If anything, this is becoming a nightmare install, but not for the usually posted reasons ("ubuntu/linux sux" or "why can't it just work?" etc.).  If anything, this whole experience has made me realize how lazy and complacent one could become, even after working with computers for 20 years, now.  I mean, FFS, I had never done anything beyond point-n-click before, so a dual-boot system was a major step forward for me (along w/ an XP crash/reinstall...repeated....).  

All help appreciated and all sarcastic comments taken in stride and good humor.

BBD

---

### Post by russell.h on 2007-03-20
```

sudo aptitude install checkinstall
./configure
make
sudo checkinstall -D --install=no

```
Should do it (I think).

---

### Post by Sweet Spot on 2007-03-20
Ok, so you're saying it can be done, which means I need certain installed packages..great. 

But is there something I have to do prior to those commands ? I'm assuming that I have to first cd to the directory where the driver is, right ? Can you or someone else be a little more concise with these instructions please ? This is the very first time I'm doing this. 

Thanks again.

doug

---

### Post by Sweet Spot on 2007-03-20
I decided (like a good ol' trusting fool ;) ) to go ahead and copy paste it anyway... Here are the results, which seem to have done nothing as far as I can see, but so far hasn't messed anything up either. What do I do now ?  Click thumbnail to enlarge please. 

[[IMG]http://img1.putfile.com/thumb/3/7810403889.jpg[/IMG]]("http://www.putfile.com/pic.php?img=5028645")

---

### Post by KenSentMe on 2007-03-20
Now you can unpack the source of the driver to a certain directory, go to that directory and do what russell.h said:

```

./configure
make
sudo checkinstall -D --install=no

```

---

### Post by Kobalt on 2007-03-20
.deb packages just grow out from sprouts and .rpm from roses ? Don't they ?
:) 
Seriously, building a .deb package can be done by the way russell.h described, but particularly in the case of building a driver package, you might want to do it with attention so that its reliable.
Here is some [doc and howto]("http://ubuntuforums.org/showthread.php?t=51003") you might find useful on building debian packages.

---

### Post by Sweet Spot on 2007-03-20
> **KenSentMe said:**
> Now you can unpack the source of the driver to a certain directory, go to that directory and do what russell.h said:

```

./configure
make
sudo checkinstall -D --install=no

```

I'm kind of confused now. What I did the first time was copy/paste the entire command list he gave me, the results of which I posted in the screen shot. And now I'm supposed to repeat a part of said command ? And how exactly do I go about unpacking the source of the driver ?Me=confused. Thanks

Doug

---

### Post by Efwis on 2007-03-20
find the source file that you downloaded. click on the tar.bz2 or tar.gz file, whichever one it is that you have. This will open file roller, this is a unpacking file that works the same way winzip does. click on extract, choose the location you want to unzip it too, I recommend creating a new directory so that all the files are in the same location, and not mixed in with files not related to the project.

next do the following:

```
cd /path/to/directory
``` 
So lets say I unzipped a program to /home/efwis/supercali I would do 
cd /home/efwis/supercali

next do this
```
./configure
make
sudo checkinstall -D --install=no
```
each line is performed after the first one is done. hit enter after each command.

Thats it, you should now have a working .deb

---

### Post by Sweet Spot on 2007-03-20
> **Kobalt said:**
> .deb packages just grow out from sprouts and .rpm from roses ? Don't they ?
:) 
Seriously, building a .deb package can be done by the way russell.h described, but particularly in the case of building a driver package, you might want to do it with attention so that its reliable.
Here is some [doc and howto]("http://ubuntuforums.org/showthread.php?t=51003") you might find useful on building debian packages.


LOL, wow. That seems like a much more shall we say " involved" way to go about making an actual .deb file ! So with all of that information, what exactly can I expect to have accomplished with the commands presented by russel/ken ?  I'd obviously hate to give someone a bum package, but it would also be fun to experiment and see if it worked the "easier way". (Yeah, that's me being lazy..but it's just that I go to school from Mon-Thurs and then work Fri-Sun so it's not like I have all the time in the world to do this stuff for anybody, though I'd like to really help BBD out)

Further explanations on the  former method (shorter) would really be appreciated. I've still got the terminal open from when I performed those commands.

---

### Post by Sweet Spot on 2007-03-20
> **Efwis said:**
> find the source file that you downloaded. click on the tar.bz2 or tar.gz file, whichever one it is that you have. This will open file roller, this is a unpacking file that works the same way winzip does. click on extract, choose the location you want to unzip it too, I recommend creating a new directory so that all the files are in the same location, and not mixed in with files not related to the project.

next do the following:

```
cd /path/to/directory
```So lets say I unzipped a program to /home/efwis/supercali I would do 
cd /home/efwis/supercali

next do this
```
./configure
make
sudo checkinstall -D --install=no
```each line is performed after the first one is done. hit enter after each command.

Thats it, you should now have a working .deb

Efwis:  I opened up a new terminal, typed "cd" then space, and then just dragged and dropped the "src" folder from the extracted driver folder in order to point to the location of the source files. I then did as you instructed, and got this:

[[IMG]http://img1.putfile.com/thumb/3/7811364682.jpg[/IMG]]("http://www.putfile.com/pic.php?img=5029191")

I must have missed something, right ?

---

### Post by KenSentMe on 2007-03-20
I think you should install the package build-essential first. That is a meta package containing several packages needed for compiling.

---

### Post by Sweet Spot on 2007-03-20
> **KenSentMe said:**
> I think you should install the package build-essential first. That is a meta package containing several packages needed for compiling.

Yeah, I actually installed that last night when I found out I didn't have it *(forgot how I realized I needed it though). I need a list of other components which are needed for compiling, as well as building the .deb file. I do however have the "Debian New Maintainer's Guide" bookmarked, and think that it lists the packages I need to build .deb's. If there's anything someone else can think of , please list it. This is all rather confusing for a noob such as myself. 

Must be off to school now, will be back later. Thanks all. 

Doug

---

### Post by Efwis on 2007-03-20
you didn't miss anything, this file doesn't have a configure file, I'm checking the process to see how to make this work.

---

### Post by Efwis on 2007-03-20
well at this point I don't know,

I attempted to do a process of making the file after using synaptic to retrieve the kernel source, and headers. System says it can't find the sources, even though it is right where it belongs. Go Figure.

anyway, at this time I am at a loss on how to do this using the shortcut method, I would recommend going with the longer version, at it appears that it may work better for this.

either way this won't necessarily be easy to do. especially if the makefile can't read the kernel source when it is in a directory it looks in to find them.

---

### Post by KenSentMe on 2007-03-20
Maybe a dumb question, but isn't the network card not detected and installed automaticly? What tye of card is it and does the command 'lspci' show your card?

---

### Post by Sweet Spot on 2007-03-20
It's not a dumb question at all, but it's not my card. This is for Bigbabydady1968. I'll refer you to :

[This post](http://ubuntuforums.org/showthread.php?t=384411)

It's hard to believe that it's this much trouble for Ubuntu to pick up his NIC or just install it. I was almost ready to tell him to buy a supported one, but based on principle, I'd like to get this licked before that.

---

### Post by russell.h on 2007-03-20
You don't want to be in the src directory when you run "./configure" , "make", and "checkinstall -D --install=no".

So open your Terminal then:
```

cd Desktop/e1000-7.2.47
<now press Enter>
./configure
<press Enter again>

```
At this point the configuration script will run. It may prompt you to install additional software packages. If it says "Can not find XYZ" open up synaptic and search for "XYZ". The package you want will probably be called "XYZ-dev" or "libXYZ-dev". Just make sure you get the one with the "-dev" suffix. You might want to keep a list of the packages you have to install.

After installing whatever package it wants run ./configure again. It may want more packages, in which case you install them, and run it yet again. And again. Keep on doing that until the ./configure runs fine with no errors.

Then:
```

make
<press enter>
sudo checkinstall -D --install=no
<press enter>

```

It will then ask you if you would like to create a default set of documents or somessuch. I typically just press Enter at each prompt until it finishes.

Now open up the e1000-7.2.47 folder on your desktop. In that folder you should find a .deb called something like e1000-7.2.47.deb.

The only thing I'm not sure about is how this will handle dependencies. You may have to install all of those "XYZ" packages (the ones without the -dev on the end, or maybe the ones with the -dev) on the machine that you eventually plan to use the driver on. Of course if you're lucky there won't be any dependencies, but that seems to be rare.

Good Luck!

Russell

---

### Post by Sweet Spot on 2007-03-20
Thanks Russel. Unfortunately, when I cd to the directory on my desktop (*as you've said, but obviously with my username..I just dragged and dropped the folder from my desktop to terminal to make sure it would be correct*)  I was still being told that the directory did not exist after I did './configure'   So really, I can't go on from there. Sorry. Being a novice w/this sucks.

---

### Post by BigBabyDaddy1968 on 2007-03-20
> **Sweet Spot said:**
> Sorry. Being a novice w/this sucks.
Wow...cuz I have barely understood a word, though I understand this is all great help....  It's actually somewhat frustrating (though not discouraging) to realize the extent of mine own n00bage.

As to the NIC card, it's not like this comp is some bottom-o'-the-heap bargain basement machine, although I didn't ask for any components to specifically be linux-friendly because it wasn't a need/desire at the time.  Still, one would think it would be a bit easier than all the effort so many are putting into my install.  

Again, many thanks to all trying to help.  But, if a relatively inexpensive card will get the job done....

---

### Post by russell.h on 2007-03-20
Open up that e1000 folder and see if there is some sort of readme or something. Some programs have weird scripts and stuff that they use to compile.

---

### Post by Efwis on 2007-03-20
just for giggles I would try actually typing the name rather than doing the drag and drop technique. That may be what the problem is.

so in Terminal just copy and paste this line or type it in

```

cd Desktop/e1000-7.2.47
```

---

### Post by Sweet Spot on 2007-03-20
> **russell.h said:**
> Open up that e1000 folder and see if there is some sort of readme or something. Some programs have weird scripts and stuff that they use to compile.

Haven't read through it all, and don't even know what to look for. It's a long read me, and will post it at the end of this post if anyone would like to sift through it. Thanks. 

> **Efwis said:**
> just for giggles I would try actually typing the name rather than doing the drag and drop technique. That may be what the problem is.

so in Terminal just copy and paste this line or type it in

```

cd Desktop/e1000-7.2.47
```

Tried it. didn't work. Thanks anyway. This has to be easier than it appears. 

Here's the readme: > Linux* Base Driver for the Intel(R) PRO/1000 Family of Adapters
===============================================================

December 5, 2006


Contents
========

- In This Release
- Identifying Your Adapter
- Building and Installation
- Command Line Parameters
- Speed and Duplex Configuration
- Additional Configurations
- Known Issues
- Support


In This Release
===============

This file describes the Linux* Base Driver for the Intel(R) PRO/1000 Family
of Adapters.  This driver supports kernel versions 2.4.x and 2.6.x.  This
driver includes support for Itanium(R)2-based systems.

This driver is only supported as a loadable module at this time.  Intel is
not supplying patches against the kernel source to allow for static linking
of the driver.  For questions related to hardware requirements, refer to the
documentation supplied with your Intel PRO/1000 adapter.  All hardware
requirements listed apply to use with Linux.

This release includes support for Intel(R) I/O Acceleration Technology,
Intel(R) I/OAT.  This is supported on systems using the Intel(R) 5000 Series
Chipsets Integrated Device - 1A38.  You can find additional information
on Intel I/OAT at [http://www.intel.com/technology/ioacceleration/index.htm](http://www.intel.com/technology/ioacceleration/index.htm).

The following features are now available in supported kernels:
 - Native VLANs
 - Channel Bonding (teaming)
 - SNMP

Channel Bonding documentation can be found in the Linux kernel source:
/Documentation/networking/bonding.txt

The driver information previously displayed in the /proc filesystem is not
supported in this release.  Alternatively, you can use ethtool (version 1.6
or later), lspci, and ifconfig to obtain the same information.

Instructions on updating ethtool can be found in the section "Additional
Configurations" later in this document.

NOTE: The Intel(R) 82562v 10/100 Network Connection only provides 10/100
support.


Identifying Your Adapter
========================

For more information on how to identify your adapter, go to the Adapter &
Driver ID Guide at:

    [http://support.intel.com/support/network/adapter/pro100/21397.htm](http://support.intel.com/support/network/adapter/pro100/21397.htm)

For the latest Intel network drivers for Linux, refer to the following
website.  In the search field, enter your adapter name or type, or use the
networking link on the left to search for your adapter:

    [http://downloadfinder.intel.com/scripts-df/support_intel.asp](http://downloadfinder.intel.com/scripts-df/support_intel.asp)


Building and Installation
=========================

To build a binary RPM* package of this driver, run 'rpmbuild -tb
<filename.tar.gz>'.  Replace <filename.tar.gz> with the specific filename
of the driver.

NOTE: For the build to work properly, the currently running kernel MUST
      match the version and configuration of the installed kernel sources.
      If you have just recompiled the kernel reboot the system now.

      RPM functionality has only been tested in Red Hat distributions.

1. Move the base driver tar file to the directory of your choice.  For
   example, use /home/username/e1000 or /usr/local/src/e1000.

2. Untar/unzip archive:

     tar zxf e1000-x.x.x.tar.gz

3. Change to the driver src directory:

     cd e1000-x.x.x/src/

4. Compile the driver module:

     make install

   The binary will be installed as:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.[k]o

   The install locations listed above are the default locations.  They
   might not be correct for certain Linux distributions.  For more
   information, see the ldistrib.txt file included in the driver tar.

5. Load the module using either the insmod or modprobe command:

     modprobe e1000

     insmod e1000

   Note that for 2.6 kernels the insmod command can be used if the full
   path to the driver module is specified.  For example:

     insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.ko

   With 2.6 based kernels also make sure that older e1000 drivers are 
   removed from the kernel, before loading the new module:

     rmmod e1000; modprobe e1000


6. Assign an IP address to the interface by entering the following, where
   x is the interface number:

     ifconfig ethx <IP_address>

7. Verify that the interface works.  Enter the following, where <IP_address>
   is the IP address for another machine on the same subnet as the
   interface that is being tested:

     ping  <IP_address>    


Command Line Parameters
=======================

If the driver is built as a module, the  following optional parameters
are used by entering them on the command line with the modprobe command
using this syntax:

     modprobe e1000 [<option>=<VAL1>,<VAL2>,...]

For example, with two PRO/1000 PCI adapters, entering:

     modprobe e1000 TxDescriptors=80,128

loads the e1000 driver with 80 TX descriptors for the first adapter and
128 TX descriptors for the second adapter.

The default value for each parameter is generally the recommended setting,
unless otherwise noted.

NOTES:  For more information about the AutoNeg, Duplex, and Speed
        parameters, see the "Speed and Duplex Configuration" section in
        this document.

        For more information about the InterruptThrottleRate,
        RxIntDelay, TxIntDelay, RxAbsIntDelay, and TxAbsIntDelay
        parameters, see the application note at:
        [http://www.intel.com/design/network/applnots/ap450.htm](http://www.intel.com/design/network/applnots/ap450.htm)

        A descriptor describes a data buffer and attributes related to
        the data buffer.  This information is accessed by the hardware.


AutoNeg
-------
(Supported only on adapters with copper connections)
Valid Range:   0x01-0x0F, 0x20-0x2F
Default Value: 0x2F

This parameter is a bit-mask that specifies the speed and duplex settings
advertised by the adapter.  When this parameter is used, the Speed and
Duplex parameters must not be specified.

NOTE:  Refer to the Speed and Duplex section of this readme for more
       information on the AutoNeg parameter.


Duplex
------
(Supported only on adapters with copper connections)
Valid Range:   0-2 (0=auto-negotiate, 1=half, 2=full)
Default Value: 0

This defines the direction in which data is allowed to flow.  Can be
either one or two-directional.  If both Duplex and the link partner are
set to auto-negotiate, the board auto-detects the correct duplex.  If the
link partner is forced (either full or half), Duplex defaults to half-
duplex.


FlowControl
-----------
Valid Range:   0-3 (0=none, 1=Rx only, 2=Tx only, 3=Rx&Tx)
Default Value: Reads flow control settings from the EEPROM

This parameter controls the automatic generation(Tx) and response(Rx)
to Ethernet PAUSE frames.


InterruptThrottleRate
---------------------
(not supported on Intel(R) 82542, 82543 or 82544-based adapters)
Valid Range:   0,1,3,100-100000 (0=off, 1=dynamic, 3=dynamic conservative)
Default Value: 3

The driver can limit the amount of interrupts per second that the adapter
will generate for incoming packets. It does this by writing a value to the 
adapter that is based on the maximum amount of interrupts that the adapter 
will generate per second.

Setting InterruptThrottleRate to a value greater or equal to 100
will program the adapter to send out a maximum of that many interrupts
per second, even if more packets have come in. This reduces interrupt
load on the system and can lower CPU utilization under heavy load,
but will increase latency as packets are not processed as quickly.

The default behaviour of the driver previously assumed a static 
InterruptThrottleRate value of 8000, providing a good fallback value for 
all traffic types,but lacking in small packet performance and latency. 
The hardware can handle many more small packets per second however, and 
for this reason an adaptive interrupt moderation algorithm was implemented.

Since 7.3.x, the driver has two adaptive modes (setting 1 or 3) in which
it dynamically adjusts the InterruptThrottleRate value based on the traffic 
that it receives. After determining the type of incoming traffic in the last
timeframe, it will adjust the InterruptThrottleRate to an appropriate value 
for that traffic.

The algorithm classifies the incoming traffic every interval into
classes.  Once the class is determined, the InterruptThrottleRate value is 
adjusted to suit that traffic type the best. There are three classes defined: 
"Bulk traffic", for large amounts of packets of normal size; "Low latency",
for small amounts of traffic and/or a significant percentage of small
packets; and "Lowest latency", for almost completely small packets or 
minimal traffic.

In dynamic conservative mode, the InterruptThrottleRate value is set to 4000 
for traffic that falls in class "Bulk traffic". If traffic falls in the "Low 
latency" or "Lowest latency" class, the InterruptThrottleRate is increased 
stepwise to 20000. This default mode is suitable for most applications.

For situations where low latency is vital such as cluster or
grid computing, the algorithm can reduce latency even more when
InterruptThrottleRate is set to mode 1. In this mode, which operates
the same as mode 3, the InterruptThrottleRate will be increased stepwise to 
70000 for traffic in class "Lowest latency".

Setting InterruptThrottleRate to 0 turns off any interrupt moderation
and may improve small packet latency, but is generally not suitable
for bulk throughput traffic.

NOTE:  InterruptThrottleRate takes precedence over the TxAbsIntDelay and
       RxAbsIntDelay parameters.  In other words, minimizing the receive
       and/or transmit absolute delays does not force the controller to
       generate more interrupts than what the Interrupt Throttle Rate
       allows.

CAUTION:  If you are using the Intel(R) PRO/1000 CT Network Connection
          (controller 82547), setting InterruptThrottleRate to a value
          greater than 75,000, may hang (stop transmitting) adapters
          under certain network conditions.  If this occurs a NETDEV
          WATCHDOG message is logged in the system event log.  In
          addition, the controller is automatically reset, restoring
          the network connection.  To eliminate the potential for the
          hang, ensure that InterruptThrottleRate is set no greater
          than 75,000 and is not set to 0.

NOTE:  When e1000 is loaded with default settings and multiple adapters
       are in use simultaneously, the CPU utilization may increase non-
       linearly.  In order to limit the CPU utilization without impacting
       the overall throughput, we recommend that you load the driver as
       follows:

           modprobe e1000 InterruptThrottleRate=3000,3000,3000

       This sets the InterruptThrottleRate to 3000 interrupts/sec for
       the first, second, and third instances of the driver.  The range
       of 2000 to 3000 interrupts per second works on a majority of
       systems and is a good starting point, but the optimal value will
       be platform-specific.  If CPU utilization is not a concern, use
       RX_POLLING (NAPI) and default driver settings.



RxDescriptors
-------------
Valid Range:   80-256 for 82542 and 82543-based adapters
               80-4096 for all other supported adapters
Default Value: 256

This value specifies the number of receive buffer descriptors allocated
by the driver.  Increasing this value allows the driver to buffer more
incoming packets, at the expense of increased system memory utilization.

Each descriptor is 16 bytes.  A receive buffer is also allocated for each
descriptor and can be either 2048, 4096, 8192, or 16384 bytes, depending 
on the MTU setting. The maximum MTU size is 16110.

NOTE:  MTU designates the frame size.  It only needs to be set for Jumbo 
       Frames.  Depending on the available system resources, the request 
       for a higher number of receive descriptors may be denied.  In this 
       case, use a lower number.


RxIntDelay
----------
Valid Range:   0-65535 (0=off)
Default Value: 0

This value delays the generation of receive interrupts in units of 1.024
microseconds.  Receive interrupt reduction can improve CPU efficiency if
properly tuned for specific network traffic.  Increasing this value adds
extra latency to frame reception and can end up decreasing the throughput
of TCP traffic.  If the system is reporting dropped receives, this value
may be set too high, causing the driver to run out of available receive
descriptors.

CAUTION:  When setting RxIntDelay to a value other than 0, adapters may
          hang (stop transmitting) under certain network conditions.  If
          this occurs a NETDEV WATCHDOG message is logged in the system
          event log.  In addition, the controller is automatically reset,
          restoring the network connection.  To eliminate the potential
          for the hang ensure that RxIntDelay is set to 0.


RxAbsIntDelay
-------------
(This parameter is supported only on 82540, 82545 and later adapters.)
Valid Range:   0-65535 (0=off)
Default Value: 128

This value, in units of 1.024 microseconds, limits the delay in which a
receive interrupt is generated.  Useful only if RxIntDelay is non-zero,
this value ensures that an interrupt is generated after the initial
packet is received within the set amount of time.  Proper tuning,
along with RxIntDelay, may improve traffic throughput in specific network
conditions.


Speed
-----
(This parameter is supported only on adapters with copper connections.)
Valid Settings: 0, 10, 100, 1000
Default Value:  0 (auto-negotiate at all supported speeds)

Speed forces the line speed to the specified value in megabits per second
(Mbps).  If this parameter is not specified or is set to 0 and the link
partner is set to auto-negotiate, the board will auto-detect the correct
speed.  Duplex should also be set when Speed is set to either 10 or 100.


TxDescriptors
-------------
Valid Range:   80-256 for 82542 and 82543-based adapters
               80-4096 for all other supported adapters
Default Value: 256

This value is the number of transmit descriptors allocated by the driver.
Increasing this value allows the driver to queue more transmits.  Each
descriptor is 16 bytes.

NOTE:  Depending on the available system resources, the request for a
       higher number of transmit descriptors may be denied.  In this case,
       use a lower number.


TxIntDelay
----------
Valid Range:   0-65535 (0=off)
Default Value: 64

This value delays the generation of transmit interrupts in units of
1.024 microseconds.  Transmit interrupt reduction can improve CPU
efficiency if properly tuned for specific network traffic.  If the
system is reporting dropped transmits, this value may be set too high
causing the driver to run out of available transmit descriptors.


TxAbsIntDelay
-------------
(This parameter is supported only on 82540, 82545 and later adapters.)
Valid Range:   0-65535 (0=off)
Default Value: 64

This value, in units of 1.024 microseconds, limits the delay in which a
transmit interrupt is generated.  Useful only if TxIntDelay is non-zero,
this value ensures that an interrupt is generated after the initial
packet is sent on the wire within the set amount of time.  Proper tuning,
along with TxIntDelay, may improve traffic throughput in specific
network conditions.

XsumRX
------
(This parameter is NOT supported on the 82542-based adapter.)
Valid Range:   0-1
Default Value: 1

A value of '1' indicates that the driver should enable IP checksum
offload for received packets (both UDP and TCP) to the adapter hardware.

Copybreak
---------
Valid Range:   0-xxxxxxx (0=off)
Default Value: 256
Usage: insmod e1000.ko copybreak=128

Driver copies all packets below or equaling this size to a fresh rx
buffer before handing it up the stack.

This parameter is different than other parameters, in that it is a
single (not 1,1,1 etc.) parameter applied to all driver instances and
it is also available during runtime at 
/sys/module/e1000/parameters/copybreak


Speed and Duplex Configuration
==============================

Three keywords are used to control the speed and duplex configuration.
These keywords are Speed, Duplex, and AutoNeg.

If the board uses a fiber interface, these keywords are ignored, and the
fiber interface board only links at 1000 Mbps full-duplex.

For copper-based boards, the keywords interact as follows:

  The default operation is auto-negotiate.  The board advertises all
  supported speed and duplex combinations, and it links at the highest
  common speed and duplex mode IF the link partner is set to auto-negotiate.

  If Speed = 1000, limited auto-negotiation is enabled and only 1000 Mbps
  is advertised (The 1000BaseT spec requires auto-negotiation.)

  If Speed = 10 or 100, then both Speed and Duplex should be set.  Auto-
  negotiation is disabled, and the AutoNeg parameter is ignored.  Partner
  SHOULD also be forced.

The AutoNeg parameter is used when more control is required over the
auto-negotiation process.  It should be used when you wish to control which
speed and duplex combinations are advertised during the auto-negotiation
process.

The parameter may be specified as either a decimal or hexadecimal value as
determined by the bitmap below.

Bit position   7      6      5       4       3      2      1       0
Decimal Value  128    64     32      16      8      4      2       1
Hex value      80     40     20      10      8      4      2       1
Speed (Mbps)   N/A    N/A    1000    N/A     100    100    10      10
Duplex                       Full            Full   Half   Full    Half

Some examples of using AutoNeg:

  modprobe e1000 AutoNeg=0x01 (Restricts autonegotiation to 10 Half)
  modprobe e1000 AutoNeg=1 (Same as above)
  modprobe e1000 AutoNeg=0x02 (Restricts autonegotiation to 10 Full)
  modprobe e1000 AutoNeg=0x03 (Restricts autonegotiation to 10 Half or 10 Full)
  modprobe e1000 AutoNeg=0x04 (Restricts autonegotiation to 100 Half)
  modprobe e1000 AutoNeg=0x05 (Restricts autonegotiation to 10 Half or 100
  Half)
  modprobe e1000 AutoNeg=0x020 (Restricts autonegotiation to 1000 Full)
  modprobe e1000 AutoNeg=32 (Same as above)

Note that when this parameter is used, Speed and Duplex must not be specified.

If the link partner is forced to a specific speed and duplex, then this
parameter should not be used.  Instead, use the Speed and Duplex parameters
previously mentioned to force the adapter to the same speed and duplex.


Additional Configurations
=========================

  Configuring the Driver on Different Distributions
  -------------------------------------------------
  Configuring a network driver to load properly when the system is started
  is distribution dependent.  Typically, the configuration process involves
  adding an alias line to /etc/modules.conf or /etc/modprobe.conf as well
  as editing other system startup scripts and/or configuration files.  Many
  popular Linux distributions ship with tools to make these changes for you.
  To learn the proper way to configure a network device for your system,
  refer to your distribution documentation.  If during this process you are
  asked for the driver or module name, the name for the Linux Base Driver
  for the Intel(R) PRO/1000 Family of Adapters is e1000.

  As an example, if you install the e1000 driver for two PRO/1000 adapters
  (eth0 and eth1) and set the speed and duplex to 10full and 100half, add
  the following to modules.conf or or modprobe.conf:

       alias eth0 e1000
       alias eth1 e1000
       options e1000 Speed=10,100 Duplex=2,1

  Viewing Link Messages
  ---------------------
  Link messages will not be displayed to the console if the distribution is
  restricting system messages.  In order to see network driver link messages
  on your console, set dmesg to eight by entering the following:

       dmesg -n 8

  NOTE: This setting is not saved across reboots.

  Jumbo Frames
  ------------
  Jumbo Frames support is enabled by changing the MTU to a value larger than
  the default of 1500.  Use the ifconfig command to increase the MTU size.
  For example:

       ifconfig eth<x> mtu 9000 up

  This setting is not saved across reboots.  It can be made permanent if
  you add:

       MTU=9000

   to the file /etc/sysconfig/network-scripts/ifcfg-eth<x>.  This example
   applies to the Red Hat distributions; other distributions may store this
   setting in a different location.

  Notes:

  - To enable Jumbo Frames, increase the MTU size on the interface beyond
    1500.

  - The maximum MTU setting for Jumbo Frames is 16110.  This value coincides
    with the maximum Jumbo Frames size of 16128.

  - Using Jumbo Frames at 10 or 100 Mbps may result in poor performance or
    loss of link.

  - Some Intel gigabit adapters that support Jumbo Frames have a frame size
    limit of 9238 bytes, with a corresponding MTU size limit of 9216 bytes.
    The adapters with this limitation are based on the Intel(R) 82571EB,
    82572EI, 82573L and 80003ES2LAN controller.  These correspond to the
    following product names:
     Intel(R) PRO/1000 PT Server Adapter
     Intel(R) PRO/1000 PT Desktop Adapter
     Intel(R) PRO/1000 PT Network Connection
     Intel(R) PRO/1000 PT Dual Port Server Adapter
     Intel(R) PRO/1000 PT Dual Port Network Connection
     Intel(R) PRO/1000 PF Server Adapter
     Intel(R) PRO/1000 PF Network Connection
     Intel(R) PRO/1000 PF Dual Port Server Adapter
     Intel(R) PRO/1000 PB Server Connection
     Intel(R) PRO/1000 PL Network Connection
     Intel(R) PRO/1000 EB Network Connection with I/O Acceleration
     Intel(R) PRO/1000 EB Backplane Connection with I/O Acceleration
     Intel(R) PRO/1000 PT Quad Port Server Adapter
     Intel(R) PRO/1000 PF Quad Port Server Adapter

  - Adapters based on the Intel(R) 82542 and 82573V/E controller do not
    support Jumbo Frames. These correspond to the following product names:
     Intel(R) PRO/1000 Gigabit Server Adapter
     Intel(R) PRO/1000 PM Network Connection

  - The following adapters do not support Jumbo Frames:
     Intel(R) 82562V 10/100 Network Connection
     Intel(R) 82566DM Gigabit Network Connection
     Intel(R) 82566DC Gigabit Network Connection
     Intel(R) 82566MM Gigabit Network Connection
     Intel(R) 82566MC Gigabit Network Connection
     Intel(R) 82562GT 10/100 Network Connection
     Intel(R) 82562G 10/100 Network Connection


  Ethtool
  -------
  The driver utilizes the ethtool interface for driver configuration and
  diagnostics, as well as displaying statistical information.  Ethtool
  version 1.6 or later is required for this functionality.

  The latest release of ethtool can be found from
  [http://sourceforge.net/projects/gkernel](http://sourceforge.net/projects/gkernel).

  NOTE: Ethtool 1.6 only supports a limited set of ethtool options.  Support
  for a more complete ethtool feature set can be enabled by upgrading
  to the latest version.

  Enabling Wake on LAN* (WoL)
  ---------------------------
  WoL is configured through the Ethtool* utility.  Ethtool is included with
  all versions of Red Hat after Red Hat 7.2.  For other Linux distributions,
  download and install Ethtool from the following website:
  [http://sourceforge.net/projects/gkernel](http://sourceforge.net/projects/gkernel).

  For instructions on enabling WoL with Ethtool, refer to the website listed
  above.

  WoL will be enabled on the system during the next shut down or reboot.
  For this driver version, in order to enable WoL, the e1000 driver must be
  loaded when shutting down or rebooting the system.

  Wake On LAN is only supported on port A for the following devices:
  Intel(R) PRO/1000 PT Dual Port Network Connection
  Intel(R) PRO/1000 PT Dual Port Server Connection
  Intel(R) PRO/1000 PT Dual Port Server Adapter
  Intel(R) PRO/1000 PF Dual Port Server Adapter
  Intel(R) PRO/1000 PT Quad Port Server Adapter 

  NAPI
  ----
  NAPI (Rx polling mode) is supported in the e1000 driver.  NAPI is enabled
  or disabled based on the configuration of the kernel.  To override
  the default, use the following compile-time flags.

  To enable NAPI, compile the driver module, passing in a configuration option:

       make CFLAGS_EXTRA=-DE1000_NAPI install

  To disable NAPI, compile the driver module, passing in a configuration option:

       make CFLAGS_EXTRA=-DE1000_NO_NAPI install

  See [www.cyberus.ca/~hadi/usenix-paper.tgz](www.cyberus.ca/~hadi/usenix-paper.tgz) for more information on NAPI.


Known Issues
============

NOTE: For distribution-specific information, see the ldistrib.txt file
      included in the driver tar.

Detected Tx Unit Hang in Quad Port Adapters
-------------------------------------------
In some cases ports 3 and 4 don't pass traffic and report 'Detected Tx Unit
Hang' followed by 'NETDEV WATCHDOG: ethX: transmit timed out' errors. Ports 
1 and 2 don't show any errors and will pass traffic.

This issue MAY be resolved by updating to the latest kernel and BIOS. The 
user is encouraged to run an OS that fully supports MSI interrupts. You can 
check your system's BIOS by downloading the Linux Firmware Developer Kit 
that can be obtained at [http://www.linuxfirmwarekit.org/](http://www.linuxfirmwarekit.org/)

82573(V/L/E) TX Unit Hang Messages
----------------------------------
Several adapters with the 82573 chipset display "TX unit hang" messages 
during normal operation with the e1000 driver. The issue appears both with 
TSO enabled and disabled, and is caused by a power management function that 
is enabled in the EEPROM. Early releases of the chipsets to vendors had the 
EEPROM bit that enabled the feature. After the issue was discovered newer 
adapters were released with the feature disabled in the EEPROM. 

If you encounter the problem in an adapter, and the chipset is an 82573-based
one, you can verify that your adapter needs the fix by using ethtool: 

 # ethtool -e eth0
 Offset          Values
 ------          ------
 0x0000          00 12 34 56 fe dc 30 0d 46 f7 f4 00 ff ff ff ff
 0x0010          ff ff ff ff 6b 02 8c 10 d9 15 8c 10 86 80 de 83
                                                           ^^
The value at offset 0x001e (de) has bit 0 unset. This enables the problematic 
power saving feature. In this case, the EEPROM needs to read "df" at offset 
0x001e. 

A one-time EEPROM fix is available as a shell script. This script will verify 
that the adapter is applicable to the fix and if the fix is needed or not. If 
the fix is required, it applies the change to the EEPROM and updates the 
checksum. The user must reboot the system after applying the fix if changes 
were made to the EEPROM. 

Example output of the script: 

 # bash fixeep-82573-dspd.sh eth0
 eth0: is a "82573E Gigabit Ethernet Controller"
 This fixup is applicable to your hardware
 executing command: ethtool -E eth0 magic 0x109a8086 offset 0x1e value 0xdf
 Change made. You *MUST* reboot your machine before changes take effect!

The script can be downloaded at 
[http://e1000.sourceforge.net/files/fixeep-82573-dspd.sh](http://e1000.sourceforge.net/files/fixeep-82573-dspd.sh)

Dropped Receive Packets on Half-duplex 10/100 Networks
------------------------------------------------------
If you have an Intel PCI Express adapter running at 10mbps or 100mbps, half-
duplex, you may observe occasional dropped receive packets.  There are no
workarounds for this problem in this network configuration.  The network must
be updated to operate in full-duplex, and/or 1000mbps only.

Driver Compilation
------------------
When trying to compile the driver by running make install, the following
error may occur:

    "Linux kernel source not configured - missing version.h"

To solve this issue, create the version.h file by going to the Linux source
tree and entering:

    make include/linux/version.h.

Jumbo Frames System Requirement
-------------------------------
Memory allocation failures have been observed on Linux systems with 64 MB
of RAM or less that are running Jumbo Frames.  If you are using Jumbo
Frames, your system may require more than the advertised minimum
requirement of 64 MB of system memory.

Performance Degradation with Jumbo Frames
-----------------------------------------
Degradation in throughput performance may be observed in some Jumbo frames
environments.  If this is observed, increasing the application's socket
buffer size and/or increasing the /proc/sys/net/ipv4/tcp_*mem entry values
may help.  See the specific application manual and
/usr/src/linux*/Documentation/
networking/ip-sysctl.txt for more details.

Jumbo Frames on Foundry BigIron 8000 switch
-------------------------------------------
There is a known issue using Jumbo frames when connected to a Foundry
BigIron 8000 switch.  This is a 3rd party limitation.  If you experience
loss of packets, lower the MTU size.

Allocating Rx Buffers when Using Jumbo Frames 
---------------------------------------------
Allocating Rx buffers when using Jumbo Frames on 2.6.x kernels may fail if 
the available memory is heavily fragmented. This issue may be seen with PCI-X 
adapters or with packet split disabled. This can be reduced or eliminated 
by changing the amount of available memory for receive buffer allocation, by
increasing /proc/sys/vm/min_free_kbytes. 

Multiple Interfaces on Same Ethernet Broadcast Network
------------------------------------------------------
Due to the default ARP behavior on Linux, it is not possible to have
one system on two IP networks in the same Ethernet broadcast domain
(non-partitioned switch) behave as expected.  All Ethernet interfaces
will respond to IP traffic for any IP address assigned to the system.
This results in unbalanced receive traffic.

If you have multiple interfaces in a server, either turn on ARP
filtering by entering:

    echo 1 > /proc/sys/net/ipv4/conf/all/arp_filter
(this only works if your kernel's version is higher than 2.4.5),

NOTE: This setting is not saved across reboots.  The configuration
change can be made permanent by adding the line:
    net.ipv4.conf.all.arp_filter = 1
to the file /etc/sysctl.conf

      or,

install the interfaces in separate broadcast domains (either in
different switches or in a switch partitioned to VLANs).

82541/82547 can't link or are slow to link with some link partners
-----------------------------------------------------------------
There is a known compatibility issue with 82541/82547 and some
low-end switches where the link will not be established, or will
be slow to establish.  In particular, these switches are known to
be incompatible with 82541/82547:

    Planex FXG-08TE
    I-O Data ETG-SH8

To workaround this issue, the driver can be compiled with an override
of the PHY's master/slave setting.  Forcing master or forcing slave
mode will improve time-to-link.

    # make CFLAGS_EXTRA=-DE1000_MASTER_SLAVE=<n>

Where <n> is:

    0 = Hardware default
    1 = Master mode
    2 = Slave mode
    3 = Auto master/slave

Disable rx flow control with ethtool
------------------------------------
In order to disable receive flow control using ethtool, you must turn
off auto-negotiation on the same command line.

For example:

   ethtool -A eth? autoneg off rx off

Unplugging network cable while ethtool -p is running
----------------------------------------------------
In kernel versions 2.5.50 and later (including 2.6 kernel), unplugging 
the network cable while ethtool -p is running will cause the system to 
become unresponsive to keyboard commands, except for control-alt-delete.  
Restarting the system appears to be the only remedy.



Support
=======

For general information, go to the Intel support website at:

    [http://support.intel.com](http://support.intel.com)

or the Intel Wired Networking project hosted by Sourceforge at:

    [http://sourceforge.net/projects/e1000](http://sourceforge.net/projects/e1000)

If an issue is identified with the released source code on the supported
kernel with a supported adapter, email the specific information related
to the issue to [email]e1000-devel@lists.sf.net[/email]






---

### Post by russell.h on 2007-03-21
Oh, ok this is easier than I could have imagined.

Open your terminal and type in:
```

cd Desktop/e1000-7.2.47
<press Enter>
sudo checkinstall -D --install=no
<press Enter>
<If this doesn't work see below*>

```
Now whenever it pops something up just press enter until it finishes. Look in the e1000 folder and you should find your .deb.... hopefully.

Judging by the readme the driver is already compiled, all you have to do is install it.

*If the above doesn't work try running ```
make
``` before checkinstall (I just compiled a program that came preconfigured somehow, but which I still had to compile).

---

### Post by Sweet Spot on 2007-03-21
> **russell.h said:**
> Oh, ok this is easier than I could have imagined.

Open your terminal and type in:
```

cd Desktop/e1000-7.2.47
<press Enter>
sudo checkinstall -D --install=no
<press Enter>
<If this doesn't work see below*>

```Now whenever it pops something up just press enter until it finishes. Look in the e1000 folder and you should find your .deb.... hopefully.

Judging by the readme the driver is already compiled, all you have to do is install it.

*If the above doesn't work try running ```
make
``` before checkinstall (I just compiled a program that came preconfigured somehow, but which I still had to compile).

Damn dude ! It seems like I'm SO close , yet so far away... I did what you said in the first method, but it didn't work: 
[[img]http://img1.putfile.com/thumb/3/7910530489.jpg[/img]](http://www.putfile.com/pic.php?img=5036011)

And then afterwards, I plugged in the desktop location again, and typed 'make' but that didn't yield any results either, unless I did something wrong ?:


Thanks so much for your help on this. It's truly appreciated. I'm having bad dreams about going the long way in making the .deb file (which I'll have to do one day anyway I'm sure). So, what do you think about the last thing I did ? Did I skip something ? It says there was no target. 

[[img]http://img1.putfile.com/thumb/3/7910530482.jpg[/img]](http://www.putfile.com/pic.php?img=5036012)

Doug

---

### Post by russell.h on 2007-03-21
Oh, crap, my bad, didn't read the instructions properly. You need to cd into the /src directory before running checkinstall. So it would be
```
cd Desktop/e1000-7.2.47/src
<press Enter>
sudo checkinstall -D --install=no
<press Enter>

```
I think.... Its hard to believe that it actually might work :) 

When you go to install the .deb you will have to do more than just install it before it will work. Read the readme, you have to do some sort of modprobe crap that I don't know anything about.

---

### Post by Sweet Spot on 2007-03-21
Please, I don't find it so hard to believe at all... I find it impossible to believe, since it still doesn't work. DOH! > The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

*** No known documentation files were found. The new package
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>>

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ root@****-desktop ]
1 -  Summary: [ Package created with checkinstall 1.6.0 ]
2 -  Name:    [ src ]
3 -  Version: [ 20070321 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ src ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Makefile:71: *** Linux kernel source not found.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

****@******-desktop:~/Desktop/e1000-7.4.27/src$




*heavy sigh*

Have to leave for school now, But seriously, thanks for keeping up with the trying for us. 

doug

(FYI, I DO keep on dragging and dropping the directory into the terminal, which was suggested I don't do. But it still does yield those progressions)

---

### Post by Sweet Spot on 2007-03-21
Russell, do you think it would be too much of me to ask you to try this method with said driver, as I have school now, and have a project due for tomorrow ? I'm sure I'll be back to look and try again, but wonder if that's still too much to ask of you. Believe me, I feel like a heel asking, but would really love to know if it's just that I'm doing something wrong, something simple perhaps. And since you've already given me so many leads, it probably would take you the same amount of time as it has just typing the code for me.

I will of course understand if you can't for whatever reasons. Just figured that at this point it couldn't help to ask. 

Doug

---

### Post by russell.h on 2007-03-21
Yeah. I just downloaded and tried to build the driver, but I got some weird architecture related error (I'm running 64 bit Feisty though, so no huge surprise).

However it was certainly working for a minute there, and I suspect it would work on a 32 bit installation. It seems as though I was wrong, it *does* have to compile it.

For that you will want to make sure you have the package "build-essentials" installed. Also make sure you have "linux-headers-<your_kernel_version_here>" installed.

Then, when you run checkinstall and it gets to this part:
```
*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@russell-desktop ]
1 -  Summary: [ Package created with checkinstall 1.6.0 ]
2 -  Name:    [ src ]
3 -  Version: [ 20070321 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ src ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

```
I would recommend changing the "version" to 7.2.47 just so its easier to keep track. Also note that because this is a kernel module any kernel updates might break it, forcing you to reinstall (oh, if you are compiling it for someone else make sure that they have the same kernel version as you).

This is getting kind of complicated.... but I think that it will work..... :confused:

---

### Post by Sweet Spot on 2007-03-21
Good stuff Russell, if anything this is an incredibly educational experience for me, and hopefully BBD as well as some other people that are interested in this topic. I'll give it one look over tonight, but can't spend too much time since I have to get a speech ready for tomorrows class. 

Thank you so much for spending your time trying to help us in these matters, it's really great of you. 

Regards, 
Doug

P.S. I'll of course keep you/others updated should this all work out or not.

---

### Post by Sweet Spot on 2007-03-21
Hell. I just realized something, which I guess you overlooked as well. You said that we'd need the same Kernel right ?  .... ... ...... ..... ](*,)

Not possible since he hasn't been able to update anything !!! LOL. 

I think this whole thing may have hit a huge brick wall sir. What to do, what to do........

Edit: hopefully One of the Kernel options in grub will match his current one. Will that work ? Otherwise, will I be able to roll back to his Kernel if I wanted to ?

---

### Post by BigBabyDaddy1968 on 2007-03-21
If that's the case, could I not just burn a new iso and reinstall?

And again, if I may grovel at the feet of those helping.... :D

BTW, does anyone remember such a difficult install?

---

### Post by russell.h on 2007-03-22
If nothing else you can probably find whatever kernel he has in the repositories.... But really, I have very little idea how all this stuff works, I'm not even sure if he will need the same kernel version or what. I'm not even sure if its possible to install it on a different computer than it was compiled on (although I would assume it is).

Probably the easiest way to do this would be to download the various required packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) (although I've never tried downloading a meta-package like build-essential), burn them to a cd, then install them on his computer. Then compile the driver right on his computer.

Seriously though, this is getting *way* out of my (very limited) area of knowledge. The thing I find hard to believe is that Ubuntu doesn't have a driver for his card by default. You should... contact someone or something :confused:

---

### Post by BigBabyDaddy1968 on 2007-03-22
> **russell.h said:**
> Seriously though, this is getting *way* out of my (very limited) area of knowledge. The thing I find hard to believe is that Ubuntu doesn't have a driver for his card by default. You should... contact someone or something :confused:
Ah, yes...but who?  I did speak to a couple of Dell tech support people (very proficient at walking me through my very first BSOD experience...and the second one as well.... :D) who seemed somewhat knowledgeable about dual boots and Linux, but don't know if they could help out "officially."

---

### Post by Sweet Spot on 2007-03-22
Good idea about taking it up with someone w/more experience. What if it turns out that we're doing this for nothing. I'd love to get an opinion and help from one of the devs or a guru etc.. I also find it hard to believe that Ubuntu hasn't picked up his card or doesn't have a more simple means of doing this. 

Whom should we ask, and where should we ask ?

---

### Post by BigBabyDaddy1968 on 2007-03-22
Also, is it possible that Ubuntu just won't work on my comp as it's configured?  Perhaps another distro?  Would Kubuntu/Xubuntu/Edubuntu possibly be more likely to work?

---

### Post by Sweet Spot on 2007-03-22
Ok, so unless anyone has a really good suggestion about either what to do at this point, or can direct us to a better source of information *a more seasoned pro for help perhaps*,  I now have to offer, this information if it's prudent :  BBD's kernel is 2.6.15.26(386) 

and the ones I have loaded are "  " ".23 / " " ".27/ and " " ".28 respectively. (386 also)  With that said, will we still have to have the same exact kernels, or are one of mine close enough, such as my 27th ?  

Doug

---

### Post by cowlip on 2007-03-23
Perhaps [https://answers.launchpad.net/](https://answers.launchpad.net/) could help?  Maybe aptoncd (it looks like it packages...packages): [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by esaym on 2007-03-23
I am no master but the e1000 drivers are included on ubuntu by default:

user@user-desktop:~$ slocate e1000
/lib/modules/2.6.15-26-386/kernel/drivers/net/e1000
/lib/modules/2.6.15-26-386/kernel/drivers/net/e1000/e1000.ko
/lib/modules/2.6.15-28-386/kernel/drivers/net/e1000
/lib/modules/2.6.15-28-386/kernel/drivers/net/e1000/e1000.ko
/lib/modules/2.6.15-27-386/kernel/drivers/net/e1000
/lib/modules/2.6.15-27-386/kernel/drivers/net/e1000/e1000.ko

Perhaps it is a new revision of the nic card so the default installer does not load the module.  Might have to load it manually.  Try ```
modprobe e1000
``` then ```
ifconfig eth0 up
```  

This will show you what modules are loaded:
```
lsmod
``` 

If e1000 is the correct driver for your card and it is not automatically loading you should be able to force it.  Sorry it is late and I can not look up the how to.  It is basic linux stuff though.  I really don't know how module loading is handled in ubuntu.  But on simpler distros it has to do with editing /etc/modules.conf and adding a line like ```
alias eth0 e1000
```  Does that ring a bell to anyone?

Also look at the last post here: [http://ubuntuforums.org/showthread.php?t=276126](http://ubuntuforums.org/showthread.php?t=276126)  Apparently some fo the other intel modules might conflict and cause the proper one from being loaded.  Try blacklisting all the one you don't need (e100 ee100, ect)

Might also want to search /var/log/dmesg and see if "e1000" is showing up anywhere

Some info here: [http://www.ubuntuforums.org/showthread.php?p=741687](http://www.ubuntuforums.org/showthread.php?p=741687)

Also looks like your friend is running stock install of ubuntu with none of the recent updates.  If you can get it connected to the interent and let it install the new kernel it might come with an updated driver...

Also look into installing edgy or fiesty, it might also have newer drivers.

---

### Post by BigBabyDaddy1968 on 2007-03-23
Loads of help, considering the hour.  Thank you.  I will definitely have a go at that tomorrow and let you know the results...I'll try to not crash anything this time....

---

### Post by chili555 on 2007-03-23
> editing /etc/modules.confIn Ubuntu, it's actually /etc/modules. The alias part is exactly correct.

If you google up 'e1000 bug', you will see this is quite a problematic module. Is this in a desktop or a laptop? If a desktop, Newegg is your friend.

---

### Post by BigBabyDaddy1968 on 2007-03-23
It is a desktop (Dell XPS 410 Media Center Edition).  If I can get this to work as configured, that's preferable since I just bought it this past Xmas.  

Thanks again for any/all input.

---

### Post by esaym on 2007-03-23
> **BigBabyDaddy1968 said:**
> It is a desktop (Dell XPS 410 Media Center Edition).  If I can get this to work as configured, that's preferable since I just bought it this past Xmas.  

Thanks again for any/all input.

Oh really?  I can't help you if you want gigabit ethernet but this card is plug and play, and cheap [http://www.directron.com/pro200wl.html](http://www.directron.com/pro200wl.html)  [http://www.linuxquestions.org/hcl/showproduct.php?product=820&cat=131](http://www.linuxquestions.org/hcl/showproduct.php?product=820&cat=131)

---

