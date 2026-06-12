---
title: "Ubuntu Fiesty Fawn Won't Shut Down, Only Freezes"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by musicman247 on 2008-01-19
I don't know if this is a known issue or not, but after a fresh install with only kiba-dock installed I can no longer shut down my laptop. Whenever I press the power button or click the Shutdown button the laptop will freeze. The mouse will still move, but nothing responds, and the power down options do not show up. I have to press and hold the power button to shut off the laptop.

Anybody else heard of this?

---

### Post by fatality_uk on 2008-01-19
This is a sort of known bug.

Start by typing the following into a terminal:

```
sudo gedit /boot/grub/menu.lst
```

Scroll down and find the first entry like this:
```
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=5cd4ce85-32c2-4bc2-8183-b68648ee7be3 ro quiet splash
```

Now add the following to the end of that line:
```
acpi=force pci=noacpi
```


So this part of your grub list should now look something like this:

> 
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5cd4ce85-32c2-4bc2-8183-b68648ee7be3 ro quiet splash acpi=force pci=noacpi
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

Hopefully this will solved the power down issue.

Hope this helps

---

