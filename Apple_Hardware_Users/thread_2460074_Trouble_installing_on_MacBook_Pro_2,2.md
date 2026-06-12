---
title: "Trouble installing on MacBook Pro 2,2"
date: 2021-04-01
forum: Apple Hardware Users
---

### Post by noh2o on 2021-04-01
I made a bootable USB flash drive for Ubuntu 20.04. I used it to install on my daughter’s MacBook 4,1 (2008) with a new Sumsung Evo SSD. All went as it should have and she is enjoying it.
I wanted to do the same on my MacBook Pro 2,2 (also early 2008). Installed a new Samsung Evo SSD, inserted the same USB flash drive, powered it up while holding the option key as I did with the MacBook 4,1. The USB drive won’t not show up in the boot menu. I pulled the SSD out and reinstalled the original HD and the machine started normally. Swapped the SSD back in and tried again. No USB in the boot menu. So I put the original HD in an enclosure, plugged it into the same USB port and again powered it up while holding the option key. The external HD popped up in the boot menu and I selected it and the machine started right up. I went to disc utility and tried a restore with the SSD as the destination and the USB drive as the source while running from the external HD. No joy. 
So I know that the machine runs well. The USB ports all work. So I reformatted the SSD and did a restore with the SSD as the destination and the external (original HD) as the source. It restored the SSD with OS 10.6.8 Snow Leopard and the machine runs fine with the SSD.
The machine run well, the USB ports are fine, the SSD works well. I tried burning the bootable SSD to a DVD to install it and that brought no joy. I did an NVRAM reset. No joy.
I know I must be missing something. Any help is welcome.

Dave

---

### Post by howefield on 2021-04-02
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by kencu on 2021-06-21
You have something like this one I presume <https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.16-15-specs.html>.

It has a 32bit UEFI, and when I installed Ubuntu on a machine with a similar 32bit UEFI, I had to use a special modification to the 64bit boot disc to make it work. (The USB boot did not work for me either).

The quite simple application is here <https://github.com/demonicsweaters/make_single_eltorito.c>. It compiles is a few seconds, and makes a slight modification to the boot DVD image that allows it work on these older UEFI systems. It looks for a disk with a specific name, so look through the code to understand what disk name it is looking for, and make your image match that (or change the code). Then burn that modified image to a DVD, and boot away.

It worked just great for me, and I used that same DVD on several older systems. 

Once you are installed, then updates, etc, work as normal and you don't need to do anything special any more.

I hope you might find this helpful.

---

