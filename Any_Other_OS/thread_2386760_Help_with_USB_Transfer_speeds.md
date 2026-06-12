---
title: "Help with USB Transfer speeds"
date: 2018-03-10
forum: Any Other OS
---

### Post by allaboutgadgets on 2018-03-10
Now, I’m using Tails OS. Not sure of the difference of Ubuntu but most things are similar. Anyway, I am running Tails OS from a usb stick so that’s how I boot up the OS on a MacBook Air. I have a file that I have to transfer from time to time over 40gb. Now to transfer this file I use a fast memory card. The first couple of times I’ve done it it seemed to go pretty fast, but now I will get about 19MB a second up until 700mb-1gb then it will drastically slow down to 700kb-1mb a second. This will take forever for a file that’s about 46gb in size. Is there something I’m doing wrong, or something that I can check? I have tried transferring with a fast CF card, and a fast SD card with the same results. These are hooked up to a card reader while the OS is boot from a usb stick directly in the computer. Any help would be greatly appreciated. Thank you!

---

### Post by wildmanne39 on 2018-03-10
*Thread moved to **Any Other OS, a more appropriate forum**.*

---

### Post by TheFu on 2018-03-10
Storage transfer speeds is mostly dependent on the performance for the storage, but also it is dependent on the bus, the controller and the way that the storage is connected.
USB1 is very slow.
Old CF is slow.  New CF claims 400Mbps, but I've never seen this. SDXC isn't the same.
USB2 claims to support 480Mbps, but in the real world it is usually closer to 20Mbps. USB2 storage devices were designed with older/cheaper/slower tech.
USB3+ claims to support 5Gpbs, but in the real world it is 100% dependent on the storage media used. USB2 storage connected to USB3 ports will only get 20-40Mbps.  USB3 flash storage is usually in the 60Mps-120Mbps range.  SSD-based storage connected via USB3 will be 160Mbps+ and up.  A fast spinning disk in a USB3 enclosure, connected to a USB3 port should get about 100-130Mbps.

All of these will use RAM as disk buffers, until the available RAM runs out. Then the  performance is limited to the storage speeds only.  That's why you see the initial high speed xfers. It is using RAM.

And don't forget that networking will almost always be faster than USB2 speeds.  20Mbps is slower than a wired 100base-tx connection to another machine with better/faster storage.

I looked up what a Macbook Air has. Forget the wireless networking. It will never touch the USB3. My chromebook is similar, but I connect a USB3-to-GigE adapter and see 920Mbps transfers.  I've also connected cheap SSD storage ($20 USB3 external + cheap Kingston 16G m.2 2242 SSD) to the USB3 port and see ... using bonnie++ .... 
```

Version      1.97   ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
cb35          7624M   632  99 19044   1 18175   2  1426  99 233935  12  7563 105
Latency             18690us    4868ms    2970ms   10643us    3610us   63826us
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
files:max:min        /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
cb35             16 28913  29 +++++ +++ +++++ +++ 30644  30 +++++ +++ 24778  18
Latency               949us     818us    2210us    1868us      28us     35us 

```
Not very impressive. Cheap controllers matter.

Always use USB3 when possible with the fastest storage available.

---

### Post by allaboutgadgets on 2018-03-10
Problem lies that I’m going usb to usb as I can’t use the internal hard drive. Everything must remain on the OS on the USB. Is there any way to somehow get a local connection setup between my Mac with the original file and just transfer it over the air like that. I’m sure 30 or so MBPs is much faster than what I’m getting now. I just can’t seem to find a way to link the two even though they are both on the same WiFi network

---

### Post by TheFu on 2018-03-10
Forget wifi. It will always suck.  I did over 1,000 wifi deployments at a prior job. That taught me to avoid wifi for anything other than  lite browsing or lite checking emails.

If you want to use networking, get a GigE ethernet adapter for all the systems, a GigE switch/router and CAT5e or better cables.

I was VERY CAREFUL to always say Mbps - that's Mega bits per second.  MBps is Mega Bytes per second - 8x faster.  Networking and disk performance is always shown in Mbps.  Only end-user software programs DON'T use Mbps, they show MBps.  Software people think in bytes.  Performance people think in bits.

---

### Post by allaboutgadgets on 2018-03-10
I was getting about a at least 20Mb over WiFi when I was transferring to things like the PS3. I’m certain even if only 10mb  which I’m certain would be much higher, it’s better than 500-600kb a second

---

### Post by TheFu on 2018-03-11
Did you look at all the components already?  Are they all USB3?  Is the CF reader USB3 and fast too?

What are the read and write speeds claimed by each of the storage devices?
 
  500 Kbps seems low, unless the flash storage is nearing the end-of-life.  I've seen USB3 flash storage go from 70+Mbps writes when I first got it to death in under a year.  This was from a highly reputable,worldwide, flash storage brand. The number of write cycles matters.  Consumer flash devices are designed for about 10,000 write cycles.  When running an OS, logs are constantly being written, which causes load-leveling in current generation flash devices.  A new flash device shouldn't slow down for a few months.

Also, I would avoid using any GUI tools to copy files around.

---

### Post by sudodus on 2018-03-11
See the following link and links from it about fast USB 3 pendrives,

[help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

I make USB pendrive that are slowing down fast again by wiping the whole device according to [this link](https://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297).

But some other component of the transfer chain might be the bottleneck, as described by TheFu.

I would also recommend a wired network (ethernet).

---

### Post by allaboutgadgets on 2018-03-11
All fast cards usb 3. They are meant to record fast large video and photos. 
What I ended up doing was just installing parallels to my iMac and booting the tails os from it then just transfering the files straight from the computer. Took about 45 minutes. Crazy part is I’m back on the Mack book air and transferring from the tails osbusb stick to the cf memory card that I keep a backup of the file on and I’m getting a solid 35mb a second with no drop under 30mbps. I find that really odd

---

### Post by TheFu on 2018-03-11
Perhaps tails behaves differently than Ubuntu?  Does it use TOR for all network connections?

---

### Post by allaboutgadgets on 2018-03-11
Yes. But tor shouldn’t have anything to do with transfer speeds between two USBs

---

