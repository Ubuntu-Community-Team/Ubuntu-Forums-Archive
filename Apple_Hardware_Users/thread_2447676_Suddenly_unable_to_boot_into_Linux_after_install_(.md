---
title: "Suddenly unable to boot into Linux after install (black screen) on Macbook Pro 2,2"
date: 2020-07-23
forum: Apple Hardware Users
---

### Post by josephjwilk on 2020-07-23
Hello all,

I am a Linux beginner who has a late 2006 Macbook Pro (2,2) that I recently started using as a Linux machine as part of a renewal process. After reviewing a wide variety of documentation to rectify the 32-bit bootloader issue, I was able to develop the following process that allowed me to test a variety of Linux variants, ultimately settling on successfully installing Lubuntu 19.10:


[LIST=1]
[*]Download distribution ISO
[*]Use UNetbootin to create a bootable USB
[*]Drag a *bootia32.efi *file into the EFI/boot directory
[*]Hold option to choose the USB as a bootable device
[*]Edit the grub entry to replace 'quiet splash' with 'nomodeset' as boot options
[*]Reboot to Linux installation on hard drive
[*]Press ESC to load grub menu and edit as per #5
[*]Edit the file at */etc/default/grub*
[*]Run the **update-grub** command
[*]Reboot and enjoy!
[/LIST]

After a while of using Lubuntu, something I did seemed to have broken audio (I was unable to get sound anymore, and none of the fixes I found online were relevant or seemed to work), so I followed the same strategy to successfully install Ubuntu 16.04 LTS. That was a bit too resource-intensive, so I thought I would try Kubuntu again as a middle-ground. And that's where I am having my problem.

I am able to successfully follow the above instructions up to and including #7. However, after I hit F10 to continue, it goes right to a black screen. I have tried following the "Troubleshooting Flow Chart" of the [stickied thread]("https://ubuntuforums.org/showthread.php?t=1743535"), attempting to boot into a text console through **nosplash --verbose text**, by appending **3 **to the boot options, and going into **Advanced Options > recovery mode** in order to access the shell prompt. None of these options allow me console access.

Does anybody have any additional insight about next steps to take? I am so lost as to how I am suddenly unable to utilize the same processes that were previously successful. I have attempted this with Xubuntu, as well as the flavors I'd installed previously, and I am lost for what to do. Thank you in advance for any time and consideration.

Kindly,
Joseph

---

### Post by TheFu on 2020-07-23
Support for 19.10 ended. That's all I know. 

If it is a 32-bit thing, then 18.04 is the only answer that I know. 32-bit support has been dropped from the normal Ubuntu. Some of the lighter Ubuntu flavors may retain 32-bit support, but IDK which, if any do.

No clue whether that model has a PowerPC or Intel CPU.

---

### Post by josephjwilk on 2020-07-25
Hello, thank you for your reply. Lubuntu 19.10 just happens to be the only distribution I am successfully able to install (I am able to then upgrade through the console, but I am unable to run an installed Lubuntu 20.04 or any other distro I've tried except for Ubuntu 16.04). I just can't figure out what is wrong&#8212;especially when it's not like I can't get *any*distro to work.

---

### Post by wildmanne39 on 2020-07-25
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by danish-bronco on 2020-08-27
Xubuntu 18.04 32-bit installed OK on my EARLY 2006 MacBook Pro (1,1), but then it's restricted to 32-bit software anyway. Yours embarks a 64-bit-capable CPU, so it's a matter of enabling efi32, either on boot by adding an argument, or by slip-streaming it into your ISO prior to copying it onto your USB thingy. 

AFAIK, your Mac has a 64-bit CPU, but the EFI itself is 32-bit. Alternately, you can format your USB stick as GPT instead of MBR.

---

