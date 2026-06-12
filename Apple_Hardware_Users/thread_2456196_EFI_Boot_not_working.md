---
title: "EFI Boot not working"
date: 2021-01-06
forum: Apple Hardware Users
---

### Post by jablocher on 2021-01-06
Hi -
I'm a newbie to Linux using it to bring life to my old (2008) iMac. 

Long story short, I had 18.04 LTS installed and working just find pre-pandemic (~March 2020). Then, I booted it up again last week and the computer fails the fsck check. I was able to run it in recovery mode to run fsck and repair the error but now I still can't get the computer to boot. 

But then, I don't get the install/recovery mode/etc menu to come up. It is like it bypasses the USB boot (after it shows me the EFI menu?) and just boots from the machine's hard drive. 
Right after I click the Up Arrow, I get a message that (very quickly!) says "System BootOrder not found. Initializing Defaults." or something like that. It just flashes on the screen. Then, the computer just hangs on a maroon screen with a cursor in the upper left corner. 

I'm happy to fully reinstall the OS - it is just a computer for my kids who use browser-based apps. But right now I can't because it won't keep reading the USB drive to continue the process. 

Help? Right now the computer is completely unusable.

---

### Post by howefield on 2021-01-06
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ajgreeny on 2021-01-06
I believe some old Mac machines were 32bit and that can cause big problems with attempts to use Linux on them using EFI.

I can't help any more with this as I have never used any Apple machines, but it may be worth investigating this possibility further.

---

### Post by oldfred on 2021-01-06
I do not know Mac, but have this in my notes:
Pre-2008 Macs mostly have IA32 EFI firmware while >=2008 Macs have mostly x86_64 EFI. All Macs capable of running Mac OS X Snow Leopard 64-bit Kernel have x86_64 EFI 1.x firmware. 

Installed Lubuntu 18.04 LTS on a MacBook Air 1,1 (early 2008) 
[https://ubuntuforums.org/showthread.php?t=2402179](https://ubuntuforums.org/showthread.php?t=2402179)

---

### Post by jablocher on 2021-01-06
I had Ubuntu 18.04 LTS running on it already for months pre-COVID, so I don't think it is an architecture issue.

---

### Post by jablocher on 2021-01-08
FWIW: I tried a USB boot of an old Mac OS X image and that worked for some reason. As I said, I don't think it is an architecture issue because I ran 18.04 LTS for months on this computer before I had this issue. Or, maybe there is something about architcture I don't understand where it can run for a while but be unstable? I don't know. The computer is currently running fine on a Mac OSX and I'll likely reinstall Linux shortly since the old OS X (Mountain Lion, maybe 10 years old) won't run many new applications.

---

### Post by gsahli on 2021-01-16
Try this: (if you haven't damaged the Ubuntu drive, but it may also show the USB if you need it.)
Power on
Immediately hold down the Option Key and hold it until you see the Mac's boot selector come up
Select the Ubuntu disk for boot and then click on the right arrow to start the boot.
After doing this once, you should get the ubuntu grub boot picker each time. If not, your backup battery may be dead. It remembers boot drive, system time, screen resolution, etc.

---

### Post by jablocher on 2021-01-18
I didn't try this, but I did end up fixing the issue. I had to re-install an old Mac OS X (Mountain Lion) which got the computer to boot again. Then, I partitioned the drive and installed Ubuntu 18.04 again maintaining the dual boot option.

---

