---
title: "Gusty install to USB Flash Drive complete with GRUB"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-02-01
OK, so let me start by explaining my plan, then what I did, then my results, then my plea for help.

1. The Plan
I am a Windows user primarily, sometimes Mac, but am very interested in exploring Linux and therefore want to be able to dabble in it without heavily committing. I rely on a lot of programs in Windows and until I understand how to do the same things in Linux I cannot fully make the switch. So, my intention was to create a complete "persistent" installation on a USB Flash Drive that I could not get from the Live CD. I wanted to have the Windows boot loader remain the boot loader for the primary hard drive and have the option to "boot to USB" to activate GRUB and load Ubuntu. I originally desired to have a "portable" OS as well, so I could boot off of another computer in a pinch, however, I am beginning to understand that that is more complicated due to differing hardware between machines. Nevertheless, the intention was to have the Linux installation that was completely confined to a USB stick and not co-mingling with my Windows installations.

2. What I Did
-I followed a guide found online pretty much. First I booted into the LiveCD. Then I inserted the 4GB USB stick. I formatted the stick using GParted, first creating a swap space of about 500MB, then creating a ext2 partition with the remaining space. I only created the partitions here, nothing else.(Note: GParted kept crashing here everytime I did an operation on the flash drive, not sure why or if this led to any problems later)
-I then double clicked the "Install" icon on the desktop and followed the wizard. When I got to the partition section where you must designate the partitions to use, I used the ones I had created in GParted and chose a mount point of "/" from the ext2 partition as per the online guide. I confirmed later in the wizard that it was installing to the swap and ext2 partitions on the USB stick. I then finished with the install wizard. And then rebooted

3. The Results
On reboot, GRUB popped up instead of Windows bootloader. I was able to boot into the Gutsy installation I had just created with no problems. Everything with the install seemed to be fine. However, GRUB was installed to my primary hard drive's MBR and is configured so that it looks for the USB stick on boot. This means that if the USB stick in not inserted at boot, GRUB gives an error and does not give me the option to boot into Windows. ARGH!

4. My Plea for Help
Now I am dependent on having the USB stick to boot into my computer's Windows installations. Not what I had intended. I should have no problem restoring my MBR from a backup disc image but then if I obliterate GRUB, will I also lose access to the Ubuntu installation. I would naturally prefer to have GRUB on the USB stick as well, so that it remains completely independent. How can I achieve this? Will I have to start over from scratch?

Thanks for your help.

---

### Post by wolfen69 on 2008-02-01
i dont know what guide you followed, but if you had followed this: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/) you would have no problems. good luck.

---

### Post by Blue Sassley on 2008-02-01
I have Ubuntu running perfectly on a 8GB SanDisk but is how I did it was I removed my hard drive out of my laptop and then booted on the live CD with my USB drive attached and did a normal full install of Ubuntu and restarted the computer. After all was working I reinstalled my hard and now all I do to boot to my Ubuntu install is I have my USB drive connected when I turn on my laptop and either I just let it boot normally to my Windows install with the normal Windows Boot loader, or I hit the F12 for the boot menu (I have a Dell Vostro laptop so there for I have a BIOS boot menu) and select boot from USB removable disk and GRUB loads and then Ubuntu loads like normal... both have there boot loader apart from each other. And both installs are unaffected by each other.

Hope this helps,
Blue

---

### Post by onthefence on 2008-02-01
Followed this guide:
[http://ubuntuforums.org/showthread.php?t=652120](http://ubuntuforums.org/showthread.php?t=652120)

But I will try the one you linked to.
One question, I am able to follow the simple commands, but which step(s) actually install the OS?
Is it steps 13-17?
What exactly is the fix that you have to use in 19-20?

---

