---
title: "Ubuntu, XP and Vista"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by TecTec on 2006-06-17
Hello,

I already have Windows XP and Ubuntu installed on my computer. I now want to install Windows Vista Beta 2 on a seperate partition. Will i need to do anything to get grub to recognize Vista? If so what must I do?

Thanks
TecTec

---

### Post by blair on 2006-06-17
I haven't installed Vista on a multi-boot system yet, but based on experience with MS arrogance, the Vista install will almost certainly toast your MBR, after which your system will only (and automatically) boot into Vista.  You will need to whack and restore your MBR using GRUB. I have had nothing but trouble doing this in the past. Do a forum search on GRUB for tips. Worst case, just reinstall Ubuntu after you install Vista. As part of the install process, Ubuntu will reconfigure GRUB correctly for all 3 OSs.

---

### Post by mscman on 2006-06-17
You'll have to reinstall grub once you have Vista loaded, as Vista will overwrite your entire MBR.  To do this, boot into the Live CD and issue the command:
```
sudo grub-install /dev/hda
``` (assuming /dev/hda is the location of the hard drive your MBR resides on.)

You should also note that Vista will leave a "permanent" bootloader that will keep loading until you reinstall Windows XP or overwrite the partition Vista resides on.  This can get pretty annoying, so I wanted to warn you in advance.

---

### Post by TecTec on 2006-06-17
Thanks
That's the simplest way. But I was hoping Vista wouldn't write over the MBR and I was wondering what to do in that case.

TecTec

Edit: didn't see mscman's post. 
Ok i guess i will try to do that. Have installed Vista yourself already?

---

### Post by mscman on 2006-06-17
You may want to check out the post here: 
[A Tale of Three OS's]("http://www.pro-networks.org/forum/viewtopic.php?t=77635")
as it covers basically the same thing you're asking.  I haven't tested it myself, so I can't guarantee any success; I'm simply pointing you in the right direction. :D

EDIT: I have installed Vista before (back in April or so) and installed Linux afterwards, which allowed me to overwrite the MBR.  I have heard Grub doesn't play well with Vista's boot loader when you try to reinstall it.  That's why I'm suggesting visiting the post above.

---

### Post by u.b.u.n.t.u on 2006-06-17
[QUOTE=TecTec]Thanks
That's the simplest way. But I was hoping Vista wouldn't write over the MBR and I was wondering what to do in that case.

TecTec

Edit: didn't see mscman's post. 
Ok i guess i will try to do that. Have installed Vista yourself already?[/QUOTE]

I saw the latest Vista beta on Thursday and it isn't anything special. If you set aside the eye candy, they haven't done anything new that Windows Blinds have already done. They haven't done anything to justify a 3Ghz CPU and 1GB RAM in my view.

---

### Post by longinus on 2006-06-17
I'm tri-booting, and it works fine..

When I installed Vista, it overwrote my mbr. For a less permant solution to boot Ubuntu, you can use the super grub live CD and it will find your grub info and show your old grub menu. Then when you are tired of Vista (or it expires) and wants grub back, just use one of the many methods to restore grub.

On a side note, I haven't tried earlier versions of Vista, but I liked what I saw. Aside from a very paranoid system, you can organize folders in a very impressive way, have folder favorites (gnome has it too of course), and the neat folder buttons on the address bar showing the directories (again, gnome has it too, but you can't choose another folder from a drop-down menu in those buttons).

---

