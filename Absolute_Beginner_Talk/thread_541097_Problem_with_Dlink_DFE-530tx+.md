---
title: "Problem with Dlink DFE-530tx+"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Ironbird on 2007-09-02
I just bought a Dlink DFE-530tx+ NIC for my computer running ubuntu 7.04.  It's not being picked up under network.  From what i've read it should be compatible with ubuntu out of the box. 

I "tried" to install a driver for it but i have very little experience with linux command line and have no idea how to compile files.  any help will be greatly appreciated.

---

### Post by nonewmsgs on 2007-09-17
OK, let's see what we can do.  i would like to have the chipset of the card first, so can you please give the output of 

```

lspci

```

---

### Post by Kypdurron5 on 2007-11-06
> **nonewmsgs said:**
> OK, let's see what we can do.  i would like to have the chipset of the card first, so can you please give the output of 

```

lspci

```
[Note: I'm assuming my problem is the same as with the OP]

It uses the Realtek 8139 chipset, and should be compatible out of the box using driver 8139too.  I'm having a problem with this card too, although I KNOW I had some version of linux running on that computer (with the same card) out of the box about a year ago.  The drivers are supposed to be included with the Kernel, and the lspci -v command does find the card by name (and says it's eth0).  However, the MAC address is listing as ff:ff:ff:ff:ff:ff, and it doesn't even pretend to connect to my router.  I've searched the internet high and low for a solution over the last 5 hours and I haven't made any progress.  I just installed Fedora in hopes it might make a difference, but the problem remains.  Everything was working perfectly under Windows, so I'd have rule out hardware problems, but I did see an article somewhere suggesting that Windows might write something to the NIC's EEPROM that binds it to Windows and prevents it from being used with Linux.  That doesn't seem likely...but I'm starting to wonder.

---

