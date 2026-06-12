---
title: "grub-mkstandalone error"
date: 2016-10-15
forum: Apple Hardware Users
---

### Post by randym-axcess on 2016-10-15
Greetings all,

I am installing Ubuntu 14.04.LTS on my Mid-2009 MacBook Pro. I used the instructions located here: [How To Dual Boot OS-X and Ubuntu]("http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf")

I was successful in my install but, I did not make it bootable; while still in my live DVD instance of Ubuntu I should have opened Terminal but, instead, I was prompted to restart; the Mac booted back into OS-X.

I restarted Ubuntu with the Ubuntu-Live DVD and, attempted to complete my install and make the laptop dual boot. 

[FONT=arial black]> Part 4: Making Ubuntu bootable[/FONT]> 
 
We're now at the home stretch. Ubuntu has been installed on your computer, but you won't be able to boot into it since there's no EFI boot loader, needed for Mac firmware to recognize the OS as bootable. So, we need to go into the Ubuntu installation and create a boot.efi file that we'll use to boot it. While still inside your live USB instance of Ubuntu, open up a Terminal window, and run the following command to mount the ext4 partition you created at the path /mnt:
 
**sudo mount /dev/sdaN /mnt**
 
You'll also need to mount several of the top-level directories, which is easiest to do with the command:
 
**for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done**
 
Now, we can use the chroot command to change our root directory to /mnt, so that the bash session
in the Terminal is effectively running inside the Ubuntu installation:
 
**sudo chroot /mnt**
 
This allows us to configure GNU GRUB, the "GRand Unified Bootloader," with:
 
**grub-mkconfig -o boot/grub/grub.cfg**
 
and then save this to a standalone file with:
 
**[SUP]grub-mkstandalone -o boot.efi -d usr/lib/grub/x86 64-efi -O x86 64-efi --compress=xz boot/grub/grub.cfg[/SUP]**[COLOR=#008000][SIZE=2][FONT=arial black]"root@ubuntu:/#[/FONT][/SIZE][/COLOR][B][SUP][SIZE=2][COLOR=#008000][FONT=arial black]grub-mkstandalone -o boot.efi -d usr/lib/grub/x86 64-efi -O x86 64-efi --compress=xz boot/grub/grub.cfg"[/FONT][/COLOR][COLOR=#800080][FONT=arial black]
[/FONT][/COLOR][COLOR=#ff0000][FONT=arial black]"grub-standalone: error: usr/lib/grub/x86_64-efi/modinfo.sh doesn't exist. Please specify --target or --directory."[/FONT][/COLOR][COLOR=#800080][FONT=arial black]
[/FONT][/COLOR][/SIZE][/SUP][/B]
[COLOR=#ff0000]
[SIZE=4][FONT=arial black]This is where I am stopped at:
[/FONT][/SIZE][/COLOR]
 
> You can then exit the chrooted partition with the exit command. The boot.efi file is still in the new
installation, however, so you'll have to use the cp command to copy it to somewhere like ~/Documents/,
from which you can move it to somewhere you can access it from OS X, such as another USB drive or Google Drive:
 
**cp  /mnt/boot.efi ~/Documents/**
 
Once you've saved this file, you can reboot your Mac to OS X.
Back in OS X, we want to open up a Terminal window, and cd into the boot loader partition we created
earlier: 
 
**cd  /Volumes/Ubuntu\** **Boot****\ ****Loader/**
 
In order to make this recognizable by Apple's firmware, we have to create the mach kernel and System/
Library/CoreServices directories, the latter of which will store our boot.efi file from before, along with a
“SystemVersion.plist" file which provides configuration information. The commands to do this are as follows:
 
**sudo mkdir System mach kernel**
**cd System**
**sudo mkdir -p Library/CoreServices ****(the ****-p ****option tells ****mkdir ****to create intermediate directories)**
**cd Library/CoreServices**
 
Now, we copy boot.efi to the CoreServices folder. If you uploaded it to Google Drive like I did, you can then download it from OS X, and then copy it from your Downloads folder with:
 
**Sudo cp ~/Downloads/boot.efi ./**So, I followed all directions but, it seems that some files were not created or, I am not accessing them from my "live instance".

When I boot the Mac with the alt key down, it gives me the option to boot from my system, my recovery but, not my installed Ubuntu.

---

### Post by deadflowr on 2016-10-16
*Thread moved to **Apple Hardware Users**.*

Don't you still need to have the full path including the /(root level symbol).
As in /usr/lib/grub/x86_64-efi,
instead of 
usr/lib/grub/x86_64-efi

---

### Post by randym-axcess on 2016-10-16
> **deadflowr said:**
> *Thread moved to **Apple Hardware Users**.*

Don't you still need to have the full path including the /(root level symbol).
As in /usr/lib/grub/x86_64-efi,
instead of 
usr/lib/grub/x86_64-efi

[COLOR=#008000][SIZE=2][FONT=arial black]"root@ubuntu:/#[/FONT][/SIZE][/COLOR][B][SUP][SIZE=2][COLOR=#008000][FONT=arial black]grub-mkstandalone -o boot.efi -d /usr/lib/grub/x86 64-efi -O x86 64-efi --compress=xz boot/grub/grub.cfg"
[/FONT][/COLOR][COLOR=#800080][FONT=arial black]
[/FONT][/COLOR][COLOR=#ff0000][FONT=arial black]"grub-standalone: error: /usr/lib/grub/x86_64-efi/modinfo.sh doesn't exist. Please specify --target or --directory."

[/FONT][/COLOR][/SIZE][/SUP][/B]Same result......

Just to check, I am at root@ubuntu/#

I enter command "cd /usr/lib/grub

now in root@ubuntu:/usr/lib/grub#

root@ubuntu:/usr/lib/grub# ls

Grub folder is populated but, no file with ".sh" extension.

---

### Post by randym-axcess on 2016-10-18
> **randym-axcess said:**
> [COLOR=#008000][SIZE=2][FONT=arial black]"root@ubuntu:/#[/FONT][/SIZE][/COLOR][B][SUP][SIZE=2][COLOR=#008000][FONT=arial black]grub-mkstandalone -o boot.efi -d /usr/lib/grub/x86 64-efi -O x86 64-efi --compress=xz boot/grub/grub.cfg"
[/FONT][/COLOR][COLOR=#800080][FONT=arial black]
[/FONT][/COLOR][COLOR=#ff0000][FONT=arial black]"grub-standalone: error: /usr/lib/grub/x86_64-efi/modinfo.sh doesn't exist. Please specify --target or --directory."

[/FONT][/COLOR][/SIZE][/SUP][/B]Same result......

Just to check, I am at root@ubuntu/#

I enter command "cd /usr/lib/grub

now in root@ubuntu:/usr/lib/grub#

root@ubuntu:/usr/lib/grub# ls

Grub folder is populated but, no file with ".sh" extension.

<figured out>

The error message was quite direct in pointing me to the problem; there was no "/[SUP][COLOR=#FF0000][FONT=arial black]x86_64-ef[/FONT][/COLOR][COLOR=#FF0000][FONT=arial][SIZE=3]i[/SIZE][/FONT][/COLOR][FONT=arial][SIZE=3][COLOR=#000000]/" [SIZE=2]in the/grub folder but, there was a i386 folder in there. 

[/SIZE][/COLOR][/SIZE][/FONT][/SUP][COLOR=#008000][SIZE=2][FONT=arial black]root@ubuntu:/#[/FONT][/SIZE][/COLOR][B][SUP][SIZE=2][COLOR=#008000][FONT=arial black]grub-mkstandalone -o boot.efi -d /usr/lib/grub/i-386 -O i386-efi --compress=xz boot/grub/grub.cfg"

[/FONT][/COLOR][/SIZE][/SUP][/B][FONT=courier new][SUP][SIZE=2]No error.[/SIZE][/SUP]

[/FONT]

---

