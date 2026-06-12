---
title: "Broadcom Wireless Adapter Disconnections"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by franfran on 2008-01-02
hey there guys,

well it seems like when i am connected wired on my hp laptop, i have no problems with the internet. however when i use the wireless card, it disconnects me at random times which range from 5 min - 1 hr of use. sometimes when it disconnects, it doesnt even reconnect.

some info about my computer: hp pavilion dv6000. its a BCM94311 card. also, i used the restricted firmware and enabled it using fwcutter in order to be able to use the wireless card. i have read some notes about the ndiswrapper, is that a better alternative and do you guys think i should transfer over and will it help with the d/c's?

also i am running an amd 64, using the 64 ubuntu OS. im not sure but i also read no one is sure if it works on the 64 version yet.

any thoughts? and good guides? all the guides ive seen are way beyond my head as im just starting out.

thank you.

---

### Post by Coombabah on 2008-01-02
I'm having the same problem with the bcm94311 on a fresh install of gutsy using the restricted firmware fwcutter and the same downloaded file.

I have a previous upgrade of feisty to gutsy in another partition that works OK with the same restricted firmware.

My hardware is a Lenovo 3000 c200 laptop.

---

### Post by theproc64 on 2008-01-03
I used to use the broadcom driver (bmxx) and I would get very bad reception (I had to be right next to the router).  I installed ndiswrapper using this tutorial [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc) and now it works perfectly..  Its probably worth a try.

---

### Post by Coombabah on 2008-01-11
> **theproc64 said:**
> I used to use the broadcom driver (bmxx) and I would get very bad reception (I had to be right next to the router).  I installed ndiswrapper using this tutorial [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc) and now it works perfectly..  Its probably worth a try.

Tried that too.

Just tried installing 8.04 alpha-2 and using the b43 but it still disconnected

Tried the steps in this thread but no luck.
[http://ubuntuforums.org/showthread.php?t=649038](http://ubuntuforums.org/showthread.php?t=649038)

It initially shows good signal strength with iwconfig but after a minute or so there is no signal and it doesn't come back until the next boot.

The odd thing is that it still works on an old install of Feisty upgraded to Gusty in a different partition.

Giving up on the internal 4311 for now and using a netgear wg511t pcmcia card instead.

---

### Post by eolson on 2008-01-11
I finally gave up on the broadcom.  I had it working, but the signal strength was lacking.  Went to Wal-mart and bought a
   "Belkin Wireless G  USB Network Adapter"
CD with the drivers is in the box
copied the driver over to my desktop
installed it with ndiswrapper
got a error message saying invalid driver, which I ignored
Works perfect with much better signal strength.

You do have the hassle of the sepearte piece of hardware,  but it's barely larger than a usb stick.

I like it.

---

### Post by Coombabah on 2008-04-10
My  Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) is working again using the B43 driver on the latest Hardy updates. 
It is working very reliably at 1MB/s

---

### Post by Coombabah on 2008-04-25
> **Coombabah said:**
> My  Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) is working again using the B43 driver on the latest Hardy updates. 
It is working very reliably at 1MB/s

It was reliable for a couple of days and died again.

Did a fresh install of the final Hardy and it is still broken :(

It worked for a few seconds using ndiswrapper then couldn't be coaxed into working again.

Perhaps my BCM94311MCG has an intermittent fault.

---

