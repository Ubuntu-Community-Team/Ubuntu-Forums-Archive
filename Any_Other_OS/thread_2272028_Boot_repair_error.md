---
title: "Boot repair error"
date: 2015-04-03
forum: Any Other OS
---

### Post by marcotx on 2015-04-03
Hello, 
 
on my laptop I have one hd with the following partitions and installed OS: 
 

[LIST]
[*]sda1 – Windows 7 
[*]sda2 – BackBox Linux 
[*]sda3 – Arch Linux 
[*]sda4 – Extended, no OS 
[*]sda5 – Linux Mint 
[*]sda6 – swap 
[/LIST]
 
I’m not able to have a working grub with all the above OS selectable. 
In particular I can have in the grub list only sda1, sda2, sda5 or sda2, sda3, sda5. 
It’s impossible to have both sda1 (Win7) and sda3 (Arch) both present in grub list. 

Here is my boot repair log: [http://paste.ubuntu.com/10729909/](http://paste.ubuntu.com/10729909/)
I used boot repair from an Ubuntu Live. 

I have tried all the options of boot repair without success. 

If I try to install grub in the partition where Arch Linux is, boot repair told me to insert this commands from terminal: 

sudo chroot "/mnt/boot-sav/sdb3" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sdb3" pacman -R --noconfirm grub*-common

I've tried but the first command gives me the following error: 

chroot: failed to run command ‘dpkg’: No such file or directory

and the second command gives me the following error: 

error: target not found: grub*-common


Please can you help me to solve this problem? 
 
Thank you
Marco

---

### Post by bardo2 on 2015-04-03
Wow! Although it is a hobby of mine to "play around" with all kind of OS'es, i did not come across all of yours, and anyway, i wouldn't say. i am comfortable with each and everyone. :-(
But... from my reading of your bootinfoscript output, i could comment on several observations:

You seem to be using MBR partitioning all over the place, which wouldnt have been my choice for such a configuration in the first place, as it will make future partition handling (a.k.a. resizing) so much more difficult. Maybe, there is a reason for you to deal with that complication - i don't know - but anyway: that is NOT the problem right now!

From the generated {something}/grub.cfg files attached, i could see, that grub2 (a.k.a. 1.99) is in fact able to boot to each and every OS, which can be verified easily by booting into each one manually using grub commandline. This leaves the problem to the generated grub.cfg files themselves. - Yet - do NOT edit those, except for experimental purpose!

This suggests, that some OS (i can't say, which one) might have problems to generate the proper entries for grub.cfg. I experienced such problems myself, because the /etc/grub.d/* files provide quite a number of limitations, and even grub itself has some. (this hints us to maybe someday try to get a more recent grub to the one provided by distributions?)

BUT: There is a solution, requiring some understanding of your system and of grub2 architecture, and since you seem to be almost happy with your system, you might want to opt for it: fix your grub2-config for good by filling in the parts, some OS is missing right now. And since you have access to all partitions from the rescue disk, that ought to be doable without having to reinvent the wheel. Yet, it requires attention and care, because messing with grub can easily render some system unable to reconfigure itself properly, thus making it even harder to sort it out.

My own experience with grub2 files is limited to tiny adjustments, i did mess with it once and had a hard time recovering from it, the best thing i ever made was to provide an automatic for booting from ISO files nicely integrated with boot (just a submenu there), and i have a sort of "workaround" in my current system running, because i am running into grub's limitations myself, which might be a solution for you as well (although less nice): On my system, i have a tiny partition created manually containing nothing more than the files necessary to get grub booted from it and i MANUALLY edited THAT grub.cfg to contain a little menu basically saying:

"do not boot from the current config, but boot from the configuration found at another location". see this example how you would access your config from MINT
```
menuentry 'use grub menu from distrbution MINT' {
	insmod part_msdos
	insmod ext2
        set root='hd0,msdos5'
        configfile /boot/grub/grub.cfg
}

```
So, you could manually create those redirections and while booting, select from which system generated grub config you'd proceed. This is pretty darn future-proof, doesnt force you to repair grub2 at all, but allows you to live with the limitations of each OS distribution, until you feel able to fix it.

I am sure, this high-level suggestion isnt what you want right away, but you seem to be comfortable at creating/resolving harder problems than this, right?

edit: recommendation
[LIST=1]
[*]backup the current state
[*]create an aditional tiny partition (8 MB should be enough)
[*]install grub to it manually and manually set up grub.cfg in there
[*]Test config from commandline
[*]on success, make change permanant by using grub-install to have the system pointing to your "redirection/chooser-area"
[/LIST]

edit2:
maybe i should add this: I personally wouldnt rely on any boot-repair option from your rescue media. It has not been designed with such a difficult config in mind, so do not expect its actions to work. Go for manual resolution instead. (see above) - i killed one of my installations with boot-repair, and i guess, that is a known problem anyway.

---

### Post by oldfred on 2015-04-03
I have used bardo's suggestion of configfile and also used the links that Debian based installs have to most current kernel in /  to boot an install instead of a specific kernel.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

But it looks like you tried to use Boot-Repair to configure the grub from Arch which is the oldest version of grub.
And it looks like the grub installed to the MBR is from BlackBox and does not include os-prober. So the only way you can boot other installs is to manually add entries to 40_custom.
And it looks like you left Windows either hibernated or needing chkdsk when you installed verision with os-prober as they gave that error.

Which install do you boot the most often? That should be the one you have in control of MBR and is the grub menu you load. Then you edit it to include all other installs if it does not have or if os-prober does not work.

---

### Post by marcotx on 2015-04-07
I would like to use Arch and Windows, but I'm not able to do it. 
I'm only able to have one of them with the other distros. 
Maybe can I try to install another boot manager? Which one, Syslinux? 
Actually I have BackBox, Mint and Windows working, but I would like to have Arch, Windows and Mint working. 
The laptop has UEFI sysem and I have set it to Legacy mode. 
If needed I can also delete BackBox and Arch and then install again Arch.

---

### Post by oldfred on 2015-04-07
It looks like Boot-Repair is trying to use dpkg. I assume that is not Arch's package manager.

But you should be able to just copy any grub2 boot stanza into whatever install's grub is in MBR.
Not every install has os-prober that creates boot stanza's automatically. You have to create your own or copy from one of the installs that does.

Your pastebin shows the install in sdb2 or Blackbox is the grub in control.
You should be able to boot into either Arch or Mint and install its copy of grub to MBR.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

And if that does not have all the versions you want copy boot stanza into 40_custom from one that does work.

---

### Post by marcotx on 2015-04-08
First of all, thanks for your help! 

As suggested by oldfred I writed: 
 
sudo fdisk -l

and the reply was: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x87c20926

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195315966    97657952    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       195317760   236277759    20480000   83  Linux
/dev/sda3       236277760   431589375    97655808   83  Linux
/dev/sda4       431591422   625141759    96775169    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       431591424   587839487    78124032   83  Linux
/dev/sda6       587841536   625141759    18650112   82  Linux swap / Solaris

So I then writed: 

sudo grub-install /dev/sda

and the reply was: 

Installation finished. No error reported.

After that I try to reboot the laptop but at the grub screen I have the same same situation as before: 

Linux Mint 13 Cinnamon 64-bit, 3.2.0-23-generic (/dev/sda5)
Linux Mint 13 Cinnamon 64-bit, 3.2.0-23-generic (/dev/sda5) -- recovery mode
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Ubuntu, with Linux 3.8.0-30-generic (on /dev/sda2)
Ubuntu, with Linux 3.8.0-30-generic (recovery mode) (on /dev/sda2)

So no way to have also Arch Linux bootable...

---

### Post by marcotx on 2015-04-08
Sorry I forgot: first of all I booted with Linux Mint (/dev/sda5), so grub was installed from that system

---

### Post by oldfred on 2015-04-08
I thought os-prober was part of Mint. Or if os-prober is not finding it just add the Arch boot stanza to 40_custom. (from your summary report of Arch's boot stanza)

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

       gksudo gedit /etc/grub.d/40_custom
or
sudo nano /etc/grub.d/40_custom
Then do:
sudo update-grub

    
```

menuentry 'Arch Linux, with Linux core repo kernel' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-core repo kernel-true-ed93d968-bd5e-4d39-ba13-9536e27aa648' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  ed93d968-bd5e-4d39-ba13-9536e27aa648
    else
      search --no-floppy --fs-uuid --set=root ed93d968-bd5e-4d39-ba13-9536e27aa648
    fi
    echo    'Loading Linux core repo kernel ...'
    linux    /boot/vmlinuz-linux root=UUID=ed93d968-bd5e-4d39-ba13-9536e27aa648 rw  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initramfs-linux.img
}
```

---

### Post by marcotx on 2015-04-08
Thank you very much oldfred, it works!

---

### Post by oldfred on 2015-04-08
It looks like Arch had several other boot stanza for various options, you can add those the same way.
And if kernel changes, you have to manually update your boot stanza.

---

### Post by marcotx on 2015-04-09
Ok, so to add a boot stanza I have to insert it in /etc/grub.d/40_custom file. 
But to modify a boot stanza what file must I edit?

---

### Post by oldfred on 2015-04-09
If Arch updates its own boot stanza, you can copy it again with the newer boot stanza into 40_custom. 

Usually just the kernel version and you can just edit that also in 40_custom rather than copy entire stanza.
Update:
Looked again at Arch boot stanza and it does not seem to show version numbers, so perhaps updates not required. But then you may need some of the other boot stanzas it has as ways to boot backup or repair? Do not know about Arch and how it works.

---

