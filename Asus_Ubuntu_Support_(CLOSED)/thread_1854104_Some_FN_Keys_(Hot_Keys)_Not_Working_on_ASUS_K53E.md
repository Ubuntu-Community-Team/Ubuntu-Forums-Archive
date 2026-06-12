---
title: "Some FN Keys (Hot Keys) Not Working on ASUS K53E"
date: 2011-10-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by GreenRaccoon on 2011-10-03
I just installed Ubuntu 11.04 Natty Narwhal 64 bit.  Some of the hot keys, like adjusting screen brightness, would work fine, but the buttons to adjust the sound wouldn't work.  I couldn't set them in the "Keyboard Shortcuts" application either.  Then I found this awesome site:

[http://blog.zasekoj.com/2011/07/16/enable-global-keys-hot-keys-in-ubuntu-on-asus-k53/]("http://blog.zasekoj.com/2011/07/16/enable-global-keys-hot-keys-in-ubuntu-on-asus-k53/")

I haven't tried making the .deb package for an easier install after kernel updates, but the first part worked great!

---

### Post by GreenRaccoon on 2011-10-30
Installing Linux kernel 3.0 also fixes this issue.

---

### Post by Kirstine on 2011-10-31
Hi! i tried the same thing, but after typing "sudo modprobe asus-nb-wmi" i got this answer:

```
FATAL: Error inserting asus_nb_wmi (/lib/modules/3.0.0-12-generic/drivers/platform/x86/asus-nb-wmi.ko): No such device
```

do you know why and what i can do? :)

---

### Post by GreenRaccoon on 2011-10-31
> **Kirstine said:**
> Hi! i tried the same thing, but after typing "sudo modprobe asus-nb-wmi" i got this answer:

```
FATAL: Error inserting asus_nb_wmi (/lib/modules/3.0.0-12-generic/drivers/platform/x86/asus-nb-wmi.ko): No such device
```

do you know why and what i can do? :)

Did you install Linux kernel 3.0.0 before following the guide?  If you install the Linux kernel, you shouldn't have to install the module from the guide; the hot keys should be working.

If you don't know how to install a Linux kernel, you can go to this thread:
[http://ubuntuforums.org/showthread.php?t=1872537]("http://ubuntuforums.org/showthread.php?t=1872537")

3.0.4 is the latest stable kernel, but the latest I have tried so far is 3.0.0.  2.6.39 might fix the hot key issue also; I am not sure.

---

### Post by GreenRaccoon on 2011-10-31
> **GreenRaccoon said:**
> Did you install Linux kernel 3.0.0 before following the guide?  If you install the Linux kernel, you shouldn't have to install the module from the guide; the hot keys should be working.

If you don't know how to install a Linux kernel, you can go to this thread:
[http://ubuntuforums.org/showthread.php?t=1872537]("http://ubuntuforums.org/showthread.php?t=1872537")

3.0.4 is the latest stable kernel, but the latest I have tried so far is 3.0.0.  2.6.39 might fix the hot key issue also; I am not sure.

I just installed Linux kernel 3.0.4 and it seems to be working great!

---

### Post by Kirstine on 2011-11-04
> **GreenRaccoon said:**
> I just installed Linux kernel 3.0.4 and it seems to be working great!


Thanks a lot! im giving it a try :)

---

### Post by Kirstine on 2011-11-04
> **GreenRaccoon said:**
> I just installed Linux kernel 3.0.4 and it seems to be working great!

a week ago i did the following to fix the screen brightness and it worked which made the sound not work... do you know how its related and if the updates of kernals should fix it?


> 
1.
Run the following command in Terminal:
```
sudo gedit /etc/default/grub
```

Find the following line:
```
GRUB_CMDLINE_LINUX=""
```

Change it to the following:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

2.
Now Run
```
sudo update-grub
```

3. Reboot

---

### Post by GreenRaccoon on 2011-11-04
> **Kirstine said:**
> a week ago i did the following to fix the screen brightness and it worked which made the sound not work... do you know how its related and if the updates of kernals should fix it?

If you don't update the kernel, I'm guessing that you would need to add something to:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
But I am not sure what that would be.  It would probably be found somewhere on this page: [http://redsymbol.net/linux_boot_parameters]("http://redsymbol.net/linux_boot_parameters/").  (Also, if you don't know this yet, whenever you change something in "/etc/default/grub", or any GRUB file, you have to type into Terminal "sudo update-grub" for the changes to take place.)  I wouldn't do any guess and testing from that page though.  If GRUB gets messed up, it can be pretty hard to fix it, since your computer won't be able to boot up.

Installing a newer kernel should fix all of your hardware problems, assuming that you have an ASUS K53E also.  If you do install that kernel, you're probably going to want to delete that modification in /etc/default/grub.  To do this, type this in Terminal:
```
sudo gedit /etc/default/grub
```
Go to this line:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
Then change it to this:
```
GRUB_CMDLINE_LINUX=""
```
Then type this in Terminal:
```
sudo update-grub
```
If you install a newer kernel, just make sure you choose that kernel in GRUB when your computer starts up.  It will almost definitely be the first option anyway.  You can still choose the older kernel if you want, but the hardware problems will not be fixed.

One more thing.  If you haven't noticed, when you are running the older kernel (the one you have now, the default), don't close the laptop lid; once you open it back up, everything freezes.  The newer kernel fixes this problem too.

---

