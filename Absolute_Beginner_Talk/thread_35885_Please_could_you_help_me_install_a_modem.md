---
title: "Please could you help me install a modem?"
date: 2005-05-20
forum: Absolute Beginner Talk
---

### Post by Trevor 42 on 2005-05-20
Hello All,
I would be very grateful if some one could help me install a modem (internal or external) on my PC.

Here are some specs Pentium II, AT motherboard (unknown manufacturer and vintage) with intel chipset north & south bridge, 4 x PCI slots (no.2 has graphics card in), 2 x ISA slots, 1st IDE =10Gb Fujitsu hard drive (with the latest Ubuntu release installed as the only operating system)   2nd IDE = CD-R, no slaves on either IDE bus.

I purchased a Hayes Accura 56K internal speakerphone/FAX ISA modem  which says it is unix/linux compatable on the box and has jumpers etc on the board. I also have  an external BCM 56K fax modem which states it is Linux compatable on the box.

I have had one or two problems so far with Ubuntu, mainly that on installing it would not recognise any keystrokes when it ask me to enter a password - except number keys, so I set a numeric password. However although it allows me to access root it will not accept this password in terminal -once again it is not recognising any keys (including numbers in this instance)

I have to say much as I would love to use Linux instead of Windows my experiences so far have not endeared it to me (I've tried Mandrake as well and ended up having to keep buying new hardware (particularly mice) to get it to work at all). Therefore any help would be gratefully received.

I am a reasonably advanced user with microsoft systems - but please go right back to basics with me on this issue (eg. take modem in right hand etc.) as a lot of what I read you guys saying may as well be in another language.

Anyway - thanking you in advance for reading this and hopefully finding a solution so I can ditch windows (which I am not keen on due to the need for registration etc.).

Thanks,

Trevor

---

### Post by jasmuz on 2005-05-20
[QUOTE=Trevor 42]Hello All,
I would be very grateful if some one could help me install a modem (internal or external) on my PC.

Here are some specs Pentium II, AT motherboard (unknown manufacturer and vintage) with intel chipset north & south bridge, 4 x PCI slots (no.2 has graphics card in), 2 x ISA slots, 1st IDE =10Gb Fujitsu hard drive (with the latest Ubuntu release installed as the only operating system)   2nd IDE = CD-R, no slaves on either IDE bus.

I purchased a Hayes Accura 56K internal speakerphone/FAX ISA modem  which says it is unix/linux compatable on the box and has jumpers etc on the board. I also have  an external BCM 56K fax modem which states it is Linux compatable on the box.

I have had one or two problems so far with Ubuntu, mainly that on installing it would not recognise any keystrokes when it ask me to enter a password - except number keys, so I set a numeric password. However although it allows me to access root it will not accept this password in terminal -once again it is not recognising any keys (including numbers in this instance)

I have to say much as I would love to use Linux instead of Windows my experiences so far have not endeared it to me (I've tried Mandrake as well and ended up having to keep buying new hardware (particularly mice) to get it to work at all). Therefore any help would be gratefully received.

I am a reasonably advanced user with microsoft systems - but please go right back to basics with me on this issue (eg. take modem in right hand etc.) as a lot of what I read you guys saying may as well be in another language.

Anyway - thanking you in advance for reading this and hopefully finding a solution so I can ditch windows (which I am not keen on due to the need for registration etc.).

Thanks,

Trevor[/QUOTE]
 Hello.

I would recomend you install the external BCM modem.
There is a list about compatible modems at [http://www.linmodems.org](http://www.linmodems.org)
when you connect it to the computer, via the serial cable..do the following:

Login
Terminal...type pppconfig
there you will fill out the information about your dialup connection
and finally it will autodetect the modem, if not you will have to verify wich COM port is using.

I use a US Robotics 56k External Message Modem.
what keyboard are you using..

---

### Post by Trevor 42 on 2005-05-21
Thanks,

I can't login to terminal as it wont recognize my password - although it does recognise the keyboard (which is a standard UK layout AT keyboard) when I hit ENTER.
 
It does let me login as root - recognises keyboard/keystrokes/password, no problem.

Thanks,

Trevor

---

### Post by Trevor 42 on 2005-05-21
By the way I forgot to add; How do I know (or find out)which COM port I am using?

Another question.

On the external serial modem there are two (serial) connections that go to the PC, one larger than the other and both female, do I need to connect both of them? 

Thanks,

Trevor

---

### Post by stevenyu on 2005-05-21
[QUOTE=Trevor 42]
Another question.

On the external serial modem there are two (serial) connections that go to the PC, one larger than the other and both female, do I need to connect both of them? 

[/QUOTE]

Nope, just the standard RS-232 serial plug, you don't need the old printer port like serial at all.

---

### Post by Trevor 42 on 2005-05-21
Progress report.

I have now managed to get to PPP configuration utility.

Don't want to go any further until I know which of the two serial connectors (long one or short one) to plug in the back of the PC. On the back of the modem you can only use the short one so that is already attatched. If anyone could advise me I would be grateful.

Trevor

---

### Post by Trevor 42 on 2005-05-21
Thanks to the person who has advised me about the serial plugs.

Trevor

---

