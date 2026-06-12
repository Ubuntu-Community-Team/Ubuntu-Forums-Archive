---
title: "Setting up networking"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by moxiot on 2007-03-19
hi there ubuntu drinkers
i have succesfully installed my drivers for the dreaded broadcom wireless card. my problem is, and it's driving me crazy, that i don't know what the heck to do next. ok, ndiswrapper tells me that the drivers are installed and that the hardware is present. ok, good so far. then i go to system>administration>networking and a wi-fi card shows up there. my problem is when i hit configure and it asks me for my essid or ip, for the life of me i dont know what to enter!!.
 i don't have a network, i mainly use my laptop at school and at some cafes so i dont have a connection at home. what should my essid be? should i enter my ip address there also, and the subnet?

please i know this has to be the simplest aswer but i have looked everywhere.

---

### Post by schwascore on 2007-03-19
Try this program.

```
sudo apt-get install wifi-radar
```

It displays all ESSID's from all wifi stations within reach.  Just be aware that ESSID's with a lock next to them are encrypted and need a key.

If you have a wireless router of your own and you do not know the ESSID, you need to configure the router.  Check it's manual or google the router name for help.

Additionally, most home networks use DHCP which automatically assigns IP addresses to computers.  You should try that setting first before worrying about static IP addresses.

---

