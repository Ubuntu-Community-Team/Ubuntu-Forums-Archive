---
title: "no luck booting live cd on eMac"
date: 2012-03-02
forum: Apple Hardware Users
---

### Post by shpoonj on 2012-03-02
Hi all, I'm new, so please excuse this plea for help!

I'm trying to install xubuntu on an old eMac(specs below). I have no problem burning and verifying the install CD(using CD-Rs if that makes a difference), but holding C on reboot does nothing. Holding cmd+opt+o+f didn't do anything either, but thanks to another forum post, I used terminal to have to eMac boot to Open Firmware. However, boot cd;\\:tbxi isn't doing the trick. The eMac does read the CD in OS X.

I've tried a few versions, most recently 10.04.

Any insight would be appreciated! Thanks for your time!

Hardware Overview:

  Machine Name:    eMac
  Machine Model:    PowerMac4,4
  CPU Type:    PowerPC G4  (2.1)
  Number Of CPUs:    1
  CPU Speed:    700 MHz
  L2 Cache (per CPU):    256 KB
  Memory:    256 MB
  Bus Speed:    100 MHz
  Boot ROM Version:    4.4.2f1
  Serial Number:    G823248SN9K

---

### Post by Double.J on 2012-03-02
> **shpoonj said:**
> Hi all, I'm new, so please excuse this plea for help!

I'm trying to install xubuntu on an old eMac(specs below). I have no problem burning and verifying the install CD(using CD-Rs if that makes a difference), but holding C on reboot does nothing. Holding cmd+opt+o+f didn't do anything either, but thanks to another forum post, I used terminal to have to eMac boot to Open Firmware. However, boot cd;\\:tbxi isn't doing the trick. The eMac does read the CD in OS X.

I've tried a few versions, most recently 10.04.

Any insight would be appreciated! Thanks for your time!

Hardware Overview:

  Machine Name:    eMac
  Machine Model:    PowerMac4,4
  CPU Type:    PowerPC G4  (2.1)
  Number Of CPUs:    1
  CPU Speed:    700 MHz
  L2 Cache (per CPU):    256 KB
  Memory:    256 MB
  Bus Speed:    100 MHz
  Boot ROM Version:    4.4.2f1
  Serial Number:    G823248SN9K



Hi there, Welcome to the forums!

I think the first thing is to look at the keyboard/usb port - those keyboard commands should work when booting... are you holding down the keys from power on?  you shouldn't press the command until the chime?

Also did you download the PPC version? I don't think the live PPC version fits on a CD if I remember, you have to use a USB key... but I could be wrong - basically when you explore the CD, does it have a folder called yaboot? it may be in a folder called install or boot? 

If you don't have a yaboot folder, it's for X86 and won't run on eMacs... get the PPC version [here]("http://http://cdimage.ubuntu.com/xubuntu/ports/releases/10.04/release/") Please not in advance that the live image will not fit on a CD and you can only boot CD -R on old eMacs - if you can't use a USB you need to use the alternate CD to install.

Also once in openfirmware, you have to point the boot process at the yaboot bootloader on the install disk - this will hand the boot process over to yaboot which will then launch xubuntu ppc.

try the following instead
```
boot cd:,\install\yaboot
```

if your OF code doesn't show where yaboot is it can't be booted from OF, same goes for USB booting. Hopefully though, by pressing the buttons just after the chime, or downloading a different CD you won't need to go into OF.

One last thing - seriously consider upgrading the ram - I got 1GB (2x512) eMac RAM off Ebay for £5.50! - very easy to fit; just unscrew the bottom panel, will make the world of difference... just bare in mind that 1GB is the max for your machine - 512MB in each slot... Oh and check on crucial first to make sure you get the right sticks!

Really hope it helps!

---

### Post by shpoonj on 2012-03-02
Your suggestion worked! I typed what you said into OF and now I'm a happy camper! Thank you!

---

