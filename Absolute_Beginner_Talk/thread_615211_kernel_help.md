---
title: "kernel help"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-16
ive built 2 custom kernels now and neither of them have a wireless option in network admin!

first time i fiddled with the Network options on the kernel, so i though that was the problem.
options i had:

    * Dial Up Modem


the second time i didnt touch anything to do with netyworking and still NO wireless option.
options i had:

    * Wired
    * Dial Up Modem


hmm.

is there something i need to add in to make it availble?
perhaps tick a box as M.

i saw somethuing mention about "pocket and portable adaptors" is that anytrhing?

ive wasted many hours on this and quite frustrating.

any help is appreciated.

Greetz Scott

---

### Post by 5-HT on 2007-11-16
Could be that the module for your card isn't loading. Can you load it manually or was it not built? Can you see the device in ifconfig and bring it up?
What card is it? There has been some shuffling of the options lately (perhaps HID support needs to be enabled).

In terms of kernel config, best to play it safe and add support for both the new (mac80211) and old networking stacks unless you know which one the module needs:
```
Networking --->
    -> Wireless
        <M> Improved wireless configuration API
        <M> Generic IEEE 802.11 Networking Stack (mac80211)
        <M> Generic IEE 802.11 Networking Stack
        <M> IEE 802.11i CCMP support
        <M> IEEE 802.11i TKIP encryption
        <M> Software Mac add-on to the IEEE 802.11 networking stack 
```You can always take things out that you don't want, but the above should cover most needs.

After that it's just a matter of getting the proper module up and running. If it's available in mainline it's a trivial matter:
```
Device Drivers --->
    -> Network device support
        -> Wireless LAN
        
[*] Wireless Lan (IEEE 802.11)
        <M> select appropriate driver
```If your card is not supported in mainline you'll need to install the driver manually or patch the kernel for it.
cheers,

---

### Post by Mikecore on 2007-11-16
When your building a kernel you need to understand what your doing you can either build a driver for wireless card into the kernel or you can build it as support and then insert a module or driver. You need to do some reading on how to compile a kernel. Go over to Gentoo and read its hand book about kernels its pretty clear and should be able to help you.

---

### Post by skymera on 2007-11-17
i have the driver for my card but it works out of the box :)

i will read up,
so what needs tyo be done, since mine is out of the box?

becuase i didnt get a wireless option nor didi it detect my hardware even when i didnt touch network :(

---

### Post by Mikecore on 2007-11-17
> **skymera said:**
> i have the driver for my card but it works out of the box :)

i will read up,
so what needs tyo be done, since mine is out of the box?

becuase i didnt get a wireless option nor didi it detect my hardware even when i didnt touch network :(

If it works out of the box use the "lsmod" command and see which driver it is using. then either built support for it in the kernel or build the kernel with modular suppor thats the "M" option you where talking about when you build it in its the "*" option. I'm not sure about ubuntu but with the amount of hardware that does work out of the Box it probably builds the kernel with "M" options for most things 
and just loads the kernel modules its needs. So I would probably do the same thing if your building your own kernels. Because if you build it into the kernel and a update comes out it may or may not work with your current driver.  you would have to rebuild your kernel after a update. ( if wireless broke because of a driver issue ). so building a kernel modular is beter for what your doing.  

Why exactly do you need a custom kernel?

---

### Post by skymera on 2007-11-17
i installed the driver in ndiswrapper :)

but in network admin i only have choice of dial up,even when i enabled as many wireless things as i could.

is there a module i can load?

sudo modprobe ______?

---

