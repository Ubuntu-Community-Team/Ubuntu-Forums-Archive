---
title: "Unable to boot MBP 2011: MODSIGN: Couldn't get UEFI db list"
date: 2018-03-22
forum: Apple Hardware Users
---

### Post by kai.ho on 2018-03-22
I'm totally new to linux and am trying to install Ubuntu on an old MBP 2011. 
Steps I have completed so far:


[LIST]
[*]Create bootable usb using etcher (also created one using diskutil through terminal but I guess there is not much difference there)
[*]Create bootable dvd as an alternative to the usb
[*]installed rEFInd
[*]attempted to boot from both the usb and the dvd
[/LIST]

Which medium I booted from didn't make a difference. After the GRUB menu appeared I chose "try ubuntu without installing" and always received the error 
       [I]couldn't get size: 0x800000...
       MODSIGN: couldn't get uefi db list
       couldn't get size: 0x800000...
[/I]after which the system froze and I had to force shutdown. 
Running the *boot* command from the GRUB terminal returns the message *load kernel first.*
Editing the boot options by pressing e and adding *nomodeset *caused the system to load further giving me the screen as pictured followed by a black screen with a cursor and nothing more. 
I have been unable to find anything helpful on the internet. Any suggestions as to how to proceed would be greatly appreciated. Is it possible that there is a fatal hardware issue behind this? The overheating makes me wonder.... I do have high sierra installed and working fine....

---

### Post by QIII on 2018-03-22
Moved to Apple Hardware Users.

---

### Post by zsuark on 2018-06-14
Can you please provide the link to where this was moved to?

---

### Post by andrew80 on 2018-06-15
You need to press "e" when the cursor is on try ubuntu without installing and then enter nomodeset after the last text and then press F10.

I have been trying to install on my MBP 2010 this was the first issue I came across.

---

