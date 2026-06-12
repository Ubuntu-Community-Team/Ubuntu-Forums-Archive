---
title: "Asus u46e and unrealiable booting of ubuntu 11.10"
date: 2011-10-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by djpemberton on 2011-10-21
I just got a new Asus u46e. I installed a solid state hard drive on it. I repartitioned and am now dual-booting Windows 7 and Ubuntu 11.10. Windows is still working flawlessly. However, I had some problems with 11.10 booting from the beginning. 

The livecd unreliably booted. It always gets to the initial screen where you can choose whether to install or boot without installing. However, no matter what I choose, it usually goes straight to a black screen with a blinking cursor, and no further. I was able to finally boot into it, by luck, and install it. It unreliably boots into the installed system as well. In fact, it rarely boots into it at all. I get to the grub screen, but I get the same results when I try booting into Ubuntu. On the rare chance when it does boot, everything works perfectly!

I have already tried various forms of what I have found at [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/") to no avail.

Please help. Overall, I really love this computer, but it will be useless to me if I cannot run Ubuntu on it, and I would rather not have to try an earlier version.

---

### Post by drs305 on 2011-10-21
Confirm you tried adding the "nomodeset" option in the Grub menuentry and that didn't work?

When you got the CD to boot, did you have to press F6 and add any kernel options to get the CD to boot to the Desktop?

Have you tried editing the Grub menuentry to remove "quiet splash" from the 'linux' line to watch for any error messages during boot?

Can you boot the Recovery mode to the root prompt? And from there have you tried installing the nvidia drivers?

I don't know if the Boot Info Script will help (especially if it's a video issue), but running it and posting the contents of RESULTS.txt won't hurt. Click the "BIS" link in my signature line to get to the script page.

---

### Post by djpemberton on 2011-10-22
Correct "nomodeset" did nothing. After removing "quiet splash" nothing changes either, just a black screen with a blinking cursor, no text. I cannot boot into recovery mode either.

Adding "acpi=off" looks like it results in a quick boot every time. However, I then lose all networking capabilities, and other functions I'm sure. Someone had told me to try acpi=noirq, but that still resulted in the same blank screen.

What are my next options?

---

### Post by drs305 on 2011-10-22
When you were able to boot into it successfully (or do in the future), did you go to the Additional Drivers and see if there are proprietary drivers available for your system? It sounds like you are having issues with either video or the SSD, but I have no idea which, and don't even know why it would successfully boot occasionally.

If you get a Grub menu, you can find out if Grub can see your boot files by going the grub prompt (press 'c') and using the 'ls' command. Substitute values for X,Y.

ls # Shows known drives (hd0) (hd1) and partitions (hd0,1), (hd0,2), (hd1,1)
ls (hdX,Y)/ # Shows the files in the root partition on hd0,1.  vmlinuz initrd.img links
ls (hdX,Y)/boot # If the Ubuntu partition, should show the kernel and initrd.img
ls (hdX,Y)/boot/grub # For Ubuntu partition, displays lots of *.mod files and grub.cfg
Example: (hd0,6)/boot/grub

---

### Post by djpemberton on 2011-10-22
Wait, I just did the acpi=off option and it booted with networking working! Is there anything I should worry about if I make this permanent? What exactly is "acpi"?

---

### Post by drs305 on 2011-10-22
> **djpemberton said:**
> Wait, I just did the acpi=off option and it booted with networking working! Is there anything I should worry about if I make this permanent? What exactly is "acpi"?

Here is a link to some of the kernel options. A Google search may provide more details, and you might search for 'Asus u46e' and "acpi=off" to see if anyone else has experience with this issue.
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")

You can put that into your Grub configuration file so you don't have to add it manually. It would go in the "GRUB_CMDLINE_LINUX_DEFAULT=" line next to "quiet splash" in /etc/default/grub.

Add the option, save the file, then update-grub.

---

### Post by djpemberton on 2011-10-23
Thank you for your help. Everything seems to be running perfectly now. Have a slight difficulty with waking the computer back up, but I think I will find a solution.

---

### Post by drs305 on 2011-10-23
The waking issue, if you didn't have it before, could be related to the kernel option. There are other possibilities besides 'off' for acpi (and other acpi variations) and perhaps one of them might both work and assist with suspend/hibernate. You could check the other acpi options in the link I provided earlier.

Of course, whether you want to tinker depends on your level of enduring pain.  ;-)

Happy Ubuntu-ing !

---

### Post by djpemberton on 2011-10-25
Yes, "acpi=off" was causing me problems with sleep, suspend, shutdown, restart, etc. Also, my fan was continually running, and battery life wasn't good.

Changing to "noapic" or "nolapic" fixed all of these problems, except the fan and battery life, while retaining ability to boot.

Are there other boot options that may allow me to fix the fan issue?

---

### Post by drs305 on 2011-10-25
I see you have posted in the ASUS Support Forum addressing the fan issue. That's probably a good place to work on the remaining issue. I found multiple fan posts re Asus but no definitive answer to the problem. Hopefully you will get an answer by other ASUS users. Best of luck.

---

### Post by adrianoglemos on 2011-11-11
Hi!
I had the same problem. I added the "acpi=off" in the grub configurations and, until now, worked normaly!

Thanks

---

### Post by misfitpierce on 2012-01-23
I had to turn APIC off and it booted fine on a u46e. For some reason all the resolutions dont show up in the resolutions tho but im working on changing the xorg and forcing the resolutions via xrandr perhaps...

---

### Post by scottsaysmoo on 2012-06-08
Sorry about digging up a thread, but I had been having the same troubles.  After picking up a U46E earlier in the year and having trouble getting 11.10 to boot consistently/at all, I decided to just wait for 12.04 and hope that whatever the issue was would be resolved.  I too was having it hang on boot, with nomodeset providing no relief.  nolapic seemed to help, but I was hoping to get normal function!

Finally, at long last, I seem to be getting some reliable activity out of it (4 consecutive healthy boots!) so I thought I'd post my method:

flashed bios to version 206
disabled VT-d in BIOS
disabled USB WiMax in BIOS

I'm not sure if the WiMax really needed to be disabled, but then I'm not sure it ever really needed to be enabled.  After disabling VT-d, Ubuntu started up without the need for nolapic in the boot commands.

Hope this helps.

---

