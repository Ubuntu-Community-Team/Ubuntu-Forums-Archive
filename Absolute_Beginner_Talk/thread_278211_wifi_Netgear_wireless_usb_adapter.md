---
title: "wifi Netgear wireless usb adapter"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by blkdragon on 2006-10-15
hey im running a Toshiba Portege 7020CT, PII 366Mhz, 128Mb Ram system, on ubuntu 6.06 with Xfce, and im wondering what packages i would need to have wireless working through my wireless Netgear Usb adapter, in addition to the normal netgear ones.

I also have a few questions:

1. can my system run it?

2. does having USB 2.0 have any significant advantages?

3. IN Australia, would i need any other special equipment?

4. a friend said that a wireless PCMCIA card would work better. is this true?

5. would i be able to browse the net free?

6. whats the difference between wi-fi and wireless internet?

7. can you install windows drivers, knowing the root password, without using wine?

8. can you think of any other problems i may have?

You help is greatly appreciated. Im going away to a rural(tamworth) area and i need to stay in touch with the rest of the world.

thanks again, blkdragon.

---

### Post by paul6 on 2006-10-16
Edit: Nevermind my original post, seems I misunderstood. Do a forum search on "wg111" for help installing the Netgear USB Adaptor. One of the threads provides complete directions on how to install it using ndiswrapper and ndisgtk.

---

### Post by capn_hector on 2006-10-16
> **blkdragon said:**
> hey im running a Toshiba Portege 7020CT, PII 366Mhz, 128Mb Ram system, on ubuntu 6.06 with Xfce, and im wondering what packages i would need to have wireless working through my wireless Netgear Usb adapter, in addition to the normal netgear ones.

I also have a few questions:

1. can my system run it?

2. does having USB 2.0 have any significant advantages?

3. IN Australia, would i need any other special equipment?

4. a friend said that a wireless PCMCIA card would work better. is this true?

5. would i be able to browse the net free?

6. whats the difference between wi-fi and wireless internet?

7. can you install windows drivers, knowing the root password, without using wine?

8. can you think of any other problems i may have?

You help is greatly appreciated. Im going away to a rural area and i need to stay in touch with the rest of the world.

thanks again, blkdragon.


1. your system could probubly run it

2. usb 2.0 realy does not have any advantages depending on what your doing, if you arnt using a external hdd, any usb will suffice

3. you dont need any special equipment.  the wifi standards are world wide

4. possibly, depends on what sort of card you get (what chip set)

5. you would be able to browse the net for free if you go to a place that runs a free access point

6. wifi and wireless internet are the same sort of, most of the time they refer to 802.11 standards, where wireless internet can also be special cards that use the cellular networks.

7. you cant use windows drivers even with wine

8. if you get a card with an athros or prism2 chipset then you should be fine.  most linux distros (including ubuntu) have drivers for those 2.

---

### Post by blkdragon on 2006-10-16
> **capn_hector said:**
> 1. your system could probubly run it

2. usb 2.0 realy does not have any advantages depending on what your doing, if you arnt using a external hdd, any usb will suffice

3. you dont need any special equipment.  the wifi standards are world wide

4. possibly, depends on what sort of card you get (what chip set)

5. you would be able to browse the net for free if you go to a place that runs a free access point

6. wifi and wireless internet are the same sort of, most of the time they refer to 802.11 standards, where wireless internet can also be special cards that use the cellular networks.

7. you cant use windows drivers even with wine

8. if you get a card with an athros or prism2 chipset then you should be fine.  most linux distros (including ubuntu) have drivers for those 2.

7. what about ndiswrapper? apparently that "wraps" the windows drivers, and makes them linux compatible.

---

### Post by Weedman on 2006-10-16
Ndiswrapper is special, and basically does what you said.

It is a 'wrapper' for the Windows drivers, though it might take some fiddling to get working. I haven't tried it myself, so I can't really comment.

weed

---

