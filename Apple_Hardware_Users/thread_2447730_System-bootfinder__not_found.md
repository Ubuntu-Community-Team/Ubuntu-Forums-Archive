---
title: "System-bootfinder  not found"
date: 2020-07-24
forum: Apple Hardware Users
---

### Post by aldo82 on 2020-07-24
Hello,
unable to boot on dual mode on my macbook 2008 , 10.6.8 snow leopard, dual mode, ubuntu 16.04  LTS
There is only the message: "System-bootfinder not found .Creating boot entry 0009.
Load image failed." 

How to recover the EFI of the Apple HFS partition?

Thanks in advance

Aldo

---

### Post by gsahli on 2020-08-08
A little more info, please. Are you trying to get into Ubuntu or into MacOS? "boot on dual mode" doesn't mean anything to me. Do you mean it has dual boot capability?
Which OS CAN you boot into? Or neither?
Look here:
[http://www.linuxandubuntu.com/home/ways-to-rescue-or-recover-grub-menu](http://www.linuxandubuntu.com/home/ways-to-rescue-or-recover-grub-menu)

---

### Post by aldo82 on 2020-08-15
I could resolve the booting issue on the ubuntu partition, but I can't
boot from my 10.6. 8. dvd. There is a message:"Kernel panic 
at booting," followed by many digits.

---

### Post by este.el.paz on 2020-08-16
> **aldo82 said:**
> I could resolve the booting issue on the ubuntu partition, but I can't
boot from my 10.6. 8. dvd. There is a message:"Kernel panic 
at booting," followed by many digits.

"Kernel panic at booting" from OSX is . . . "not good" . . . it generally means there is "corruption" in the system . . . soft or hardware--the system determines it is "unsafe or unable to boot the computer."  Might be that the HDD is "dying"??  Do you have SMARTReporter installed in either OSX or ubuntu??  There is a linux app that has a similar name and it does give more details on the state of the drive.

Question is if you are trying to boot the "10.6.8 dvd"  why is it not booting into the installer???

I have an '09 MBP and I replaced the HDD with an SSD at least a year or so back . . . it's pretty easy to do that . . . of course you'd have to re-install ubuntu . . . .  Otherwise there isn't too much "support" around for 10.6.8 . . . I have a "triple boot" install in my 500 GB SSD . . . I also still have the OEM 10.6.8 in one smaller partition, a 10.11 (max upgrade w/o patcher) and possibly Manjaro MATE in the third . . . .

Good luck with it.

---

### Post by aldo82 on 2020-09-10
I have this issue  since i tried Qubuntu 20.4. on a live USB flash drive.
There was a system crash and later I could not boot, neither on Ubuntu nor 
on Mac partitions.

It was easy to restore  the Ubuntu partition thanks to Linux boot-repair. But as to
the 10.6. 8. partition the log in failed  though I used the DVD.

Is there a boot repair for Mac similar to Linux boot repair?

Many thanks in advance

Aldo

---

### Post by aldo82 on 2021-07-18
Finally, I found a solution. I used my 16.04 flash drive to boot 
my 2008 iBook pressing alt. Then I booted my 10.6. 8 partition.
Next step was to repair the permission using utilities. 
I rebooted the device, pressing the alt key and selected the mac partition
using the arrows on my keyboard.  That's all.

I guess, it's a good way to use old computers as archives 
for running apps, Rosetta for instance, you won't found
on current macOS versions anymore.

---

