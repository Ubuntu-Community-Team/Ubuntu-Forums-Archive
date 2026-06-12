---
title: "Grub nowhere to be seen."
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by TRANQU111TY on 2008-01-24
After installing Ubuntu and using it for a week, I decided to go back into Windows for the first time since the installation of Ubuntu. I rebooted the comp, chose Windows in the Grub loader, then windows error - hal.dll missing etc annoyed me so I fixed it and got into Windows.

Now Grub does not load when I start my comp, it just brings up the Windows OS and I do not know of another way to boot into Ubuntu. Can someone please help me boot into Ubuntu?

---

### Post by p_quarles on 2008-01-24
One of the fixes you ran in Win may have overwritten the bootloader. Fortunately, it's easy to reinstall GRUB with the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kshane on 2008-01-24
> **TRANQU111TY said:**
> After installing Ubuntu and using it for a week, I decided to go back into Windows for the first time since the installation of Ubuntu. I rebooted the comp, chose Windows in the Grub loader, then windows error - hal.dll missing etc annoyed me so I fixed it and got into Windows.

Now Grub does not load when I start my comp, it just brings up the Windows OS and I do not know of another way to boot into Ubuntu. Can someone please help me boot into Ubuntu?

Download the iso file for Super Grub and put it on a cd, then boot with it.  It will provide you the option to reinstall Grub.  It's a "must have" for anyone running a dual boot system., IMHO...

Kevin

---

### Post by TRANQU111TY on 2008-01-24
OK thanks. Grub is working now but when I choose Ubuntu from the list I get this - Error 17: Cannot mount selected partition. Used SuperGrub.

---

### Post by kshane on 2008-01-24
> **TRANQU111TY said:**
> OK thanks. Grub is working now but when I choose Ubuntu from the list I get this - Error 17: Cannot mount selected partition. Used SuperGrub.

Can you post the contents of /etc/fstab?

Kevin

---

### Post by TRANQU111TY on 2008-01-24
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

---

### Post by kshane on 2008-01-24
> **TRANQU111TY said:**
> ```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

Seems to me that Grub isn't being told the Ubuntu partition is there.  Can you post the results of
```
blkid
```

Kevin

---

### Post by TRANQU111TY on 2008-01-24
```
/dev/sda1: UUID="64D8A877D8A848DE" TYPE="ntfs" 
/dev/sda2: UUID="eb0cd224-9196-471e-9dd8-b8af680b1948" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="A4857024856EC47" TYPE="ntfs" 
/dev/sda5: UUID="b8912a7f-dfa4-4b5a-b698-960003c8f9fc" TYPE="swap" 
```

---

### Post by kshane on 2008-01-24
> **TRANQU111TY said:**
> ```
/dev/sda1: UUID="64D8A877D8A848DE" TYPE="ntfs" 
/dev/sda2: UUID="eb0cd224-9196-471e-9dd8-b8af680b1948" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="A4857024856EC47" TYPE="ntfs" 
/dev/sda5: UUID="b8912a7f-dfa4-4b5a-b698-960003c8f9fc" TYPE="swap" 
```

Use the below code to open your fstab file:
```
 gksudo gedit /etc/fstab
```

Ad this line to your fstab file:
```

#Entry for /dev/sda2
UUID=eb0cd224-9196-471e-9dd8-b8af680b1948 / ext3 defaults,errors=remount-ro 0 1

```

Save then reboot and let us know what happened...

Kevin

---

### Post by TRANQU111TY on 2008-01-24
I'm still getting Error 17: Cannot mount selected partition. I need to go bed soon but thanks for your help will be on tomorrow sometime. :)

---

### Post by kshane on 2008-01-24
> **TRANQU111TY said:**
> I'm still getting Error 17: Cannot mount selected partition. I need to go bed soon but thanks for your help will be on tomorrow sometime. :)

Sorry we didn't fix ya.  :(

I should be around tomorrow, too...  

Kevin

---

### Post by p_quarles on 2008-01-24
This has worked for others getting the same error:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by TRANQU111TY on 2008-01-25
I did the fail safe thing of reformatting my whole computer and it's working fine now. :)

---

