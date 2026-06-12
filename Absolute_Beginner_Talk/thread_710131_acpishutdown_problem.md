---
title: "acpi/shutdown problem"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by bluebaby on 2008-02-28
hi everyone. i'm an absolute newbie with linux. i installed it ubuntu on an old compaq presario laptop. everything seems great until i tried to shutdown. the splash screen appears and then nothing happens. i then tried to install kubuntu but the same thing happens. i have to hard press the power button to turn it off. i also noticed that an "acpi error" message appears during boot up. i'm not sure if these problems are related. can somehow help me with this? thanks..

---

### Post by moshy on 2008-02-28
Is the error message during bootup something along the lines of
BIOS failed cutoff date (1997) acpi=force
(off the top of my head)?

I've got this problem too.
Go to this file /boot/grub/menu.lst
and down the bottom there is a little paragraph that looks like this
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0be926f9-6590-4f6b-95d2-9013bbc299b3 ro quiet splash acpi=force
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```
You've got to add acpi=force to the end of the line that starts with kernel

This fixed it for me, but everytime you get a kernel update, you have to do it again

---

### Post by jw5801 on 2008-02-28
The better way to do that would be to add it to the debian automagic options. That way you don't have to manually change it with any kernel change. Find the bit that looks like this (your options will probably be different to mine):
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet vga=791
```
and add acpi=force there:```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet vga=791 acpi=force
```

Then when you run "sudo update-grub" it'll rewrite your default entry with the new option.

---

### Post by moshy on 2008-02-28
Wow, I did not know that. So do I ever have to run "sudo update-grub" ever again, or will that happen automatically?

---

### Post by jw5801 on 2008-02-28
apt will call it for you whenever it installs a kernel update. In fact that's probably what's been removing acpi=force in the past! So, yeah, unless you change something else in the automagic options you shouldn't ever need to call update-grub again.

Have a read through the options, it's quite well documented and some of the others are quite useful too.

---

### Post by bluebaby on 2008-02-28
> **jw5801 said:**
> The better way to do that would be to add it to the debian automagic options. That way you don't have to manually change it with any kernel change. Find the bit that looks like this (your options will probably be different to mine):
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet vga=791
```
and add acpi=force there:```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet vga=791 acpi=force
```

Then when you run "sudo update-grub" it'll rewrite your default entry with the new option.
i'm sorry i have no idea how to do this..

---

### Post by plucky on 2008-02-28
> i'm sorry i have no idea how to do this..

Open a terminal **Applications > Accessories > Terminal** ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bck
gksudo gedit /boot/grub/menu.lst
``` Scroll down to the **# defoptions=quiet** and add **acpi=force** to the end of it.Save file.

Again in terminal ```
sudo update-grub
``` This will add **acpi=force** to the end of the kernel line.


Voila
Good luck

---

### Post by bluebaby on 2008-02-29
thanks a lot..but it didn't quite work. i tried substituting acpi=off instead and the bios error message disappeared but i still can't get proper shutdown.any suggestions?

---

### Post by plucky on 2008-02-29
> i still can't get proper shutdown.any suggestions?

When you put **acpi=off** you still need power management,so I suggest you also put **apm=on** also in the kernel line after the acpi=off.

To fix your power off problem ```
gksudo gedit /etc/modules
``` and add the line ```
apm power_off=1
``` to the end of the file, save file and then reboot

Good luck

---

### Post by bluebaby on 2008-03-01
hi. thanks for your patience. adding apm power_off=1 still doesnt solve the problem. .

---

