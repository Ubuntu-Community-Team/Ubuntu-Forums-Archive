---
title: "[SOLVED] Cloned my hard drive, now no boot"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-06-18
Ok I just cloned my hard drive... and now Xubuntu won't boot.

It loads the GRUB then just stops on the Xubuntu loading screen...

How can i make this hard drive boot?

thanks,
tom

---

### Post by confused57 on 2007-06-18
> **kernel tom said:**
> Ok I just cloned my hard drive... and now Xubuntu won't boot.

It loads the GRUB then just stops on the Xubuntu loading screen...

How can i make this hard drive boot?

thanks,
tom

Boot up the live cd, open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

You could mount your root partition from the live cd & post your menu.lst(and maybe your fstab):
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by ramjet_1953 on 2007-06-18
What did you use to clone your HDD?

I have found that Ghost for Linux (G4L) makes a perfect, working clone.

If you follow this, you should be able to install GRUB.

1. Boot from your LiveCD

2. Open a console

3. Type in : [COLOR="Red"]sudo grub[/COLOR]

4. **grub>** [COLOR="Red"]root (<tab>[/COLOR]  [COLOR="Blue"]      note: <tab> is an actual TAB keystroke[/COLOR]

5. It should then recognise your HDD and give the mountpoint.

6. **grub>** [COLOR="Red"]root (<mountpoint as given above>)[/COLOR] eg (hd0,5)

7.**grub>** [COLOR="Red"]setup (<your HDD>) [/COLOR]eg hd0

8 **grub>** [COLOR="Red"]quit[/COLOR]

Now re-boot and hopefully, you should get a GRUB menu and your system should boot.

Regards,
Roger :cool:

---

