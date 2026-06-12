---
title: "Infos on switching from Windows"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by PapZ[ITA] on 2006-01-21
Hi people,

I've just tried out Ubuntu Live on my laptop and I've felt something like "whoo". Astonishing.
Now, some questions before I take care of switching from Windows on my desktop PC. Sorry for not posting every single question in a dedicated thread, but it would take too long. Maybe, we could delete all after. It's up to admin.

I have an AMD64 3000+, Gigabyte K8NS mobo, Ati Radeon 9600 256mb ddr, 2 SATA hdd Maxtor (200 and 80gb), Sound Blaster 24-bit live!, 1gb (512x2) ddr 400mhz, Scanner HP scanjet 2400 (usb), printer Lexmark Z45 (usb), burner Pioneer DVR-109, and a DSL modem  Zyxel 630-C (usb), keyboard logitech radio controlled with many function buttons (will they work on Ubuntu?), and a Logitech MX 700 wireless mouse (same question).
In addition, this pc is acting like a server on a miserable 2 pc's LAN (this one and  my brother's one in the next room :P). He deserves to remain on its sucking windows pc, and the first question is about that:

1 - Is it possible to setup a LAN between UBUNTU and Windows XP?

2 - How to setup a DSL internet connection with that usb modem (PPPoATM, I think)?

3 - Do you know any known issue with those peripherals I listed?

As you probably noticed, I'm such a Linux lamer, and — as lamer's habit — I'm quite unsure about...err...ALL.

Could you help me? I've figured out you all are very kind people; I hope I won't abuse of your patience. 

Thank you in advance,

Francesco

P.S.: Sorry for my English, I'm a stupid italian.

---

### Post by AndyCooll on 2006-01-21
1 - Is it possible to setup a LAN between UBUNTU and Windows XP?
**Yes it is, you'll need to install Samba, smbfs and configure. There are a number of excellent HOWTO's on these forums which will explain that**

2 - How to setup a DSL internet connection with that usb modem (PPPoATM, I think)?
**It is more than likely that your Internet connection will be automatically found when you do an install**

3 - Do you know any known issue with those peripherals I listed?
**Sorry, I can't answer this one for certain. There doesn't seem to be anything there that will cause any issues as far as I'm aware**

:cool:

---

### Post by public_void on 2006-01-21
3. If you try the live CD and see if all your hardware works, there should be any problems.

---

### Post by PapZ[ITA] on 2006-01-21
Thank you guys,

I tried ubuntu Live, and amazing discovered that I can browse the other pc, and send/receive files from it!
Unfortunately, I wasn't able to get my modem work. The DSL (signal) led wasn't blink or other. Just doesn't appear :(
My question is: do I need a driver? I mean: does Ubuntu work like windows, with driver for peripherals that aren't recognized from the system?
Sorry if I bother you with lamer questions, but I don't know anyone (but you) that uses a Linux OS.

Francesco

---

### Post by ysse on 2006-01-21
Hi Francesco, 
I also have an ATI 9600 graphics card, and had no problem with the live CD, but when installing I had to use the option vga=771, or else the screen just went blank. Don't worry though,  there is help about that to get from the install screen. Not really more difficult than running a Windows installer.

Good luck

Anders

---

### Post by rubinstein on 2006-01-21
Hi Francesco!

[QUOTE='PapZ[ITA]']
2 - How to setup a DSL internet connection with that usb modem (PPPoATM, I think)?[/QUOTE]
I searched a bit, and I think the modem should work - but it is difficult to install. Can't help you more...

Read these links:
[http://ubuntuforums.org/showthread.php?t=85852](http://ubuntuforums.org/showthread.php?t=85852)
[http://dsl.linux.it/ChipsetConexantUsb](http://dsl.linux.it/ChipsetConexantUsb)

This is the driver:
[http://accessrunner.sourceforge.net/index.shtml](http://accessrunner.sourceforge.net/index.shtml)

This may also help you:
[http://wiki.gentoo-italia.net/index.php/Conexant_Accessrunner_USB_e_Gentoo_Linux_2.6](http://wiki.gentoo-italia.net/index.php/Conexant_Accessrunner_USB_e_Gentoo_Linux_2.6)
[http://siracusa.linux.it/doc/conexant.htm](http://siracusa.linux.it/doc/conexant.htm)

---

### Post by dueY on 2006-01-21
[QUOTE=public_void]3. If you try the live CD and see if all your hardware works, there should be any problems.[/QUOTE]

Seconding this. The only hardware I have that you have is the mx-700 and the soundcard and they work fine.  I could go test a Logitech wireless keyboard in the other room if you REALLY want me to :p

---

