---
title: "Enable dual processors?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-16
I recently downgraded to 6.06 from 6.10. I installed the 686 smp via synaptic and rebooted, but did not see the 686 kernel. How do I get this to use both processors? 

uname -a:

Linux fastback 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686 GNU/Linux

cat /proc/cpuinfo:

shawnr@fastback:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) D CPU 2.80GHz
stepping        : 4
cpu MHz         : 2800.153
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5604.82

---

### Post by kambei on 2007-03-16
Check your /boot/grub/menu.lst - do you have an entry listing that 686-smp kernel you downloaded using Synaptic?

---

### Post by 67GTA on 2007-03-16
It shows the 686 kernel in the grub menu list, but it doesn't show up on the grub menu when I reboot. Do I need to update grub?

title		Ubuntu, kernel 2.6.15-28-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-28-686
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

---

### Post by 67GTA on 2007-03-16
Ran sudo update-grub and the 686 kernel still did not show in grub menu. Not sure where to go now. With 6.10 they were enabled by default, but 6.10 was still too buggy for me. Any ideas?

---

### Post by kambei on 2007-03-16
> **67GTA said:**
> It shows the 686 kernel in the grub menu list, but it doesn't show up on the grub menu when I reboot. Do I need to update grub?

Grub does not need to be refreshed manually to see a new boot entry... When you boot your system, do you see *any* boot entries displayed? By default (at least on Edgy) the grub menu display is disabled by default... that option has to be commented out like so:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

...in order to display your kernel choices...

---

### Post by 67GTA on 2007-03-16
I am dual booting Ubuntu 6.06 and Kubuntu 6.06, so it always shows the grub menu to select the OS. Right now it shows:

ubuntu
2.6.15-28- 386
2.6.15-28-386 recovery mode
2.6.15-26-386
2.6.15-26-386 recovery mode

and the kubuntu kernels

My grub section looks like this:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

The hiddenmenu option is commented out. Does this mean it is hiding the kernel?

---

### Post by kambei on 2007-03-16
> **67GTA said:**
> 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

The hiddenmenu option is commented out. Does this mean it is hiding the kernel?

Comment out ( put a # mark) that second mention of 'hiddenmenu"

---

### Post by kambei on 2007-03-16
> **67GTA said:**
> I am dual booting Ubuntu 6.06 and Kubuntu 6.06, so it always shows the grub menu to select the OS. Right now it shows:

ubuntu
2.6.15-28- 386
2.6.15-28-386 recovery mode
2.6.15-26-386
2.6.15-26-386 recovery mode

and the kubuntu kernels


Which /boot/grub/menu.lst is providing grub with its boot options... the Ubuntu install or the Kubuntu install?

Maybe you have the 686-smp listed on one of the menu.lst files... but grub is configured to use the menu.lst on the other install?

---

### Post by 67GTA on 2007-03-16
I installed Kubuntu last, so it would have configured the grub install. It is listed first in the grub menu. I didn't know that would cause a problem. How do I check to see if this is the case, and how would I fix that? If I change this, will Kubuntu have the same problem if ubuntu handles  grub? I haven't started it up yet.

---

### Post by kambei on 2007-03-16
> **67GTA said:**
> I installed Kubuntu last, so it would have configured the grub install. It is listed first in the grub menu. I didn't know that would cause a problem. How do I check to see if this is the case, and how would I fix that? If I change this, will Kubuntu have the same problem if ubuntu handles  grub? I haven't started it up yet.

Not necessarily a problem... I take it you installed that 686-smp kernel on Ubuntu, and the menu.lst file on Ubuntu contains the new entry for it, right?

Afterwards, when you installed Kubuntu it installed grub in your Master Boot Record and overwrote your previous Ubuntu config - pointing grub to the /boot/grub/menu.lst on Kubuntu.

If you are satisfied with that arrangement... just copy-n-paste that 686-smp grub entry from the menu.lst that has it listed, into the menu.lst that does not...

---

### Post by 67GTA on 2007-03-16
I installed them both before I installed the 686 kernel in ubuntu. When I look in grub (ubuntu) there is only one menu list. They are on seperate partitions.

---

### Post by 67GTA on 2007-03-16
I just booted into Kubuntu and the grub menu only showed the 386 kernel. It makes sense that if Kubuntu installed grub that it would use it's config instead of Ubuntu's. I will try putting the 686 entry into Kubuntu as you suggested and see what happens.

---

### Post by kambei on 2007-03-16
> **67GTA said:**
> I installed them both before I installed the 686 kernel in ubuntu. When I look in grub (ubuntu) there is only one menu list. They are on seperate partitions.

Try these steps:

1/ While in Ubuntu, open /boot/grub/menu.lst in your text-editor-of-choice... Scroll down until you see that entry for that 686-smp you installed... it will be something like this (your settings will differ):

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 vga=791 ro splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

...copy that entry, then...

2/ Mount the partition that contains the /boot directory in Kubuntu... open the menu.lst file stored in Kubuntu using a text editor and paste that 686-smp entry along with the other boot entries...

3/ Make sure any lines that mention 'hiddenmenu' are hashed out (i.e. # hiddenmenu)

4/ Save your changes and reboot.. the boot option you pasted should now appear

In the future, whenever you add a kernel to the *buntu install that grub references its menu.lst at boottime (in your current setup, that would be Kubuntu) - it will automatically be added to the file... But whenever you add a kernel to the other *buntu install, the new entries will have to be copied and pasted over like the method above...

Hope that helps...

---

### Post by kambei on 2007-03-16
Just a quick hint... before you modify your /boot/grub/menu.lst, you might want to backup a copy:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

This has saved me from some grief in the past... :-)

---

### Post by 67GTA on 2007-03-16
I copied the 686 menu listings into the Kubuntu grub menu list, booted to 686 kernel  and I now have dual processors again!!! Thanks for the help. I never thought about the Kubuntu installation handling my grub menu. One of these days I will get rid of the Microsoft mentality. ](*,) 
Man I love Linux!

---

### Post by 67GTA on 2007-03-16
Just a side note for anyone using this post for help, I had to reinstall my ATI driver after changing kernels to get direct rendering and 3D acceleration working again.

---

