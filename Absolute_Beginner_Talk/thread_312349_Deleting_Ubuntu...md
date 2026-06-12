---
title: "Deleting Ubuntu.."
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by lee101 on 2006-12-04
if i delete my linux partition via disk management in windows will that be safe 2 do, if i do this will i then have an empty hard drive or will it be unuseable.

please help!:)

---

### Post by wyldstryker on 2006-12-04
I've reinstalled Ubuntu enought times on my laptop to answer this one :-k : 

 If you delete the partitions while running windows you'd loose the Ubuntu install completely. But if you do delete it, remember to use fdisk or something like it to reset the master boot record or else the Grub boot loader will have a fit. ( fdisk /mbr )

---

### Post by Tomosaur on 2006-12-04
Sure, you can delete the partition without any problems (usually, but such things CAN go wrong. It's always wise to back stuff up before doing disk operations like this), but the partition will then be seen as unused space. You'll have to format it to something else before Windows can use it again. Alternatively, you can just grow your windows partition to cover the space.

Any particular reason you want to delete Ubuntu? If you just don't want it, that's fine, but if you're having problems someone may be able to help.

---

### Post by an.echte.trilingue on 2006-12-04
**Yes it is safe, but FIRST you should restore your windows MBR.**

Yous your windows system recovery disk and boot into the recovery console and type the command FIXMBR.

Once you are sure that has worked you can delete the ubuntu partition safely.

---

### Post by lee101 on 2006-12-04
> **Tomosaur said:**
>  Any particular reason you want to delete Ubuntu? If you just don't want it, that's fine, but if you're having problems someone may be able to help.

well i have a virus on my windows partiton and i want to delete linux 2 sort everyhing out.

---

### Post by lee101 on 2006-12-04
> **an.echte.trilingue said:**
> **Yes it is safe, but FIRST you should restore your windows MBR.**

Yous your windows system recovery disk and boot into the recovery console and type the command FIXMBR.

Once you are sure that has worked you can delete the ubuntu partition safely.

i dont have my windows system recovery disk:(

---

### Post by Tomosaur on 2006-12-04
That doesn't make much sense. You can run a Windows virus scan from linux just fine (which is in fact probably a better idea than running one within Windows).

---

### Post by lee101 on 2006-12-04
> **Tomosaur said:**
> That doesn't make much sense. You can run a Windows virus scan from linux just fine (which is in fact probably a better idea than running one within Windows).

ive tried that already, still won't go, i was planing 2 delete linux anyway, i may re-install it soon

---

### Post by Tomosaur on 2006-12-04
Hehe fair enough then.

Without your windows restore disk there is no easy way to 'restore' your MBR. However, there are a bunch of alternative bootloaders which will allow you to boot Windows anyway. Try searching on google for 'GAG Bootloader'. Once you have Windows working, you can look around for a windows recovery disk. There are a few sitting around online which have the recovery tools.

---

### Post by John E on 2006-12-04
It's definitely NOT SAFE to simply delete your Ubuntu partition. If you do so without removing Grub, you'll end up with an un-bootable PC (WyldStyker already mentioned one of the problems but there are potentially two...)

1) After you delete the partition you'll need to either boot from a **bootable** floppy disk that also contains **fdisk.exe** - OR - if you're running Windows XP you'll need to be able to boot from the install CD and choose the option to repair your installation. If I were you, I'd practise these things before deleting anything!!

2) Depending upon which partition is your Windows partition you might need to create an empty partiton in place of the deleted Ubuntu partition. This is because Windows own boot manager numbers the partitions sequentially. If Windows is in partition 1, you should be okay. However, if Windows was in partition 3 and Ubuntu was in partition 2, partition 3 would become partition 2 after you've deleted partition 2. Therefore, your Windows boot manager will attempt to boot from partition 3 which no longer exists. After deleting the Ubuntu partition, play safe and create a blank partition to replace it.

---

### Post by Sefrin on 2006-12-04
> **an.echte.trilingue said:**
> Yous your windows system recovery disk and boot into the recovery console and type the command FIXMBR.

I definitely had to do this once.  Was fairly easy once you knew how to enter recovery mode from the install disc.

---

### Post by deanlinkous on 2006-12-04
Download a win98 (or similar) boot floppy from bootdisk.com and use the fdisk utility to add/remove partitions, change the active partition or whatever you want to do. Or just use the command **fdisk /mbr** to wipe the bootloader if that is all you want.

easy peasy

---

