---
title: "need help with airlink card."
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by skot on 2007-03-18
i was hoping someone could point me out to some information on how to get my
Airlink AWLH3026T card to work. 

ive searched the NdisWrapper route but it lists the card as unsupported. but seaching through posts on this site i see people using other airlink cards not on the NdisWrapper list.
in the terminal i used *lspci* and what i think is the right line lists......
*01:00.0 Network Controller: RaLink Unknown device 0302*
is this the line for my card?
step by step help would be great but im switching away from windows to start learning the inner workings of linux.  so any links to sites or documentation helping me with this problem would be great. but i need help on making this card work; which is something a cant find anywhere. so if you can tell me what to look for that would be awesome.

thanks in advance,

skot

---

### Post by crispy_420 on 2007-03-19
dmesg?

---

### Post by skot on 2007-03-19
> **crispy_420 said:**
> dmesg?

i ran that, what exactly should i be looking for. thanks/

---

### Post by skot on 2007-03-19
ok after figuring out a way to send files between my 2 computers heres what the dmesg output
i think i might have the section your looking for.  if not let me know and i can post more....


```

[17179573.560000] ACPI: bus type pci registered
[17179573.560000] PCI: Using MMCONFIG
[17179573.560000] Setting up standard PCI resources
[17179573.572000] ACPI: Interpreter enabled
[17179573.572000] ACPI: Using IOAPIC for interrupt routing
[17179573.572000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.572000] PCI: Probing PCI hardware (bus 00)
[17179573.576000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.576000] Boot video device is 0000:01:01.0
[17179573.576000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.584000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179573.588000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179573.588000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.588000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.588000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.588000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179573.588000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179573.588000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.588000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[17179573.588000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.588000] pnp: PnP ACPI init
[17179573.592000] pnp: PnP ACPI: found 15 devices
[17179573.592000] PnPBIOS: Disabled by ACPI PNP
[17179573.592000] PCI: Using ACPI for IRQ routing
[17179573.592000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.592000] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
[17179573.592000] PCI: Bridge: 0000:00:1e.0
[17179573.592000]   IO window: a000-afff
[17179573.592000]   MEM window: e0000000-e1ffffff
[17179573.592000]   PREFETCH window: d0000000-dfffffff
[17179573.592000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.592000] NET: Registered protocol family 2
[17179573.636000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.636000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179573.636000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179573.636000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.636000] TCP reno registered
[17179573.636000] audit: initializing netlink socket (disabled)
[17179573.636000] audit(1174249657.636:1): initialized
[17179573.636000] highmem bounce pool size: 64 pages
[17179573.636000] VFS: Disk quotas dquot_6.5.1
[17179573.636000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.636000] Initializing Cryptographic API
[17179573.636000] io scheduler noop registered
[17179573.636000] io scheduler anticipatory registered
[17179573.636000] io scheduler deadline registered
[17179573.636000] io scheduler cfq registered (default)
[17179573.636000] isapnp: Scanning for PnP cards...
[17179573.988000] isapnp: No Plug & Play device found

```

---

### Post by skot on 2007-03-20
how do black list a driver?  i was told to do this...
> 
Add "blacklist mrv8k"

to the bottom of the file:

/etc/modprobe.d/blacklist


im not quite sure on how to black list something. and when i look through the file structure the only folder i see under modprobe.d is "arch"

ive found the drivers i need to install and will post all my findings after i get it up and running.  but i need to get past this part.

---

### Post by skot on 2007-03-20
ok i figure out how to get the command to work.....
```

gksudo gedit /ect/modprobe.d/blacklist

```

then a window pops up and it looks like a text document.  so i type "blacklist mrv8k" minus quotes and i get an error "could not save the file  /ect/modprobe.d/blacklist.
unexpected error: file not found"

then when i look back at the terminal i see  error messages from my attempt to save the file
file

```

skot@orange:~$ gksudo gedit /ect/modprobe.d/blacklist

(gedit:10410): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gedit:10410): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
skot@orange:~$ 

```


any ideas?

thanks
skot

---

### Post by Ptero-4 on 2007-03-20
The error is because the folder is called /etc . There`s no folder called /ect.

---

### Post by skot on 2007-03-20
im a moron.  i am the typo king.

so now i got it to work, hehe
i just added the line..... 
```
 blacklist mrv8k 
```
at the end of the document. do i need to type any thing else like a reason with a "#" before hand like all the other things listed by defult?

its just double spaced at the end all by itself.

---

### Post by skot on 2007-03-20
ok now im stuck (as if is want stuck before) after all the typos and not understanding how to load packages and such ive done all i need to do (as im told) to get my wireless going.

i blacklisted the original driver that loads up with ubuntu. (Marvel Libertas 8000 driver)
then i installed ndiswrapper and utility programs from synaptic package manager 
i then pointed the "windows wireless drivers" program to my new driver "mrv8000c.inf"
driver *mrv8000c* now added butit  lists "hardware present: no"

i run ```
lspci
``` and it still lists 
```

network controller: ralink unknown device 0302

```

ive reset my cpu and still lists that.  am i missing something?

---

### Post by tgalati4 on 2007-03-20
Dear Skot,

Sorry to hear of your troubles.  It appears that the Airlink 101 has switched chipsets.  I only paid $7 for mine at Fry's Electronics.  The way they keep them cheap is by switching to the cheapest chipset during production.  Here is my lspci:

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


So you see, I have a Marvell chipset.  You appear to have a Ralink chipset.  No worries, you need to find a Ralink windows driver:  cheesyralinkdriver.inf

Do a few searches and let us know what you find.

Getting wireless to work is a chore under Ubuntu.  The mixture of wireless chipsets (mostly closed) and vast array of laptop hardware out there make finding a good combination difficult.  That is why there is an Ubunutu wiki page devoted to wireless.  This way people can post what works and go out and buy compatible hardware.  

I bought the Airlink because of the open source Marvel driver, but as you can see, it would not work in my case.  I had to use the Windows driver under ndiswrapper instead.  It works, and for $7, it's definitely worth it.

Keep the faith.

Terry

---

### Post by tgalati4 on 2007-03-20
If you do a quick search of "ralink" in the forums, you find quite a few suggestions, including:

[http://ubuntuforums.org/showthread.php?t=369100&highlight=ralink](http://ubuntuforums.org/showthread.php?t=369100&highlight=ralink)

Good luck!

You might need to blacklist the Ubuntu ralink driver as well if you find that it interferes with ndiswrapper.  Others have gotten the ralink to work under Ubuntu, so keep the faith.

When you sent me a private message, I assumed that you had a similar card to mine.

I have an Airlink 101 AWLC3026 pcmcia 54 mbps wireless card with a Marvell (Libertas) 8000 series chipset.  It works with ndiswrapper and Mrv8000c.inf windows driver on an old Dell Inspiron 7500 laptop.

You have an Airlink AWLH3026T running on unknown hardware.  Obviously your Airlink card is different from mine.  Your hardware thinks it is a Ralink chipset, but can't pin down the exact model.  That is why you get an error in lspci.  The driver won't load if there is not an exact match.  Sort of like the difference between /etc and /ect.  Linux is particular about those things.

Do a google search on AWLH3026T Linux and see what comes up.

Looking for help through private messages reduces exposure to the wider community.  Of course providing advice through PM is dumb as I have discovered.

Post the output of:

lsmod

---

### Post by dawv on 2007-03-26
ummmm i cant understand what your saying.....

does ralink work for an Airlink101 AWH3026T? or does linux "think" it will... or what exactly are you talking about......

---

### Post by xueg0i on 2007-03-26
you might want to look on [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) . This is a page dedicated to opensource ralink drivers for linux.

Goodluck!

---

### Post by dawv on 2007-03-26
so AWLH3026t uses ralink drivers... this makes no sense.... or are you guys saying that it *DOESN'T* work... cuz that would make more sense... as it was being blacklisted..

---

### Post by xueg0i on 2007-03-27
Hi dawv, please don't panic ;)

After a short search on the web, I think you have a ralink chipset on your wireless card. This means: probable it will work!

We'll first try the easy way, do:
```
sudo modprobe -v rt2500
```
If you are lucky you will see no errors, but something about a driver being loaded. In this message you can see how your wireless card is recognized. Should be something like wlan0 or eth1. Then:
```
sudo ifconfig wlan0 up
```
Ofcourse you will have to change wlan0 to whatever was displayed before. Please post dmesg and iwconfig results.

A forum is not the fastest way of helping people, but we will get to the solution eventually.

Kind regards & good luck,

Xueg0i.

---

