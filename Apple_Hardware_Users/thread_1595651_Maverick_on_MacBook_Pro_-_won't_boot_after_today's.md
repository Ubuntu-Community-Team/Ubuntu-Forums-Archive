---
title: "Maverick on MacBook Pro - won't boot after today's update"
date: 2010-10-13
forum: Apple Hardware Users
---

### Post by fhucho on 2010-10-13
I have Maverick on Macbook Pro 7,1. Today I installed updates and restarted. When I select Linux in rEFIt, it shows penguin for a while and then black screen with blinking cursor, no grub. What can I do?

---

### Post by pc_michael on 2010-10-13
First try using rEFIt to resync your partitions.

If that doesn't work, you might have to boot from a LiveCD and reinstall Grub [using these instructions](https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD).

---

### Post by QB89Dragon on 2010-10-15
Same issue here. Update nuked a working 64-bit install.
I've tried reinstalling grub on both /dev/sda and /dev/sda3, wiped grub and rebuilt the MBR on the disk. Reinstalled refit, tried booting to the disk via a live cd. Every time it gets to grub, it freezes with the same symptoms described above. However the bugs relating to this issue on the livecd seem to suggest it is to do with efi support in the kernel - I'm not sure if this means the ubuntu kernel or grub's mini-kernel thing.
Either way, I'm about to wipe mac os and put an msdos disklabel on my mac - I need this computer running by tomorrow :(

I can update the install from a livecd and will try doing proposed updates from the repos to see if anything fixes it.

---

### Post by ceratophyllum on 2010-10-21
This happens to me on my macbook pro 6,2 every once in a while. It happened right after I installed Kubuntu 10.4 (dual boot using refit: OS X, Lucid. I resized the HFS+ partition to make room for linux.).  I'm not sure what I did to fix it; I think I just rebooted a couple of times and it worked. Now today it stopped at the penguin again and rebooting a couple times doesn't fix it. I don't remember installing any updates yesterday! I did apt-get dist-upgrade to Maverick a couple of days ago...

It's strange that this flakey behaviour is not mentioned in community ubuntu macbook docs and the refit site.  Maybe it is something obscure involving grub, refit, and Apple's bizarre partition table, but only with certain macbooks?

Any luck?

---

### Post by ebash on 2010-10-24
I have the same problem with my macbook pro 7,1. It was running ubuntu 10.04 fine without problems. I upgraded to 10.10 and did all upgrades afterwards. I was able to reboot the laptop a couple of times but this morning nothing. All I see is a black screen with a cursor blinking.

I tried to reinstall grub using use the rescue disk, the live cd, remounting the physical partitions, etc and nothing. Grub complains that it can't be installed in /dev/sda3 and instaling in /dev/sda yields also errors.

At the end there's no ubuntu on my laptop :(

---

### Post by ceratophyllum on 2010-11-02
The update had nothing to do with why my macbook pro hangs at the penguin screen: it was the Virgin Mobile wireless USB modem/microSD reader that I'd left plugged in! Just removing it caused the macbook pro to continue booting normally.

Plugging in the modem AFTER the macbook pro has booted is no problem. It seems to work perfectly. Maybe refit/grub sees a USB drive and hangs trying to boot from it?

---

