---
title: "Laptop booting R-E-A-L-L-Y slowly"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by fourdigit on 2008-04-09
It's a gateway ([http://support.gateway.com/s/Mobile/Q106/Blade/1008822sp2.shtml](http://support.gateway.com/s/Mobile/Q106/Blade/1008822sp2.shtml)) and whenever I turn it on, it hangs with a blank screen for about 3-4 minutes. But once the login screen appears everything moves along nice and smoothly. I can't seem to figure out what could be causing this.

Any ideas?

---

### Post by spiderbatdad on 2008-04-09
Possibly certain boot parameters are required due to bios settings. Run ```
dmesg
``` in your terminal and follow the boot process. Some things look like errors bu really aren't. Other problems in the boot process may offer you suggestions, for example "APIC diabled in BIOS.....try adding 'lapic'" or it may say local APIC found!

Also check to make sure you have a file called /etc/X11/xorg.conf.

---

### Post by fourdigit on 2008-04-09
```
[   27.113517] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18

```

That showed up a lot. Does it mean anything?

There was also this:

> [   13.661528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.661656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   13.661756] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   13.661855] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   13.663631] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   13.663721] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   13.663807] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   13.663892] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   13.663982] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   13.664066] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   13.664152] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   13.664237] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   13.664367] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.



EDIT: I also just found this:

> [   13.464864] ENABLING IO-APIC IRQs
[   13.465058] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.504740] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   13.504786] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   13.504788] ...trying to set up timer as Virtual Wire IRQ... works.
[   13.652322] Brought up 1 CPUs


---

### Post by spiderbatdad on 2008-04-09
nope. interrupts are supposed to be there.
can you copy and paste the whole thing into a gedit text document. Then right click on the document and select 'create an archive'  You can upload the archive here using the manage attachment tool below the reply window.

---

### Post by fourdigit on 2008-04-09
[http://rafb.net/p/gUNSBG42.html](http://rafb.net/p/gUNSBG42.html)

This was easier.

---

### Post by waynep on 2008-04-09
I loaded 7.10 on my HP nc4000 laptop. It took forever to boot like you are describing. It sat on a blank screen for minutes. It made me wonder if anything was really happening. I went to openSUSE, it was better. Monday evening, I loaded ubuntu 8.04 Beta, it loads quickly. Also during boot, there is not a blank screen, it has a bar that moves back and forth so you can see something actually happening. 

I would really like to see the boot for ubuntu momic openSUSE. It has a splash screen that you can hit ESC on and watch the boot info scroll buy if you want. It's a nice feature.

I guess I did not really answer your question, but my install of 8.04 does boot much faster than my 7.10 install did. Both were installed from the Live CDs.

-wayne

---

### Post by fourdigit on 2008-04-09
> **waynep said:**
> I loaded 7.10 on my HP nc4000 laptop. It took forever to boot like you are describing. It sat on a blank screen for minutes. It made me wonder if anything was really happening. I went to openSUSE, it was better. Monday evening, I loaded ubuntu 8.04 Beta, it loads quickly. Also during boot, there is not a blank screen, it has a bar that moves back and forth so you can see something actually happening. 

I would really like to see the boot for ubuntu momic openSUSE. It has a splash screen that you can hit ESC on and watch the boot info scroll buy if you want. It's a nice feature.

I guess I did not really answer your question, but my install of 8.04 does boot much faster than my 7.10 install did. Both were installed from the Live CDs.

-wayne

Well, the thing is, I have 7.10 on my desktop as well, and it loads perfectly really swiftly.


An unrelated question, if you install the beta of 8.04, will you be able to upgrade to the stable release seamlessly or how does that work?

---

### Post by spiderbatdad on 2008-04-09
Hmmm. I don't see anything that jumps out as a serious problem.
Two thoughts come to mind:
1. my system used to hang like that, and was fixed by editing the values in /etc/usplash.conf to 1024x768 That was in Gutsy. Upgrading to Hardy I developed the system hang again and usplash did not fix it. Instead, I had to make use  of some kernel parameters.

2. Edit the kernel line by removing --quiet splash so you can watch and see where it hangs.

I believe you can do this one time. By entering the grub menu at boot...press 'e' to edit...arrow key to the line beginning with 'kernel' and delete --qiuet splash from the end of that line...press 'b' to boot.

This should work, if it doesn't post back, or edit the line via /boot/grub/menu.lst

---

### Post by waynep on 2008-04-09
> **fourdigit said:**
> Well, the thing is, I have 7.10 on my desktop as well, and it loads perfectly really swiftly.


An unrelated question, if you install the beta of 8.04, will you be able to upgrade to the stable release seamlessly or how does that work?

Usually when a new release is out there is an option to upgrade. I assume the same thing will happen when the official release is out. I am not making a ton of customizations until I am sure I can update to the non-beta version after release.  I backup my home dir to a NAS so a reinstall if needed wont be an issue.

Reinstall, put home dir back, and I am good to go. Yea I'll have to setup a printer again but that was fairly trivial.

-wayne

---

### Post by fourdigit on 2008-04-09
> kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=be11dd18-e4ed-4c3a-b891-51143960b44b ro quiet splash

That line?

---

### Post by fourdigit on 2008-04-09
I mean, is that the line that I'm supposed to remove "quiet splash" from?

---

### Post by spiderbatdad on 2008-04-09
yes...

---

### Post by fourdigit on 2008-04-09
I tried it and pretty much the same thing happened.

EDIT: never mind, I removed a few more things and it's all better now.

Thanks man!

---

