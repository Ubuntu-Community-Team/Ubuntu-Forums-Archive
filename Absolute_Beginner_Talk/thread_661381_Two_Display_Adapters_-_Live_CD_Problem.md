---
title: "Two Display Adapters - Live CD Problem"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by suberatu on 2008-01-07
My computer was shipped with an integrated Intel(R) Extreme Graphics 82845G\GL\GE\PE\GU card. I upgraded by installing an nVidia GeForce 5500 FX to PCI slot (PCI:1:9:0) about a year ago. I disabled the Intel card (through Windows device manager) and reconnected the monitor cable to the slot coming out of the 5500's PCI slot instead of the Intel card's slot. It's been working fine ever since. Now, when I try to run Ubuntu from Live CD (tried both 7.10, and 6.06 LTS), I get some strange errors which I believe have something to do with the video cards.

Most of the time, the error that comes up complains about no screen being found or xserver not having been configured correctly. When I try to 'sudo dpkg-reconfigure xserver-xorg', and set it to auto-detect, it sees the Intel card, not the nVidia 5500. Of course, no monitor is connected to the card. I don't know how to make the live cd load on the 5500 (would like to know), so I tried re-enabling the card (through windows device manager), but when I do that and try to connect the monitor to that (Intel) card, it's as though there is nothing connected to the monitor (amber light and goes to sleep). 

Anyone have any similar experience or know how to fix this problem? Help would be much appreciated.

---

### Post by blueridgedog on 2008-01-08
What you do in device manager under windows will have no effect outside of that environment.

Can you disable the on-board card in the BIOS of your motherboard?  Typically you hit a key (F2 for example) to enter the BIOS and then look for something related to "integrated peripherals" and then a method to disable the onboard video adapter.

However, some newere motherboards will not let you disable it, only giving an option to set it to "auto".  

Perhaps a more Ubuntu savvy poster will pitch another answer.

---

