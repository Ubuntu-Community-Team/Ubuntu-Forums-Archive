---
title: "Hello!"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by waste301 on 2007-09-11
I'm a complete newb to ubuntu, first time using it, first time loading it on a brand new PC. I installed it, as a dual boot with the windows XP that came with thte system.

When I boot into ubuntu and click firefox, there is no connection. When I goto system-->network (there is no networking) it only shows an inactive dial-up connection.

Do I need to create a network connection or something? When I boot into windows it connects fine.

---

### Post by reckless2k2 on 2007-09-11
welcome to ubuntu. we are going to need a little more info. is this a laptop or desktop....make and model please.....how are you connecting...wired or wireless....

hahaha

pretend you are calling dell, hp, microsoft, or the geek squad....HAHAHAHAHA

we need more info to help.

---

### Post by waste301 on 2007-09-11
Brand new dell desktop.  Dual-core, 80  gig hard drive I just repartitioned using the  Ubuntu installation software. Connecting with Comcast, no network - I'm plugging the modem into my PC.  When I boot into Ubuntu it doesn't see the network.

---

### Post by reckless2k2 on 2007-09-11
under network connections are you set to get dhcp? your interface would have to be active as well...should be like eth0. this should have been setup on install. 

go into system > admin...> network. 

enable the interface then make sure the dhcp setting is config under properties for that interface.

it should get an address then. 

opps...just read your post...it doesn't see the network card....hhmm...

that's odd. how did you install with no networking?

i need an open terminal and type this:

lspci -v

and post it for us.

---

### Post by Maestro23 on 2007-09-11
> **reckless2k2 said:**
> under network connections are you set to get dhcp? your interface would have to be active as well...should be like eth0. this should have been setup on install. 

go into system > admin...> network. 

enable the interface then make sure the dhcp setting is config under properties for that interface.

it should get an address then. 

opps...just read your post...it doesn't see the network card....hhmm...

that's odd. how did you install with no networking?

i need an open terminal and type this:

lspci -v

and post it for us.

Yeah, that stumped me too.  His post caught my eye because I have Comcast Broadband as well, and everyting was detected with no problems on installation.

---

### Post by Digitallysick on 2007-09-11
hopefully connected via ethernet cable and not usb

---

### Post by waste301 on 2007-09-11
No - I can't tell if it sees the network card, because I don't know how to check.  The connection light is flashing normal.

I installed by downloading and burning the cd.  Ubuntu comes up fine, but shows nothing under system-->network but a generic dial up connection.  Is ther something I need to do to create a network connection?

---

### Post by waste301 on 2007-09-11
> **Digitallysick said:**
> hopefully connected via ethernet cable and not usb

I've got an rj-45 cable cable going from the modem to my network.  It works with windows.

---

### Post by reckless2k2 on 2007-09-11
lspci -v 

we need the output...i'm wondering if it's an unsupported net card which would be highly unlikely.

---

### Post by Maestro23 on 2007-09-11
> **waste301 said:**
> No - I can't tell if it sees the network card, because I don't know how to check.  The connection light is flashing normal.

I installed by downloading and burning the cd.  Ubuntu comes up fine, but shows nothing under system-->network but a generic dial up connection.  Is ther something I need to do to create a network connection?

Type in the command that was posted earlier. You will need to open a terminal.

> lspci -v

Copy/past the output here for us.

---

### Post by waste301 on 2007-09-11
OK - I'll have to reboot a couple times, so it will be a  sec.  I'm assuming it will be easy to figure out how to open a terminal in ubuntu.  Yes, I'm an idiot newb.

---

### Post by reckless2k2 on 2007-09-11
applications > accessories > terminal

no idiots ...only grasshoppers

---

### Post by waste301 on 2007-09-11
OK - I ran  lspci -v, and got the info you needed, but I can't save a file that windows can access, and I can't save it as a .doc in Open Word and email it to my self. How do I copy the results and post them here?

Once again, I feel like an idiot, but I'm a windows tech.

---

### Post by ubonewbo on 2007-09-11
Hello,

I'm a newbie too, but if you're using Terminal from Applications/Accessories the terminal should have Edit in the menu bar at the top. Just highlight the text and then select Copy from the Edit menu. This puts it on the clipboard. Then paste directly into this reply box with Ctrl/V or Paste from the right-click menu.

Hope that helps.
:)

---

### Post by waste301 on 2007-09-11
> **ubonewbo said:**
> Hello,

I'm a newbie too, but if you're using Terminal from Applications/Accessories the terminal should have Edit in the menu bar at the top. Just highlight the text and then select Copy from the Edit menu. This puts it on the clipboard. Then paste directly into this reply box with Ctrl/V or Paste from the right-click menu.

Hope that helps.
:)

The problem is that I can't access the internet on ubuntu.  I would do what you said, but to get back to this forum I have to restart in Windows, so I cant save what is on my clipboard.

I can save the log as a .doc - but only to the ubuntu partition, which windows can't read.  I can't email it to myself as a .doc and post it - because I can't get online in ubuntu!!

Do I have a faulty installation or something?

---

### Post by ubonewbo on 2007-09-11
I had no problems with Firefox or Internet access -- it all happened automagically, so maybe your installation is faulty or something. There will be someone along much more knowledgeable than me soon. 

As for the message in terminal, can you paste it from the clipboard into a new document, save it and than back the document up on a flash drive or disk so you can use it in your other partition?

---

### Post by waste301 on 2007-09-11
> **ubonewbo said:**
> I had no problems with Firefox or Internet access -- it all happened automagically, so maybe your installation is faulty or something. There will be someone along much more knowledgeable than me soon. 

As for the message in terminal, can you paste it from the clipboard into a new document, save it and than back the document up on a flash drive or disk so you can use it in your other partition?

Good idea. I will reboot into ubunto and plug in my flash drive.   Hopefully it will see it and I'll save the log there and post it here.

Be back in few.

---

### Post by waste301 on 2007-09-12
ubonewbo  YOU ARE THE MAN

Here is the log:


matt@matt-desktop:~$ lspci -v

00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)

        Subsystem: Dell Unknown device 023d

        Flags: bus master, fast devsel, latency 0

        Capabilities: <access denied>



00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02) (prog-if 00 [Normal decode])

        Flags: bus master, fast devsel, latency 0

        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

        I/O behind bridge: 0000c000-0000cfff

        Memory behind bridge: f8000000-fbffffff

        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff

        Capabilities: <access denied>



00:19.0 Ethernet controller: Intel Corporation Unknown device 10c0 (rev 02)

        Subsystem: Dell Unknown device 023d

        Flags: bus master, fast devsel, latency 0, IRQ 10

        Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]

        Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]

        I/O ports at ff00 [size=32]

        Capabilities: <access denied>



00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02) (prog-if 00 [UHCI])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, medium devsel, latency 0, IRQ 16

        I/O ports at fe00 [size=32]

        Capabilities: <access denied>



00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02) (prog-if 00 [UHCI])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, medium devsel, latency 0, IRQ 18

        I/O ports at fd00 [size=32]

        Capabilities: <access denied>



00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02) (prog-if 00 [UHCI])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, medium devsel, latency 0, IRQ 17

        I/O ports at fc00 [size=32]

        Capabilities: <access denied>



00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02) (prog-if 20 [EHCI])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, medium devsel, latency 0, IRQ 20

        Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]

        Capabilities: <access denied>



00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)

        Subsystem: Dell Unknown device 023d

        Flags: bus master, fast devsel, latency 0, IRQ 21

        Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]

        Capabilities: <access denied>



00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02) (prog-if 00 [UHCI])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, medium devsel, latency 0, IRQ 19

        I/O ports at fb00 [size=32]

        Capabilities: <access denied>



00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02) (prog-if 00 [UHCI])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, medium devsel, latency 0, IRQ 17

        I/O ports at fa00 [size=32]

        Capabilities: <access denied>



00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02) (prog-if 00 [UHCI])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, medium devsel, latency 0, IRQ 20

        I/O ports at f900 [size=32]

        Capabilities: <access denied>



00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02) (prog-if 20 [EHCI])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, medium devsel, latency 0, IRQ 19

        Memory at fdffd000 (32-bit, non-prefetchable) [size=1K]

        Capabilities: <access denied>



00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])

        Flags: bus master, fast devsel, latency 0

        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32

        I/O behind bridge: 0000d000-0000dfff

        Memory behind bridge: fde00000-fdefffff

        Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff

        Capabilities: <access denied>



00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)

        Subsystem: Dell Unknown device 023d

        Flags: bus master, medium devsel, latency 0

        Capabilities: <access denied>



00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17

        I/O ports at f800 [size=8]

        I/O ports at f700 [size=4]

        I/O ports at f600 [size=8]

        I/O ports at f500 [size=4]

        I/O ports at f400 [size=16]

        I/O ports at f300 [size=16]

        Capabilities: <access denied>



00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)

        Subsystem: Dell Unknown device 023d

        Flags: medium devsel, IRQ 11

        Memory at fdffc000 (64-bit, non-prefetchable) [size=256]

        I/O ports at 0500 [size=32]



00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02) (prog-if 85 [Master SecO PriO])

        Subsystem: Dell Unknown device 023d

        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17

        I/O ports at f100 [size=8]

        I/O ports at f000 [size=4]

        I/O ports at ef00 [size=8]

        I/O ports at ee00 [size=4]

        I/O ports at ed00 [size=16]

        I/O ports at ec00 [size=16]

        Capabilities: <access denied>



01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0402 (rev a1) (prog-if 00 [VGA])

        Subsystem: nVidia Corporation Unknown device 0505

        Flags: bus master, fast devsel, latency 0, IRQ 5

        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]

        Memory at d0000000 (64-bit, prefetchable) [size=256M]

        Memory at f8000000 (64-bit, non-prefetchable) [size=32M]

        I/O ports at cf00 [size=128]

        [virtual] Expansion ROM at fb000000 [disabled] [size=128K]

        Capabilities: <access denied>



matt@matt-desktop:~$

---

### Post by waste301 on 2007-09-12
^bump

Please help!  we're so close - I jst need someone to interpret the lspci -v an dtell me what is wrong!

---

### Post by Beggar on 2007-09-12
You seem to be missing some drivers, remarkably similar to this post:

[http://sudan.ubuntuforums.com/showthread.php?p=3058127](http://sudan.ubuntuforums.com/showthread.php?p=3058127)

Give me a minute, I will see if I cant track down the relavent eth driver and then we will go from there.

---

### Post by waste301 on 2007-09-12
> **Beggar said:**
> You seem to be missing some drivers, remarkably similar to this post:

[http://sudan.ubuntuforums.com/showthread.php?p=3058127](http://sudan.ubuntuforums.com/showthread.php?p=3058127)

Give me a minute, I will see if I cant track down the relavent eth driver and then we will go from there.

Thanks, you are my e-hero.  I really don't want to go back to windows.

---

### Post by Maestro23 on 2007-09-12
> **waste301 said:**
> Thanks, you are my e-hero.  I really don't want to go back to windows.

What's the model # off your Dell?

---

### Post by Beggar on 2007-09-12
Found it, its a EtherExpress PRO/100 VE. Now to find the driver...

---

### Post by waste301 on 2007-09-12
> **Maestro23 said:**
> What's the model # off your Dell?

here are the specs:

1	223-1769	Vostro 400, Intel Core2 Duo CPU E6550 (2.33GHz, 1333FSB 4MB L2)
1	311-7366	2GB DDR2 SDRAM 800MHz, Dual Channel DT
1	310-9322	Dell USB Keyboard
1	320-5667	Dell 22 inch Wide E228WFP Analog Flat Panel Monitor
1	320-5760	256MB NVIDIA GeForce 8600GT 2DVI
1	341-4988	80GB Serial ATA Hard Drive 7200RPM, 8MB Cache
1	341-4742	No Floppy Drive Requested
1	420-7369	Genuine Windows XP Home
1	420-7243	CyberLink PowerDVD 7.0 DVD Playback
1	310-9440	Windows XP Home backup CD
1	420-7180	Dell Support 3.4
1	420-7286	GOOGLE SEARCH PORTAL ON
1	313-5798	Dell Resource CD, Vostro 400
1	310-9326	Dell Scroll Mouse
1	430-2501	Integrated 10/100 Ethernet
1	313-5469	No Modem Requested
1	420-7275	Adobe Acrobat Reader
1	313-5456	16X DVD+/-RW Drive
1	420-7241	Roxio Creator
1	313-5672	Integrated 7.1 Channel Audio
1	313-5461	No speakers
1	420-7189	DellNetwork Assistant 1.7
1	420-7262	No Pre-installed Security Software
1	420-7280	No Internet Service Provider Requested
1	420-7281	No Pre-installed Productivity Software
1	412-0359	Soft Contracts - Qualxserve
1	983-4250	Warranty Support,Initial Year
1	987-6849	No Warranty, Year 2 and 3
1	983-8540	Type 3 Contract - Next Business Day Parts and Labor On-Site Response, Initial Year
1	988-0387	Dell Hardware Warranty PlusOnsite Service, Initial Year
1	987-7479	VOSTRO,Datasafe 10GB,1YR(Incl w/price)
1	420-7368	Dell DataSafe 2.0 Online, 10GBfor 1 Year Free (for ABU only)
1	960-8851	1YR AUT. PC TUNE UP,VOSTRO, Included in Price
1	420-7367	PC Tune-up, 1 Year (For English OS only)
1	462-4506	Purchase is NOT intended for resell
1	310-8591	You have chosen a Windows XP System
1	310-8977	S and P Drop-in-Box Marcom forBSD Systems Box

---

### Post by Maestro23 on 2007-09-12
> **Beggar said:**
> Found it, its a EtherExpress PRO/100 VE. Now to find the driver...

Begger beat me to it.  :)

---

### Post by Beggar on 2007-09-12
alrighty then,

```

sudo modprobe e100
dmesg | tail

```

Second command should let us know if it works :)

---

### Post by waste301 on 2007-09-12
sorry - total noob

I should reboot into ubuntu, open a terminal
type:

sudo modprobe e100
dmesg | tail

Then see if it recognizes my network card?

---

### Post by Beggar on 2007-09-12
Yup. to check run an ifconfig, should show you an internet (hypothetically it should get an ip address automatically).


Whoops that should read,->
Yup. to check run an ifconfig, should show you an interface (hypothetically it should get an ip address automatically).

Not deleting the first one cause everytime I read it, it makes me laugh.

---

### Post by waste301 on 2007-09-12
> **Beggar said:**
> Yup. to check run an ifconfig, should show you an internet (hypothetically it should get an ip address automatically).


Whoops that should read,->
Yup. to check run an ifconfig, should show you an interface (hypothetically it should get an ip address automatically).

Not deleting the first one cause everytime I read it, it makes me laugh.

OK - get this - now when I try to boot into ubuntu, its freezing.  The load bar comes up, and locks at 1%.

I'll post this and try it again, but I've already tried 3 times.

---

### Post by Beggar on 2007-09-12
This before or after my recommended change?

---

### Post by waste301 on 2007-09-12
> **Beggar said:**
> This before or after my recommended change?

OK - it let me boot into ubuntu.  I opened a terminal.  I typed: sudo modprobe e100

It asked me for a password.

I tried dmesg ! ( what is that vertical slash - its not on my keyboard!?!) tail

I tried: tail
It warned me about 2 attempts.

I stopped trying.


I'm sorry but you are going to have to explain this in the most idiot-friendly e-tard language.

---

### Post by Maestro23 on 2007-09-12
> **waste301 said:**
> OK - it let me boot into ubuntu.  I opened a terminal.  I typed: sudo modprobe e100

It asked me for a password.

I tried dmesg ! ( what is that vertical slash - its not on my keyboard!?!) tail

I tried: tail
It warned me about 2 attempts.

I stopped trying.


I'm sorry but you are going to have to explain this in the most idiot-friendly e-tard language.

The password is the one for the user account you setup during install.  This symbol "[COLOR="Red"] |[/COLOR] " should be on the key with your "[COLOR="Red"] \[/COLOR] ".  At least it is on my keyboard.

---

### Post by Beggar on 2007-09-12
yup, its going to be shift-\

---

### Post by waste301 on 2007-09-12
OK - thats not on my keyboard.  I'll try it again

---

### Post by waste301 on 2007-09-12
I tried several times to start ubuntu.  In recovery mode it says "Tried to start unkown devices  - try again in 5 seconds" but does nothing.

Is my installation screwed?  If so, should I try to reinstall ubuntu? (how?)

---

### Post by Beggar on 2007-09-12
The problem is that almost every single one of your hardware devices did not autodetect during setup. This means your computer is currently using a bunch of really basic drivers where it can, and sojme of your hardware isnt being used at all (your eth for example). You can try reinstalling if you want, this could have bee caused by the installer going haywire, if you do then I would recommend you double check the hash of the cd you are using to install (search the forums for how to do this, as this has been posted hundreds of times). Alternatly, you could just be the unluckiest person in the world, in which case once you will have to go through and get modules for all of the devices. Not hard, but not fun either.

---

### Post by waste301 on 2007-09-12
> **Beggar said:**
> The problem is that almost every single one of your hardware devices did not autodetect during setup. This means your computer is currently using a bunch of really basic drivers where it can, and sojme of your hardware isnt being used at all (your eth for example). You can try reinstalling if you want, this could have bee caused by the installer going haywire, if you do then I would recommend you double check the hash of the cd you are using to install (search the forums for how to do this, as this has been posted hundreds of times). Alternatly, you could just be the unluckiest person in the world, in which case once you will have to go through and get modules for all of the devices. Not hard, but not fun either.

I didn't double check the hash like it instructed - I assemed that it was OK - which makes an *** out of me.

However, it just let me boot into ubuntu and I did this:

Opened terminal

Typed:sudo modprobe e100

(no password auth this time!)

typed dmesg | tail

got this:

matt@matt-desktop:~$ sudo msdprobe e100

Password:

sudo: msdprobe: command not found

matt@matt-desktop:~$ modprobe e100

WARNING: Error inserting mii (/lib/modules/2.6.20-15-generic/kernel/drivers/net/mii.ko): Operation not permitted

FATAL: Error inserting e100 (/lib/modules/2.6.20-15-generic/kernel/drivers/net/e100.ko): Operation not permitted

matt@matt-desktop:~$ sudo modprobe e100

matt@matt-desktop:~$ dmesg | tail

[   25.716197] Bluetooth: HCI socket layer initialized

[   25.741254] Bluetooth: L2CAP ver 2.8

[   25.741257] Bluetooth: L2CAP socket layer initialized

[   25.938572] Bluetooth: RFCOMM socket layer initialized

[   25.938579] Bluetooth: RFCOMM TTY layer initialized

[   25.938581] Bluetooth: RFCOMM ver 1.8

[   37.202655] NET: Registered protocol family 10

[   37.202723] lo: Disabled Privacy Extensions

[  130.610390] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI

[  130.610393] e100: Copyright(c) 1999-2006 Intel Corporation

matt@matt-desktop:~$ 


HALP!

---

### Post by Beggar on 2007-09-12
why do you need help? 
  130.610390] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI

It worked.


Now, run ifconfig like I told you too.

```

ifconfig

```

it should display something like: 

eth0      Link encap:Ethernet  HWaddr 00:19:B9:7A:DB:A3  

Assuming that works fine (which Im pretty sure it will), you should be able to use System->admin->network to configure your internet connection.

Also, if you were to rerun lspci -v at this point it should display something different for the ethernet entry.

Either way I wont be able to help any more tonight, Ill check in on this thread tomorrow. If you run into more problems, just search the forums and/or google, every answer I gave you tonight can be found within 5 minutes of looking on those. Good luck!

---

