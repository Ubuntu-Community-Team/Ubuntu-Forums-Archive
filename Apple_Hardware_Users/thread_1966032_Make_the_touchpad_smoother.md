---
title: "Make the touchpad smoother?"
date: 2012-04-26
forum: Apple Hardware Users
---

### Post by s0l1dsnak3123 on 2012-04-26
Hi there! I managed to get 12.04 running on my Macbook Pro 8,1, and I'm very happy as a result! I'd now like to make it my mission to refine it down to perfection.

My main gripe with ubuntu right now is a relatively small one: the touchpad driver, in comparison with OSX, is no where near as nice for me, in my humble opinion (that is literally the only *real* problem I have!).

I also reckon it's more likely to be a configuration issue than a code issue, so I was wondering if anyone knew how to refine it?

This is what I'm used to from OSX:
[LIST]
[*]When I drag with 3 fingers I simulate a left click and drag
[*]When I drag with 4 fingers I move to a different workspace
[*]When I drag 2 fingers to the right, the scrollbar goes to the left
[/LIST]

---

### Post by Kallun on 2012-04-28
Hi s0l1dsnak3123,

You can achieve this with Touchegg, however I don't believe it's working in 12.04, it seems to present a segmentation fault. I haven't read up on it recently though, so perhaps there's progress?

---

### Post by s0l1dsnak3123 on 2012-04-28
> **Kallun said:**
> Hi s0l1dsnak3123,

You can achieve this with Touchegg, however I don't believe it's working in 12.04, it seems to present a segmentation fault. I haven't read up on it recently though, so perhaps there's progress?

Yep, segfaults for me also.

---

### Post by watgrad on 2012-04-28
Did you get bluetooth working?  This is the only thing that I cannot get to work on my macbookpro 8.1

---

### Post by s0l1dsnak3123 on 2012-04-28
> **watgrad said:**
> Did you get bluetooth working?  This is the only thing that I cannot get to work on my macbookpro 8.1

It works out of the box for me, I have the following hardware:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #5 (rev 05)
00:1a.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #1 (rev 05)
00:1d.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) (rev 08)

```

---

### Post by bradleyjones on 2012-04-28
In terms of configuration for the touchpad, touchegg is definately the way to go however it is not currently working in 12.04 due to problems with uTouch, see bug report - [https://bugs.launchpad.net/utouch-geis/+bug/986886](https://bugs.launchpad.net/utouch-geis/+bug/986886)

To those people getting the segfaults with touchegg you can fix this by downloading the daily build directly from the touchegg's svn but until uTouch gets updated we are left waiting.

I wish there was a way just to configure the multitouch gestures be default as the ones provided by the synaptics driver actually work quite well I just don't really have a need for 3-finger screen movement or a four finger tap, would rather configure them to do something useful!

---

### Post by phidia on 2012-04-29
> **bradleyjones said:**
> In terms of configuration for the touchpad, touchegg is definately the way to go however it is not currently working in 12.04 due to problems with uTouch, see bug report - [https://bugs.launchpad.net/utouch-geis/+bug/986886](https://bugs.launchpad.net/utouch-geis/+bug/986886)

To those people getting the segfaults with touchegg you can fix this by downloading the daily build directly from the touchegg's svn but until uTouch gets updated we are left waiting.

I wish there was a way just to configure the multitouch gestures be default as the ones provided by the synaptics driver actually work quite well I just don't really have a need for 3-finger screen movement or a four finger tap, would rather configure them to do something useful!

I think mulitouch can be quite useful and there are more options than just screen movement. 

Does anyone have experience with battery life on a mbp using 12.04 and if so how does it compare to OS X?

---

### Post by watgrad on 2012-05-03
> **phidia said:**
> I think mulitouch can be quite useful and there are more options than just screen movement. 

Does anyone have experience with battery life on a mbp using 12.04 and if so how does it compare to OS X?

I am finding that battery life is much improved.  It is comparable to OSX - can't say for sure how close, because I rarely use OSX anymore...but I'm getting about 5 hrs use on one charge.

---

