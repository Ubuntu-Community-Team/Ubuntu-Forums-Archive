---
title: "Disable OS Leopard EFI Update"
date: 2008-01-28
forum: Apple Intel Users
---

### Post by Funkasaurus on 2008-01-28
Hey Guys, 
I've been running Ubuntu on my mac for a bout 2 weeks now, and one day after mac os updated itself... boom, no more rEfit boot menu. 
The jerks down at apple had written over my bootloader!

After some poking around & reinstalling rEFIt once, (don't think it was necessary tho).. i just reenabled the bootloader by entering:

cd /efi/refit
./enable.sh

I don't care for the EFI firmware update that apple wants me to have... Is there a way to permenantly disable it??

---

### Post by cyberdork33 on 2008-01-28
> **Funkasaurus said:**
> Hey Guys, 
I've been running Ubuntu on my mac for a bout 2 weeks now, and one day after mac os updated itself... boom, no more rEfit boot menu. 
The jerks down at apple had written over my bootloader!

After some poking around & reinstalling rEFIt once, (don't think it was necessary tho).. i just reenabled the bootloader by entering:

cd /efi/refit
./enable.sh

I don't care for the EFI firmware update that apple wants me to have... Is there a way to permenantly disable it??It's OK, that happens often. rEFIt is not a bootloader, it is just an interface to the EFI firmware. You described exactly how to fix it, and you don't have to do that very often.

---

### Post by Funkasaurus on 2008-01-29
Ok thanks for clarification on the issue. I figured that it was not worth it to try and disable the EFI Updater

---

### Post by ronocdh on 2008-01-31
> **Funkasaurus said:**
> one day after mac os updated itself... boom, no more rEfit boot menu. 
If this was a typical system update, then you should have been able to uncheck the individual EFI update. I think you do this by hitting the delete key with the update selected in the list.

I don't run Leopard, but I remember in September 2007 Apple released an EFI update for Tiger that solved my non-responsive keyboard problem in GRUB and the main menus of live CDs.

---

