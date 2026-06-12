---
title: "Can't install ethernet card drivers!"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by simon303 on 2006-11-30
Ive just installed Ubuntu on my computer and it won't connect to the internet.
Infact it can't even detect my ethernet card and im unable to follow the manufacturers instructions for installing the drivers as Ubuntu obviously differs in setup from the type of system they expect to be used.
Im using a Belkin desktop Network PCI Card.
Any ideas on installing the drivers?
I would be gratefull for any hints/tips/solutions that my get it working.

---

### Post by Bachstelze on 2006-11-30
Ubuntu is Linux. Any Linux driver will work in Ubuntu, just follow the instructions provided by Belkin and post here if you don't understand something :)

---

### Post by simon303 on 2006-11-30
the instructions are:
A) Driver Installation by Using Bundled Driver
   ===========================================
   Some LINUX kernels had supported rtl8139 NIC. You can check whether
   rtl8139.o exists or not. If your LINUX (ex. RedHat 6.1 or above) can
   auto-detect rtl8139 NIC, you just skip the following installations and
   follow the screen's instructions to install rtl8139.o driver directly.

   1. Check the driver file "/lib/modules/2.0.XX/net/rtl8139.o".
      Where the XX is the version number of the latest kernel.

   2. Add "alias eth0 rtl8139" into the /etc/conf.modules file.

      cd /etc
      vi conf.modules
         alias eth0 rtl8139

   3. Run the following commands at the LINUX prompt.

      modprobe rtl8139

      ifconfig eth0 192.74.53.10

   4. Now, you can run 'ifconfig' or 'netstat -i' to see if there is a
      interface 'eth0'.

but i can't seem to get it to do anything

---

### Post by Bachstelze on 2006-11-30
Hmm, what does that do ?

```
sudo modprobe rtl8139
```

---

### Post by simon303 on 2006-11-30
it come up with the error text
> FATAL: Module rtl8139 not found.

---

### Post by Johan! on 2006-11-30
The rtl8139 module is already inside the kernel.
So you don't want to install the Belkin drivers.

try this:
```
 dmesg |grep 8139
```

This is the output of my server (Dapper) with a rtl8139 card:
```
[17179591.084000] 8139too Fast Ethernet driver 0.9.27
[17179591.084000] eth0: RealTek RTL8139 at 0xe08ea000, 00:50:bf:d9:bf:5b, IRQ 11
[17179591.084000] eth0:  Identified 8139 chip type 'RTL-8139C'
[17179591.116000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
```

Do you see any errors in your output?

---

### Post by simon303 on 2006-11-30
that doesn't actually do anything
it still doesn't know its got an ethernet card connected to it

---

### Post by Johan! on 2006-11-30
Try this:

lspci |grep 8139

It should print something like this:

0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

And if it doesn't:

lspci

there you can see all pci devices in your computer.

---

### Post by simon303 on 2006-11-30
```
lspci |grep 8139
```
does nothing
```
lspci
```
brings a whole list of things up but no ethernet reference among them

---

### Post by Johan! on 2006-11-30
can you copy/paste the output of lspci?

also, what does this command tell you?
sudo lshw -C network

---

### Post by simon303 on 2006-11-30
result of lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller:  Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
01:05.0 VGA compatible controller: nVidia Corperation NV11 [GeForce2 MX/MX 400] (rev al)
```

about to try
sudo lshw -C network

---

### Post by simon303 on 2006-11-30
sudo lshw -C network
just flashes a couple of things, pausing slightly on IDE to read cd drive, but no output to copy

---

### Post by Johan! on 2006-11-30
If your network card doesn show up when you type lspci, then your computer doesn't recognise it.

What mainboard do you have, and what is the exact model of the network card?

edit:
what does
sudo lspci -vv
say?

---

### Post by simon303 on 2006-11-30
ive gone into system>administration>divec manager
but i cant work out which item its likely to be
it all worked fine when it ran windows xp before

sudo lspci -vv
brings up alot of text that i cant copy across as i have to write it down and type it out on another machine

---

### Post by Johan! on 2006-11-30
Do you see any errors?
Do you see any lines that look like your ethernet card?

---

### Post by simon303 on 2006-11-30
it looks ok to me

---

### Post by CatKiller on 2006-11-30
> **simon303 said:**
> I would be gratefull for any hints/tips/solutions that my get it working.

Actually my network card (different make/model) didn't work after the upgrade to Breezy (it had worked in Hoary) until I moved it into a different slot. Something to do with a change in IRQ sharing, I'd imagine.

The reason I mention it is because it's possible that the reason it isn't showing up might well not be a driver issue, but a more fundamental hardware one.

Once I'd sorted out my IRQ problem, it worked straight away. Just a thought.

---

### Post by simon303 on 2006-11-30
i have tried moving it but no luck
any idea on a 'preferred' slot?

IRQ problem?

---

### Post by CatKiller on 2006-11-30
> **simon303 said:**
> i have tried moving it but no luck
any idea on a 'preferred' slot?

Not really. One that doesn't share an IRQ with anything else, I guess. If you press the Pause/Break key at the appropriate point in the boot process, you can see which IRQs have been assigned to which device. Pressing Enter will cause the boot process to continue.

> IRQ problem?

In my case, I think it was that the network card was sharing an IRQ with the graphics card. Or the IDE controller. Can't remember now.

---

### Post by simon303 on 2006-11-30
here are the driver instalation instructions if anyone can see anything in them that would help

Belkin Components
                  F5D5000 PCI Card / Desktop Network PCI Card
                       Driver Installation for LINUX

  Contents:
  ---------
    A) Driver Installation by Using Bundled Driver
    B) Driver Installation by Using Compiled Driver

A) Driver Installation by Using Bundled Driver
   ===========================================
   Some LINUX kernels had supported rtl8139 NIC. You can check whether
   rtl8139.o exists or not. If your LINUX (ex. RedHat 6.1 or above) can
   auto-detect rtl8139 NIC, you just skip the following installations and
   follow the screen's instructions to install rtl8139.o driver directly.

   1. Check the driver file "/lib/modules/2.0.XX/net/rtl8139.o".
      Where the XX is the version number of the latest kernel.

   2. Add "alias eth0 rtl8139" into the /etc/conf.modules file.

      cd /etc
      vi conf.modules
         alias eth0 rtl8139

   3. Run the following commands at the LINUX prompt.

      modprobe rtl8139

      ifconfig eth0 192.74.53.10

   4. Now, you can run 'ifconfig' or 'netstat -i' to see if there is a
      interface 'eth0'.


   Other Installation Method
   -------------------------
   RedHat 6.x
     - Run "linuxconf" to setup your card.

        Select Networking -> Client tasks -> Basic host information
        -> Click Adaptor 1 to configure your adapter

        For example:

             Click "Enabled" (i.e. enable "Activate interface at boot time")

             IP address      192.74.53.10
             Netmask         255.255.255.0
             Net device      eth0
             Kernel module   rtl8139
             I/O port
             Irq

     - Save the changes and run "shutdown -r now" to reboot the system.


   Slackware:
     - Add "alias eth0 rtl8139" into the /etc/conf.modules file.
     - Run netconfig to configure IP.
     - Modify /etc/rc.d/rc.modules:
         Add one line: /sbin/modprobe rtl8139


B) Driver Installation by Using Compiled Driver
   ============================================
   Below are the instructions for installing linux driver. You must complie
   the source code to generate rtl8139.o and use "insmod" to insert rtl8139.o
   as module. You can use "netconfig" utilities to setup network parameters
   for the driver.

   Files Description:
   ------------------
   rtl8139.c  The adapter source code. You can download the newest version
              from [http://www.scyld.com/network/rtl8139.html](http://www.scyld.com/network/rtl8139.html).
   trans      Compile batch file.
   linux.txt  This file.

   Installation:
   -------------
   1. Plug F5D5000 PCI Card into PC's PCI-bus slot.

   2. Boot into LINUX and keyin the following commands at the LINUX prompt.
      Remember, LINUX is case sensitive.

         mkdir /temp
         mcopy a:/linux/rtl8139.c /temp
               (Copied from LINUX directory of the driver diskette.)
               ("mcopy" is the mtools. If you don't have mtools, you can
                mount -t msdos /dev/fd0 /mnt and use cp command)
         mcopy a:/linux/trans /temp
         cd /temp
         chmod 777 trans

   3. Run trans file to complie and copy driver to linux source code:

         cd /temp
         ./trans

         (rtl8139.o will be generated and be copied to /usr/src/linux/modules.)

   4. Run netconfig (or netcfg) to set you network parameter (like ip, gateway).

      Slackware: Run "netconfig" to configure IP environment.
                 This will create '/etc/rc.d/rc.inet1' and 'rc.inet2' files.

         netconfig


      RedHat:
      - Add "alias eth0 rtl8139" into the /etc/conf.modules file.
         cd /etc
         vi conf.modules
            alias eth0 rtl8139

      - Run "netcfg" in the xterm of X-window to configure IP environment.
         startx
         netcfg
         (Configure IP of eth0 and enable "Activate interface at boot time".)


   5. Use editor vi to modify 'rc.inet1'(or 'rc') in the /etc/rc.d directory to
      insmod driver.  This file will be run at boot time. You just add a line
      at the beginning of 'rc.inet1'(or 'rc').

      Slackware:
         cd /etc/rc.d
         vi rc.inet1
            insmod /usr/src/linux/modules/rtl8139.o

      RedHat: Add a line at the beginning of 'rc' file.
         cd /etc/rc.d
         vi rc
            insmod /usr/src/linux/modules/rtl8139.o

   6. Reboot the LINUX.

         reboot    ( or shutdown -r now )

      When system boots, the driver will be loaded. Then the driver will
      scan I/O port to see if a card is there.
      (You can run 'dmesg' to see the boot message.)

   7. Run 'ifconfig' or 'netstat -i' to see if there is a interface 'eth0'.

----
All trademarks or brand names mentioned are properties
of their respective companies.



---

### Post by Johan! on 2006-11-30
This is not going to work:-k 


Ubuntu already has all the drivers for your card.

Ubuntu doesn't "see" the ethernet card.
That's why it won't work.

If Ubuntu finds the card, it will automatically recognize it and use it.
I don't understand why Ubuntu doesn't see your card.](*,)

---

### Post by simon303 on 2006-11-30
ok
i will rephrase my question to see if anyone can help
does anyone know of a way of making Ununtu "see" my ethernet card?

---

