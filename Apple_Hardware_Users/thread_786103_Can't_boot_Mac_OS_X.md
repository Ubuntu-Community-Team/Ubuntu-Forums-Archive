---
title: "Can't boot Mac OS X"
date: 2008-05-07
forum: Apple Hardware Users
---

### Post by jobbernowl on 2008-05-07
Ok, so I thought I knew what I was doing, but I was wrong =)

I installed Ubuntu using bootcamp and now I can't boot up Mac OS. 

I understand I will probably have to reformat, which is ok because I made a backup before the whole procedure. 

My problem is that I can't boot up Leopard (OSX 10.5) when I restart with the CD in the tray, it just boots up unbuntu every time. 

Could someone lend some advice on booting the OSX cd? Is there a command I can enter in the grub boot loader?

Thanks!

---

### Post by cyberdork33 on 2008-05-07
hold c on startup, or try holding Option to get a menu.

---

### Post by jobbernowl on 2008-05-07
Nope, it just goes right into grub and then starts up ubuntu

---

### Post by cyberdork33 on 2008-05-07
wait are you on PPC? Open Firmware is only on PPC Macs.

---

### Post by jobbernowl on 2008-05-07
No, it is intel, so yes, no open firmware.

---

### Post by thenes on 2008-05-08
It sounds strange that you should not be able to boot the os x CD when holding down c at start up.

*You say that the system goes right into grup, but there is a grey screen first (which is efi loading)?
*Are you able to boot the Ubuntu live CD by holding down c at start up?

---

### Post by dark_harmonics on 2008-05-08
On intel macs its the D key on startup. If you want boot options you can also hold down the command (super) key on startup.

---

### Post by thenes on 2008-05-08
> **dark_harmonics said:**
> On intel macs its the D key on startup. If you want boot options you can also hold down the command (super) key on startup.

Strange. On my intel mac mini I hold down c to boot from a CD at start up and option (alt) to get options at start up:-k. (Though most of the time I use rEFIt)

---

### Post by blurg on 2008-05-08
> **thenes said:**
> It sounds strange that you should not be able to boot the os x CD when holding down c at start up.

*You say that the system goes right into grup, but there is a grey screen first (which is efi loading)?
*Are you able to boot the Ubuntu live CD by holding down c at start up?

Its the C key for boot from CD on my Intel iMac... And the alt/option key to use the bootcamp screen.

---

### Post by cyberdork33 on 2008-05-08
> **thenes said:**
> Strange. On my intel mac mini I hold down c to boot from a CD at start up and option (alt) to get options at start up:-k. (Though most of the time I use rEFIt)

me too.

---

