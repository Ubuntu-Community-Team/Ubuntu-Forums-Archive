---
title: "Xubuntu usb problem"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by LuckyX2 on 2007-01-27
I installed xubuntu on my sisters computer to experiment with. Previously having suse my sister had really enjoyed supertux. Now with xubuntu I need to install supertux but the computer has no internet connection and when I put supertux onto a usb drive and plug it in xubuntu does not recognize it. I noticed the red led on the flash drive does not turn on either but I am fairly sure that the usb ports are not broken. If anyone could help me get the usb working it would be greatly appreciated. Thanks

---

### Post by taurus on 2007-01-27
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by slipperhead on 2007-01-30
dont know if this will be any help but i booted with 'irqpoll' (without quotes)

i booted xubuntu, pressed esc to get into grub, e to edit the kernal line(with quiet splash etc.)
and added irqpoll on to the end of that line, then enter then b to boot normally

i only tried this because my usb did not work and as the laptop booted i saw irq 11 being ignored and a suggestion to boot with irqpoll.

it worked for me and usb works(tho i dont know why!)

if it works you can then edit menu list.

---

