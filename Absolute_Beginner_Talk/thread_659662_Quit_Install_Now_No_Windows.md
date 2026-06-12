---
title: "Quit Install Now No Windows"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by archiphile on 2008-01-05
I quit install of Ubuntu, now my pc will not boot windows xp.  I receive the following error message;

MBR ERROR 

Press any key to boot from floppy.....

is there any way to edit the MBR in Ubuntu?

I have to have windows and all of my info on that system is still there Windows XP just cannot boot. 

Help Please I am sick at this point.

Thanks

Archiphile

---

### Post by wheredidrealitygo on 2008-01-06
You could download the Super Grub Disc on another computer and use it to repair your MBR, use the MS Recovery Console ([http://support.microsoft.com/kb/314058]("http://support.microsoft.com/kb/314058")) or finish the Ubuntu install, which should fix it by properly mapping Grub (the boot loader) to XP.

---

### Post by SpookComix on 2008-01-06
If you're running Windows XP, your best hope is to boot from your Windows XP CD.  However, only do this if you're prepared to lose access to your Ubuntu install until you fix Grub later.  After the setup program finally loads, choose the options to repair an existing Windows installation using the Recovery Console.

Once at the command prompt that the Recovery Console drops you to, use the following commands:

```
fixboot
fixmbr
exit
```

Remove the CD before the system reboots.  See if that works out for you.

Another big question would be to find out how and why your Ubuntu installation failed.  Any information you can provide might let someone steer you toward a solution, and might fix Grub in the process, making Windows accessible.

--SC

---

### Post by archiphile on 2008-01-06
Another big question would be to find out how and why your Ubuntu installation failed.  Any information you can provide might let someone steer you toward a solution, and might fix Grub in the process, making Windows accessible.


I quit the install that is why it "Failed" I quit the install because I put grub in the wrong partition.

---

### Post by SpookComix on 2008-01-06
Honestly, then, I'd just restart the install.  Once it finishes, it will have found your Windows installation and give you the option to boot from it.

--SC

---

