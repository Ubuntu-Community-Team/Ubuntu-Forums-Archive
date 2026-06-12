---
title: "How do I get sound?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by nra2877 on 2008-01-19
I just installed Linux 7.10 on my PC and I dont have any sound. I just successfully installed Adobe Flash after a million attempts and I need sound to go with the video. I must warn that I am extremely illiterate when it comes to this kind of stuff and need things explained in layman's terms. I trying to learn but it's all new and confusing to me. Any and all help will be greatly appreciated.

---

### Post by ubuntu-freak on 2008-01-19
I'd suggest you search 'sound compile' or 'sound how-to'.
 
There are many reasons why sound doesn't work for some. Try the simple things first.
 
sudo apt-get install alsamixer
 
It will install into your applications menu.

It's a shame so many are having sound issues. You could try upgrading to the Hardy kernel also. Works for some.
There's a how-to on that.

Nathan

---

### Post by nra2877 on 2008-01-19
> **reassuringlyoffensive said:**
> I'd suggest you search 'sound compile' or 'sound how-to'.
 
There are many reasons why sound doesn't work for some. Try the simple things first.
 
sudo apt-get install alsamixer
 
It will install into your applications menu.

It's a shame so many are having sound issues. You could try upgrading to the Hardy kernel also. Works for some.
There's a how-to on that.

Nathan

Sorry to sound like such a moron but I really don't understand any of that. The "sudo apt..." is something I run in terminal right? I have no idea what Hardy kernel is. I'm trying to learn as I go but I was never very PC literate. Thanks for the reply and I appologize if its a burden to have to explain it to me further.

---

### Post by jcwmoore on 2008-01-19
I had problems with my sound in version 7.04 and 7.10, well it turned out that some of the sound settings were muted on my machine by default.  this may not by your problem it couldn't hurt to check that all your sound is turned up.  

right click on the speaker icon and open the volume control, then Edit>Preferences and click on all the options.  after than just make sure nothing is muted

simple fix for me, so i can't say that it will work for you, or even that that's what is wrong...

---

### Post by ubuntu-freak on 2008-01-19
> **nra2877 said:**
> Sorry to sound like such a moron but I really don't understand any of that. The "sudo apt..." is something I run in terminal right? I have no idea what Hardy kernel is. I'm trying to learn as I go but I was never very PC literate. Thanks for the reply and I appologize if its a burden to have to explain it to me further.

 
Yeh the Terminal.
 
/Applications/Accessories
 
I'm no expert on this issue as I've never ever had sound issues. Like the previous post said, try the simple things first.
 
The Hardy kernel is the next Ubuntu releases kernel. The kernel is the engine, workhorse, gets everything working together. The brain of Ubuntu. 
 
Linux = kernel
GNU = operating system 
 
Don't forget to use 'sudo' when you install or make system changes. gksudo for you use gedit or other GUI apps from the terminal or run command app.
 
Try searching those keywords I gave you. Install alsamixer too.
 
Let me know if you get sound working at some point.
 
Nathan

---

### Post by mmb1 on 2008-01-19
Go to your applications-accessories menu, you should find a program labeled, "terminal", open it and type "sudo alsamixer", then post the output. 

If you need any help at all interpreting, or if you need to me to be more thourough, please feel free to ask.

---

### Post by ubuntu-freak on 2008-01-19
Have you tinkered with the mixer applet on the panel near the clock? Also, type 'alsamixer' in the terminal and see if sound is enabled properly.
 
Failing that try
 
sudo apt-get install linux-backports-modules-generic
 
Nathan

---

### Post by Sef on 2008-01-19
> sudo apt-get install linux-backports-modules-generic

You don't need to use backports.  I had a problem because of that module was missing.  

First let's check what kernel you are running

Applications > Accessories > Terminal

```
uname -a
```

If you are running a generic kernel, type in this one:

```
sudo apt-get install linux-ubuntu-modules-2.6.22-14-generic
```

If you are running the i386 kernel, then run this one:

```
sudo aptitude install linux-ubuntu-modules-2.6.22-14-386
```

---

### Post by ubuntu-freak on 2008-01-19
Really? I've never had sound issues so I'm just quoting what others did to cure theirs. I'll remember what you said though.
 
Nathan

---

### Post by kostkon on 2008-01-19
> **nra2877 said:**
> I just installed Linux 7.10 on my PC and I dont have any sound. I just successfully installed Adobe Flash after a million attempts and I need sound to go with the video. I must warn that I am extremely illiterate when it comes to this kind of stuff and need things explained in layman's terms. I trying to learn but it's all new and confusing to me. Any and all help will be greatly appreciated.

OK, so many people here suggested you to do some unnecessary (and complex) things blindly, without even knowing what type of sound card you have.

Please, you don't specify what is your sound card in order the people here at the forums to be able to help you. It is necessary to give the details of your card in order the people that will want to help you, to be able to check if your card is supported by you Ubuntu and if any extra action would be needed to make it to work.

Also, if you have a laptop, giving its brand and the model would be useful. 

Please open a terminal that you will find at  *Applications -> Accessories -> Terminal*, type
```
lspci -v
```
press Enter, and please post the output here.

---

### Post by ahervey85 on 2008-01-22
sorry to butt in but i too am trying to get some help getting sound i ran lspci -v and here is my out put - 

angel@angel-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c4000000-c6ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00004000-00007fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f3ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00008000-0000bfff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cbffffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f8000000-f80fffff
        Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f8404c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Memory behind bridge: f8100000-f81fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 18d8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18d0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f8404000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: medium devsel, IRQ 10
        Memory at c2100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at c000 [size=256]
        Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at c2000000 [disabled] [size=128K]
        Capabilities: <access denied>

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at f8100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
 

any help would be greatly appreciated!

---

### Post by dcstar on 2008-01-23
> **nra2877 said:**
> I just installed Linux 7.10 on my PC and I dont have any sound. I just successfully installed Adobe Flash after a million attempts and I need sound to go with the video. I must warn that I am extremely illiterate when it comes to this kind of stuff and need things explained in layman's terms. I trying to learn but it's all new and confusing to me. Any and all help will be greatly appreciated.

Try installing the **esound** package and see if that helps.

---

### Post by ahervey85 on 2008-01-23
would this work for me? can someone please help?

---

### Post by ubuntu-freak on 2008-01-23
> **ahervey85 said:**
> would this work for me? can someone please help?

 
Did you type 'alsamixer' in the terminal? Some have to unmute their sound manually that way. Did you try Sef's solution on page 1? If they don't work, post your output in a sound how-to thread. The guys who write those know lots more than me about all these sound issues. Try the simple things first, like alsamixer. 
 
Nathan 
 
Note: MM in alsamixer means its muted, OO means it isn't. If it isn't muted, try Sef's solution.

---

### Post by ahervey85 on 2008-01-23
i tried the -

sudo aptitude install linux-ubuntu-modules-2.6.22-14-386 

and it messed up my laptop monitor/video when i restarted so i think i will pass on that. i was really posting for kostkon b/c he suggested to do 

lspci -v and post the output which i did. as for you suggestion you mean starting another thread titled what exactly? what do i put to let people know that i still need help?

---

### Post by ubuntu-freak on 2008-01-23
> **ahervey85 said:**
> i tried the -

sudo aptitude install linux-ubuntu-modules-2.6.22-14-386 

and it messed up my laptop monitor/video when i restarted so i think i will pass on that. i was really posting for kostkon b/c he suggested to do 

lspci -v and post the output which i did. as for you suggestion you mean starting another thread titled what exactly? what do i put to let people know that i still need help?

 
There are already threads about compiling your sound driver. Do a search. Try google too. It should always be fixable. I'm no expert on it though as I've never had the problem.
 
Nathan

---

### Post by lninjo on 2008-01-23
I had the same problem. I tried using the third party and restricted packages and was able to get my sound to work


I also install the pcm packages do you see a master channel

---

### Post by lninjo on 2008-01-23
i always got to synaptic to download packages first. If they are not listed then i will go to the terminal

---

### Post by ahervey85 on 2008-01-23
yeah i can see the master and pcm channel in alsamixer but there is nothing underneath them and the volume is turned all way up

---

### Post by blerinab on 2008-01-26
I have the exact same problem. I get the same output when i do a lspci -v. 
And i also dont see  the green 00 or grey MM in alsamixer.

---

