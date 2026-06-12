---
title: "Ubuntu on ~NEW~ MacBook"
date: 2007-11-08
forum: Apple Intel Users
---

### Post by cleentrax on 2007-11-08
UPDATE: ACK! I can't get anything else working. 

[B]No touchpad luck 
[/B]
Changes to Xorg.conf don't make any difference. Gsynaptics won't load. If I set the Synaptics to be the core pointer, X won't start, claiming there is no Synaptics device. So I can't get scrolling or tapping to work.

**No Wifi Luck**
I have tried ndiswrapper, and I have tried installing bcm43xx firmware. I can't get the wireless to show up at all. LSPCI reveals it as a Broadcom 4328.

**No Sound**
I haven't fooled too much with this one yet, but sound doesn't work for me.

++++
I have a new 2.2ghz MacBook, the one with the SantaRosa architecture, including the new integrated video. I have upgraded the RAM to 4gB.

So far, I have done the following...

1. Used Boot Camp to resize the Leopard partition
2. Installed rEFIt
3. Installed 64-bit version of Ubuntu Studio 

Everything is going very smoothly so far. It is my goal to use Ubuntu for day-to-day use, and for audio/video production, and to use OSX for web design. (The Linux design apps just aren't mature enough yet).

Some questions:

1. Anyone get Compiz working yet on the MacBook with X3100 video?
2. Can I use some sort of VM (Fusion, Parallels, etc.) in Leopard to access my 64-bit Ubuntu partition, or will I have to boot into it to use it?

---

### Post by cyberdork33 on 2007-11-08
accessing your linux partition with vmware is not really easy:
[http://smithii.com/node/88](http://smithii.com/node/88)

I am assuming you have an ATI graphics card. I don't know that ATI's proprietary driver supports your card yet. This likely means no 3D acceleration, and thus no Compiz.

---

### Post by cleentrax on 2007-11-08
It's a MacBook, so it has integrated video. The new ones have the X3100. Thanks for the VM link.

---

### Post by cyberdork33 on 2007-11-08
> **cleentrax said:**
> It's a MacBook, so it has integrated video. The new ones have the X3100. Thanks for the VM link.
So Intel Graphics.

Should work. Intel has open drivers. If you have 3D acceleration, you just have to enable effects from the appearance menu.

---

### Post by addicted44 on 2007-11-08
Congratulations.  I got a new macbook like you did too, and installed Ubuntu 7.10 and its running great.  However, do you know how to get the Wireless working on it?  Any help will be greatly appreciated.

Thanks

---

### Post by cleentrax on 2007-11-08
> **addicted44 said:**
> Congratulations.  I got a new macbook like you did too, and installed Ubuntu 7.10 and its running great.  However, do you know how to get the Wireless working on it?  Any help will be greatly appreciated.

Thanks

[URL="https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688"]
New MacBook Wireless Guide[/URL]

Short story, you'll need to hook up via ethernet and install madwifi, because the latest MacBook wireless drivers are proprietary, and not yet supported by Linux without madwifi.

I haven't tried it yet. First task when I get home tonight.

---

### Post by addicted44 on 2007-11-08
> **cleentrax said:**
> [URL="https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688"]
New MacBook Wireless Guide[/URL]

Short story, you'll need to hook up via ethernet and install madwifi, because the latest MacBook wireless drivers are proprietary, and not yet supported by Linux without madwifi.

I haven't tried it yet. First task when I get home tonight.

Thanks for the quick response.  However, the wireless chipset is not Atheros at all, but rather a Broadcom BCM4328 (rev 03) chipset.  Will this work with this chipset too?  (Note:  I have the 2 GHz Macbook)

---

### Post by cyberdork33 on 2007-11-08
> **addicted44 said:**
> Thanks for the quick response.  However, the wireless chipset is not Atheros at all, but rather a Broadcom BCM4328 (rev 03) chipset.  Will this work with this chipset too?  (Note:  I have the 2 GHz Macbook)

You probably want to use ndiswrapper. It is the same card I have in my iMac.

---

### Post by NightCrawler03X on 2007-11-08
> and to use OSX for web design. (The Linux design apps just aren't mature enough yet).
Text editor?
Real web designers use a text editor, and a few languages they know, usually HTML/XHTML, Javascript, and (now) usually CSS.

Emacs has been around for a very long time my friend.

---

### Post by cleentrax on 2007-11-08
> **NightCrawler03X said:**
> Text editor?
Real web designers use a text editor, and a few languages they know, usually HTML/XHTML, Javascript, and (now) usually CSS.

Emacs has been around for a very long time my friend.

I am a "real" web designer, whatever that means. The tools I'm primarily talking about are Flash and Photoshop (for design work). For coding, my favorite three text editors all happen to be Cocoa apps (BBEdit, Smultron, Coda), as do my two favorite FTP apps (Transmit, Cyberduck).

---

### Post by dmber on 2007-11-08
afaik, the X3100 is blacklisted for CF.

---

### Post by Levo75 on 2007-11-08
> **cyberdork33 said:**
> You probably want to use ndiswrapper. It is the same card I have in my iMac.

Can you help me with this?

I still havent got this working in my iMac.

I installed Ndiswrapper multiple times with different toturails.

Broadcom BCM4328

---

### Post by addicted44 on 2007-11-08
> **dmber said:**
> afaik, the X3100 is blacklisted for CF.

What do you mean by CF?

I tried NDISwrapper, but it did not work.  Actually, besides lspci and lshw, pretty much no other tool even detects my wireless card.  (I tried ifconfig, cat /etc/network/interfaces, iwconfig etc...)

Thanks

---

### Post by addicted44 on 2007-11-08
I should probably start a new thread...I am about to do that...

---

### Post by dmber on 2007-11-08
CF = compiz fusion.

---

### Post by cyberdork33 on 2007-11-08
> **Levo75 said:**
> Can you help me with this?

I still havent got this working in my iMac.

I installed Ndiswrapper multiple times with different toturails.

Broadcom BCM4328

Use this driver in ndiswrapper:
[ftp://ftp.us.dell.com/network/R151517.EXE](ftp://ftp.us.dell.com/network/R151517.EXE)

should work for 32bit and 64bit clients

---

### Post by cleentrax on 2007-11-09
Well, I spent three hours tonight trying to get sound and wifi working on my MacBook. No luck with either.  I tried numerous, contradictory tutorials, and only succeeded in making things worse. Now Ubuntu won't even boot. It hangs up on network settings.

I think I'll start from scratch with 32bit version.

---

### Post by JordiMac on 2007-11-09
As the sound typed in the MacBook ?

---

### Post by JordiMac on 2007-11-10
I have no sound in my MacBook Santa Rosa help thanks

---

### Post by pyre on 2007-12-03
> **dmber said:**
> afaik, the X3100 is blacklisted for CF.

Why would it be blacklisted?  And where did you get this from?  A quick google search turned not much up on the issue.

---

### Post by cyberdork33 on 2007-12-03
> **pyre said:**
> Why would it be blacklisted?  And where did you get this from?  A quick google search turned not much up on the issue.
Here are the blacklisted PCIIDs in /usr/bin/compiz:
```
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
```It does not mention the X3100 specifically, but does have the X3000 which is also the Intel 965 chipset. Here are some other PCIIDs that are blacklisted as well. [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

This command will give you your PCIID:
```
lspci -nn |grep VGA
```

---

