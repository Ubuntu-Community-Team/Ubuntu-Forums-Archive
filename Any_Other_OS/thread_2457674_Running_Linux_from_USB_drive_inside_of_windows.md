---
title: "Running Linux from USB drive inside of windows"
date: 2021-02-06
forum: Any Other OS
---

### Post by robertsaron on 2021-02-06
I want to run some linux distro from a USB drive inside of windows, with out rebooting, and/or making changes to the BIOS.  I have spent hours and hours all over the internet looking. I have not been able to find out how to do this. I have tried several walkthroughs, for QEMU, Virtual Box Portable, and while very handy, they are out of date. 

Basically a virtualized container on a USB drive, that does not require admin privileges in windows. Once done, I close the or remove the USB drive, and I am done. I would like this USB drive to have persistent data. 

I am posting this here As I have no idea where else to go.

---

### Post by CelticWarrior on 2021-02-06
Any virtualization software can do that and the actual VM can be anywhere including a removable USB drive thus making it portable.

---

### Post by TheFu on 2021-02-06
Seems like a Windows limitation in your situation.  Any Unix-based host would have the same issue.

A hypervisor will need root/administrator access, so those are out. You said you tried QEMU, which I've used before, but I don't think network settings on the host computer can be configured in either NAT or bridge modes, so having a running Linux, without any networking would be nearly useless.

I don't see how it would be possible.

Another alternative would be to setup a tiny Linux VPS and use the internet to connect to it from Windows.  Then you could use the built-in ssh subsystem on Window10 or some "portable" ssh terminal, like putty. Short of that working, the networking aspects, which need admin rights to modify, just don't work otherwise.

---

### Post by C.S.Cameron on 2021-02-07
If Microsoft **Hyper-V** is installed on your computer, VirtualBox, QEMU or any other good virtualization software will not work.

I did not have good luck with Virtual Box Portable, it disabled my installed version of VBox every time I used it.

---

### Post by TheFu on 2021-02-07
> **C.S.Cameron said:**
> If Microsoft **Hyper-V** is installed on your computer, VirtualBox, QEMU or any other good virtualization software will not work.

I did not have good luck with Virtual Box Portable, it disabled my installed version of VBox every time I used it.

Only one hypervisor can have exclusive control (mandatory) of the VT-x/AMV-v CPU extensions at a time. For most people, this means only 1 can be installed at a time.

QEMU doesn't use those CPU hardware extensions. It does the CPU/machine spoofing in software, so we can run QEMU (not KVM-QEMU) just fine. It is slower, however. Much slower.  But if you need to emulate a MIPS CPU on intel or AMD hardware, it is the only way.

---

### Post by aandmsantos0910 on 2021-12-10
This is the closest I could find, not from USB but withing windows: [https://www.pcgamer.com/linux-in-windows-10/](https://www.pcgamer.com/linux-in-windows-10/)

---

### Post by Skaperen on 2021-12-11
i'm guessing that what OP wants to do is run Linux under Windows with a particular USB storage device as the single device Linux accesses.  so, in theory, the Linux system on that storage device can be booted on any compatibly configured PC.  the 2 issues i see:

1. will the non-VM Linux in Windows allow you to boot any boot loader and kernel desired, or is Linux in Windows limited to running a customized kernel image that it loads by its own means that can interface to Linux in Windows.  if so limited, you will most likely need to run a regular virtual machine.
2.  you most likely need Administrator authority to "assign" access to the particular USB bus and device (or maybe the whole bus) to the user running the virtual machine.

FYI, i have done this running QEMU under Linux.  i had sudo access, too.  my USB storage device was one of a few flash memory sticks i have in 8GB and 32GB sizes.  i did this with Slackware on my old Xeon box.  i was working on custom automation of the process to build the image that was recorded in whole to the whole storage device (the image started with the MBR partition table and SYSLINUX boot loader).

---

### Post by TheFu on 2021-12-11
Folks, excellent necro posting. This thread is from last February.  The op should have responded or started a new thread since then.

---

