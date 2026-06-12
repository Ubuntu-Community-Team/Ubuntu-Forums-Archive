---
title: "acpi problem"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by citreonman on 2006-12-12
Hi All
  I am running ubuntu 6.10 x64 on asus-m2n-sli amd64-3200 1gb-mem 80gb-sata The problem is i had to disable acpi in bios before i could install ubuntu.Now when i want to go into xp pro i have to go into bios and enable acpi. Having to keep going into bios is a bit of a pain is there a program to fix this or have i done something wrong. Ubuntu is running fine upto now with luck if i can learn to do everything i want to do in linux i will sack windows to the bin.
     please be gentle i am an oldie learning something new
         regards 
            brian

---

### Post by Kobalt on 2006-12-12
Hello, 
I think I quite don't understand what you write, you mean, when you boot up your computer : don't you have Grub loading and asking you what system you want to boot on (like Ubuntu or Windows, or Ubuntu in recovery mode and something call MemTest...) ? You should have this...

---

### Post by citreonman on 2006-12-12
HI
 Yes i have grub and a choice between ubuntu or windows.If i want to use windows i have to enable acpi in bios. If i want to use ubuntu i have to disable acpi in bios.Ubuntu dosent seem to like acpi for some reason.
f

---

### Post by Kobalt on 2006-12-12
Ok then you must add the option to disable acpi when Ubuntu boots up, so that you can leave it always on in your BIOS. To do so, open the Terminal and in command line type this : 
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` (it's a backup, just in case). Then : 
```
sudo gedit /boot/grub/menu.lst
```
Look for a section, located at the end of the file that opened, that looks like this (even though some numbers should be different, but it's normal) : (the first one after *## ## End Default Options ##*)
> title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
And add "noapic nolapic acpi=off" at the end of the third line, so that it looks like this : 
> kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash noapic nolapic acpi=off
Save the file and close it, now reboot your computer and enable ACPI in BIOS, then try booting Ubuntu. 

Hope it helps you ! 
Cheerio

---

### Post by citreonman on 2006-12-13
Hi
  it works great thanks for your help

---

### Post by Kobalt on 2006-12-13
You're welcome !

---

### Post by tvgm2 on 2006-12-14
If you use this on a dual core system (X2) it will only use 1 CPU.  Is there any way to remedy this?

---

