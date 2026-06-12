---
title: "wireless woes D-Link DWL-610 for Feisty"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by bookbinder on 2007-05-14
Hello. I am new. I have fruitlessly been searching and trying to get my wireless card recognized and going.

I have installed Feisty from a downloaded cd iso on a Toshiba Satellite 2450 laptop.

In Terminal, ran
    lshw

which listed the following, which I believe to be associated with my wireless card

 *-network UNCLAIMED
          description: Ethernet controller
          product: DWL-510 2.4GHz Wireless PCI Adapter
          vendor: D-Link System Inc
          physical id: 0
          bus info: pci@03:00.0
          version: 20
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0 maxlatency=64 mingnt=32
          resources: iomemory:3c000000-3c0001ff irq:11


I do not know what to do next. I tried downloading and installing ndiswrapper but hit a wall, so please start from the basic info above and assume I know nothing.

with much gratitude to whoever helps me escape Windows oppression

---

### Post by bookbinder on 2007-05-14
Further info. Ran the following in Terminal

lspci -v | less

which yielded the following:

03:00.0 Ethernet controller: D-Link System Inc DWL-510 2.4GHz Wireless PCI Adapter (rev 20)
        Subsystem: D-Link System Inc DWL-510 2.4GHz Wireless PCI Adapter
        Flags: medium devsel, IRQ 11
        I/O ports at c400 [disabled] [size=256]
        Memory at 3c000000 (32-bit, non-prefetchable) [disabled] [size=512]
        Capabilities: [50] Power Management version 2

---

### Post by ugm6hr on 2007-05-18
I have the same WLAN card (D-Link Air DWL-610)), and am having a bit of a night mare installing it on Xubuntu7.04 (Feisty) too.  The laptop involved is a Dell Inspiron 5000e (which I had anightmare sorting out the resolution and refresh rates).  As you have demonstrated with your lspci, the card is recognised as being present (although as DWL-510 rather than DWL-610!).  I am certain this works with ndiswrapper (I have used it with PuppyLinux).  So I installed "ndisgtk" from the Synaptics Package Manager, which automatically installs "ndiswrapper-common" and "ndiswrapper-utils-1.9" (actually, I don't have wired connection on that laptop - so had to download them all from [http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk) and further links from there).

ndisgtk makes installing ndiswrapper with the appropriate XP driver (as worked with PuppyLinux) easy.  A reboot following this stage allowed me to connect via WEP128-bit using the "Network" interface, albeit having to manually enter the ESSID.  Using this connection, I then used "Add/Remove..." to install "Network Manager", which recognised the network immediately, and also allowed me to connect with either WEP or WPA Personal/TKIP.  Great...

Except, the laptop has a dual-boot with Windows XP SP2, which I have recently reinstalled.  The next time I booted into XP, and it downloaded about 13 updates, and the next time I booted into XP, there was an error message saying that Windows had successfully recovered some configuration file (I can't recall the exact words unfortunately).

Since then, neither of the lights on the PCMCIA card light up until XP has fully loaded (which was not the case previously).  And unfortunately, they never turn on in Xubuntu at all now (they used to flash constantly before).  Now ndisgtk seems to think that the Hardware is not present (even when it's plugged in either at switch-on, or following Xubuntu boot).  And "Network" can't see any ethernet interfaces (there aren't any others).

So I am convinced that an XP update has done something unusual, but I can't work out why that would have an effect in Linux.  Am trying to sort it out too...

---

### Post by ugm6hr on 2007-05-19
Bizarre.  I found a link on the ndiswrapper website which suggested that the Realtek driver works better than the Dlink one, provided you make a few adjustments to the .inf code.  So did that, and it seemed to install via ndisgtk this time.  However, it didn't work.  So reinstalled the Dlink driver again, and it now works again.  But only with WEP.  Not WPA.

I don't understand.  But at least I'm back online.

---

### Post by jcsewell on 2007-05-20
I'm considering buying this card (ebay) and did a little research.  According to [http://support.dlink.ca/products/view.asp?productid=DWL%2D610](http://support.dlink.ca/products/view.asp?productid=DWL%2D610) the card is 802.11b and only 128 bit WEP, no WPA is mentioned which I assume means not supported.  Glad to know it can work in Ubuntu, however...


-James

---

