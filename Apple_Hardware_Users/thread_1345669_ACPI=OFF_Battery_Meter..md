---
title: "ACPI=OFF Battery Meter."
date: 2009-12-04
forum: Apple Hardware Users
---

### Post by Tuesdays on 2009-12-04
[FONT=Trebuchet MS]Everything is now working on my Macbook White 5,2... Apart from the Battery meter and the shutdown command. However yesterday I managed to get both these to work, and when I switched my laptop back on it stopped, and I can't figure out what I did to make it work, and I'm guessing it has something to do with the acpi being turned off in order for it to start. 

Is there a fix/tutorial for this for a beginner like myself as I'm not that confident on Ubuntu. Thanks in advance.[/FONT]

---

### Post by linuxopjemac on 2009-12-04
10) If it doesn't boot the GRUB menu - do a hard restart (hold down power button). Both times I installed, I had to do a hard restart at this point. This is the only time you should have too.

11) At the GRUB menu that starts after rEFIT, press E. This brings up a command list. Add acpi=off at the end of line that has your kernel version.

Looks something like this:
/boot/vmlinuz-2.6.31-14-generic root=/dev/sda3

12) Press ctrl+X to boot with this new parameter.

13) Ubuntu now boots. 

Follow this thread:
[http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758)

---

### Post by Tuesdays on 2009-12-04
I can get it too boot, it's the fact that when I apply ACPI=OFF, it makes my battery meter not work.

---

### Post by linuxopjemac on 2009-12-04
Follow the thread as I gave you:

> I have Karmic (9.10) successfully installed on my macbook 5,2 (5.2). I've got sound and graphics acceleration and function keys (except brightness) and wireless. I've also got the grub-efi working so don't have to boot with acpi=off. This gives you both cores of your processor** and gives your correct battery reading** (and it seems it reduced brightness on my screen to a tolerable level ++ ++ ).

> 1 There is a thread for configuring grub-efi the hard way (compiling from scratch). In Karmic you can install grub-efi for your platform. (I am using amd64). Just do:

sudo install grub-efi. This will pop an error most likely and give the package for your platform (i386 or amd64). sudo install that package. CD into /usr/lib/grub

You'll see a directory with your package (i386/amd64). CD into that directory. Then run grub-mkimage as root and pass the necessary options.

sudo grub-mkimage -d . -o grub.efi part_gpt hfsplus fat ext2 normal sh chain boot configfile

The above works great and will generate a grub.efi file in the directory /usr/lib/grub/whateveryourplatformis
Open up gedit as root:
sudo gedit grub.cfg

Copy and paste the following into that file (modify for your kernel version)
menuentry "UBUNTU 2.6.31-14" {
# Set the root device for Linux.
fakebios
root=(hd0,3)
# Load the loader. - other options: video=vesafb noefi
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 video=efifb acpi=force
initrd /boot/initrd.img-2.6.31-14-generic
}

menuentry "MacOSX" {
# Search the root device for Mac OS X's loader.
search --set /usr/standalone/i386/boot.efi
# Load the loader.
chainloader /usr/standalone/i386/boot.efi
}

menuentry "Boot from MBR" {
appleloader HD
}
menuentry "Boot from CD" {
appleloader CD
}
#keymapping: remeber these keys when you boot, they can be helpful!!!
#F1 = ctrl-x
#F2 = ctrl-a
#F3 = ctrl-e

save and close that.

19) Copy that ENTIRE folder onto a USB drive. I accomplished this by chmod -R 777 /usr/lib/grub/whateveryourdirectoris and then using the GUI 'finder' window to drag and drop the directory onto the USB drive.

20) Restart the computer. Boot into OSX this time.

21) Open finder and copy the directory from the USB drive into the /efi folder. The /efi folder is visible after clicking on Go > Computer.

22) Reboot

23) In rEFIT you should (will) have the new grub-efi available as bootable (the icon looks like 3 blocks stacked). Chose that and boot.

---

### Post by Tuesdays on 2009-12-05
I tried that as best as I could and when clicking the icon at the refit menu, an error message comes up saying unsupported grub.efi.

---

### Post by linuxopjemac on 2009-12-05
ask for further information to the guy who wrote the post directly, it's easier.

---

