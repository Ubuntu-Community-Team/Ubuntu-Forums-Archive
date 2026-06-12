---
title: "Coming back to Ubuntu, installing on microSD errors"
date: 2017-06-28
forum: Apple Hardware Users
---

### Post by Donnut on 2017-06-28
Hi, I'm posting in the newbies 'cause I'm a born again newbie. Haven't really used Ubuntu in ten+ years. I'm trying to install on my MacBook with Mac OS X and Windows 10 already on the SSD, so I'm using a 256gb SD card. Every time I try to format it I get multiple errors including "backup GPT table corrupt". how can that be and how do I fix it? I have had a heck of a time trying to format this card in OS X, Windows, and Linux.

---

### Post by QIII on 2017-06-28
*Moved to **Apple Hardware Users*** for a better fit.

---

### Post by oldfred on 2017-06-28
I do not know Mac.

But post this, but Mac may use different devices?
sudo gdisk -l /dev/sda

If not /dev/sda
sudo parted -l

---

### Post by johndough2 on 2017-06-29
Hi

The usual answer is

Format the card to FAT32 in a digital camera if possible.

Otherwise I can only think that the SD card has a problem in itself.  If not then...

The address/location of the card is wrong.

I think dd  [https://linux.die.net/man/1/dd](https://linux.die.net/man/1/dd) may help.  I have used an SD with a Raspberry Pi using dd on my imac.
The command line is tricky initially, but not too arcane.
[https://www.raspberrypi.org/documentation/installation/installing-images/linux.md](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md) - 
dd bs=4M if=2017-06-21-raspbian-jessie.img of=/dev/sdX

[https://askubuntu.com/questions/388037/how-to-create-an-img-file-from-iso-on-ubuntu](https://askubuntu.com/questions/388037/how-to-create-an-img-file-from-iso-on-ubuntu)


So please take some steps forward and ask for more help as you progress if you need to.

---

### Post by Autodave on 2017-06-29
If you cannot format it on anything, I think that it is time for a replacement. Sounds like card is dead.

Do any of the OSs recognize it when you plug it in? And, do they recognize the size of it?

---

### Post by Donnut on 2017-07-10
The card seems to be mostly dead. I formatted it using Ubuntu, then Mac, then Windows. They all format it, copy things to it, then when I restart the computer, it's corrupt. I just installed it on my SSD via tripleboot and it runs oh so much faster than on an SD anyway.

---

### Post by Bucky Ball on 2017-07-10
> **Donnut said:**
> I just installed it on my SSD via tripleboot and it runs oh so much faster than on an SD anyway.

:) That it would. An SD is good for a Raspberry Pi, but ...

If you're happy, please mark the thread solved to help others using Thread Tools (even though your original problem wasn't solved, rather resolved and it does sound like a dodgy card).

---

