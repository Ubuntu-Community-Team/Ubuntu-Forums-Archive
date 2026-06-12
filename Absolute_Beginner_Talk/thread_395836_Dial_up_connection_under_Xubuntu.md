---
title: "Dial up connection under Xubuntu"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by DreadPirateRoby on 2007-03-28
I followed the community documaentation page for my winmodem until it suggested modifying grub: 

"To fix, change the grub boot commands /boot/grub/menu.lst as follows _(pci=routeirq is new)_:"

> ## ## Start Default Options ##
  ## default kernel options
  ## default kernel options for automagic boot options
  ## If you want special options for specifiv kernels use kopt_x_y_z
  ## where x.y.z is kernel version. Minor versions can be omitted.
  ## e.g. kopt=root=/dev/hda1 ro
  # kopt=root=/dev/hda1 ro pci=routeirq

I'm not exactly sure where it wants me to replace or insert this text inside the file and I really don't feel like reinstalling everything should I mess up.

---

### Post by nixclusive on 2007-03-29
pci=routeirq is to appended to the line that says 'kernel'
example:

kernel          /vmlinuz-2.6.20.3-teststation root=/dev/hdc2 ro **pci=routeirq**

by the way.. make sure you know what you are doing.

---

### Post by DreadPirateRoby on 2007-03-29
For some reason I didn't see that chunk of text shown in the example in the file itself and assumed it wanted me to put the whole string someplace new.

When I checked again I saw it pretty clearly and was able to complete the instructions by placing just that part where it needed to go.

It still didn't work, but I'm starting to get tired of trying to get this winmodem working and I'm going to see about what else I can do.

Thanks for responding

---

### Post by DreadPirateRoby on 2007-03-29
I'll only have access to someone else's broadband connection for a short period tomorrow and need to know what I may need to get things working.These are my options as I see them.

I have an old thinkpad with a serial port and I was thinking of installing Xubuntu, DamnSmall, Puppy, or whatever else works on it and sharing the connection through USB (can you do that?) or a PCIMA ethernet card that I'd have to buy.

I could try adding a serial port through PCI card.

I'm going to try hooking up my external modem via usb, but I don't know what kind of success I'll have.
My external modem is an Actiontec 56k External Modem usb/serial

Try Open Suse on the HP and see if it has any better luck with my win modem

Computer is a HP [a1450n]("http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=us&dlc=en&product=1843646&lang=en")
with a Agere Systems PCI-SV92PP soft modem

Thanks agian to anyone who can respond.

---

