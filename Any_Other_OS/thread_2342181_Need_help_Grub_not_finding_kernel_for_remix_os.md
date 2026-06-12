---
title: "Need help Grub not finding kernel for remix os"
date: 2016-11-04
forum: Any Other OS
---

### Post by Johnathan_Simpson on 2016-11-04
I followed the guide [here]("http://forum.xda-developers.com/remix/remix-os/guide-remix-os-3-0-alongside-grub2-t3487578"). I have 3 Hdd on this desktop. sda which is windows only, sdb which is for windows storage, and sdc which is my Ubuntu drive. I have Bios set to Only Boot UEFI(Don't know if that matters. Have the same issues either way). On the ubuntu drive i partitioned a space of 32gb Ext4 to install Remix OS for PC. So i Install it and inputed this grub entry

```
insmod part_gpt
insmod ext2
set root='(hd2,gpt3)'
    linuxefi /RemixOS/kernel root=/dev/ram0 androidboot.hardware=remix_x86_64 androidboot.selinux=permissive SRC=/RemixOS UVESA_MODE=1920x1080 verbose logo.showlogo=1 
    initrdefi /RemixOS/initrd.img
```

 but when it boots i get error disk hd2,gpt3 not found. but if i change it to this

```
insmod part_gpt
insmod ext2
set root='(hd2,3)'
    linuxefi /RemixOS/kernel root=/dev/ram0 androidboot.hardware=remix_x86_64 androidboot.selinux=permissive SRC=/RemixOS UVESA_MODE=1920x1080 verbose logo.showlogo=1
    initrdefi /RemixOS/initrd.imgit
```

says error /RemixOS/kernel not found. is this not pointing correctly to the remix OS files or is this not a grub issue?

---

### Post by ajgreeny on 2016-11-04
*Thread moved to **Any Other OS**.* which is more appropriate for the problem and should be a better fit.

Unfortunately I do not know anything about running RemixOS, which is based on Android, as far as I can see.

---

### Post by oldfred on 2016-11-04
Looks like you have a BIOS boot stanza, but if other installs are UEFI is your RemixOS an UEFI install?

You can run from Ubuntu install or live installer. Not sure of RemixOS has all the same utilities it needs or not.
       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Johnathan_Simpson on 2016-11-05
Ok [Here]("http://paste2.org/Zh7ObIJJ") is the Boot-Info. And they are all installed via UEFI

---

### Post by oldfred on 2016-11-05
Boot-Repair points this out:
> SFS detected. You may want to retry after converting Windows dynamic partitioning (SFS partitions) to a basic disk. This can be performed via tools such as TestDisk or EASEUS-Partition-Master / MiniTool-Partition-Wizard.

 	Do you want to continue?


SFS is dynamic partitions. It is a proprietary Windows partitioning scheme somewhat like Linux's LVM. Used as a work around for the 4 primary partition limit on MBR(msdos) partitions.
But both of your other drives are gpt which has no 4 partition limit, either.

Best to undo SFS/dynamic and maybe convert to gpt.
[https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

It looks like you have installed the 32bit UEFI version of RemixOS?
/EFI/RemixOS/bootia32.efi

Separate question?
Was Ubuntu on sda when you installed it. As UEFI has only installed to ESP on sda, but you now have ESP on sdc for Ubuntu only.

---

### Post by Johnathan_Simpson on 2016-11-05
> [COLOR=#000000]Was Ubuntu on sda when you installed it. As UEFI has only installed to ESP on sda, but you now have ESP on sdc for Ubuntu only.[/COLOR]
It was the only drive in the computer when installing Ubuntu.

> [COLOR=#000000]Best to undo SFS/dynamic and maybe convert to gpt.[/COLOR]
Did this been looking for a way to do that. I guess i looked past the obvious choice. 

> [COLOR=#000000]It looks like you have installed the 32bit UEFI version of RemixOS?[/COLOR]
[COLOR=#000000]/EFI/RemixOS/bootia32.efi[/COLOR]
I am using the installer and the ISO of remixos 64bit. If i "Reboot to Android-x86" it boots but after a restart nothing.

---

### Post by oldfred on 2016-11-05
Guess I just do not know enough about how RemixOS works to know what else to suggest.

Often when all else fails, you can copy boot stanza from the other operating system into grub2's 40_custom. 
I normally turn off os-prober, and only use copies (often my own) to boot as I have several old Ubuntu installs still on system that I do not want in grub menu.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by Johnathan_Simpson on 2016-11-05
Well after reinstalling ubuntu with other drive connected and changing sda back to gpt still same result.
[Here]("http://paste2.org/4F3gCmM6") is the new Boot-Info if it helps any.

I had this working and if i install it on windows partition i can boot it from Windows boot manager. but i was hoping to boot it from grub and skip that part. Maybe if i copy and paste the windows entry and try that?

---

### Post by Bucky Ball on 2016-11-05
Just some thoughts and a suggestion. I know this doesn't solve your specific problem posted here, but your computer sounds like it has a bit of grunt. Tried running RemixOS as a virtual machine using Virtualbox in one of your existing installs? I was playing around with it a couple of months ago and had it installed and up and running as a virtual machine in no time flat. No issues. Ran perfectly. 

I have no idea how RemixOS works as a full install to hard drive either but to others, yes, it is 'Android for the PC', more or less. There were problems with it, for me at least, but not in the actual day-to-day operation. Annoying things like, as it's NOT on a phone, there is no GPS on my computer. Therefore, I am locked to the US location. After a couple of days of searching for a fix to change the location, I gave up. I'm in Australia and was only using RemixOS for one sporting web site ... which would only run if the geolocation thingy could see 'Australia'. 

Also, if you have a 16:9 widescreen, remember, RemixOS is _Android_ which is for a _phone_. In other words, the RemixOS screen is thin and tall, not squat and wide, and you can't simply turn your computer screen and have the desktop screen adjust like a phone. Consequently, you spend most of your time scrolling up and down rather than getting things done. I had no end of twiddling trying to get the screen right also, to no avail. :| 

So, unless you live in the US and have a screen you can turn (they do exist) or you can do a better job of fixing the issues I outlined above than I did, you may not be that overjoyed with what you get when you get there anyway. It was four or five days of fiddling I'll never get back, although I did learn some things, but hoping things go better for you and RemixOS. A nice idea to get Android to the PC, but some way to go for mine. :)

Good luck.

---

### Post by Johnathan_Simpson on 2016-11-10
Have a question. I noticed that all the guides for this say to modify the 40_custom in /etc/grub.d but there isnt a 40_custom in said directory. but there is one in the backup folder of said directory. when i open that backup 40_custom i get the words that are suppose to be there. but if i add the remix entry there i have to use a live usb to repair boot cause it wont boot. Could this be related to my concern?

---

### Post by oldfred on 2016-11-11
@Johnathan_Simpson
Probably better to start your own thread.
But did you use grub-customizer? That creates its own scripts and backups up the standard scripts. The backups should not be set to run, otherwise you get duplicate entries.

---

### Post by Johnathan_Simpson on 2016-11-12
Ok well it sounds like that was the info i was looking for grub-customizer goes nuts if you move them. thanks... where is the thanks button?

---

### Post by Bucky Ball on 2016-11-12
There is no 'thanks' button but there is a 'solved' button you can use when the issue is solved. 

If/when it is solved please give a clear description of how you did it then mark as 'solved' using Thread Tools at top right or follow the link in my signature at the bottom of this post.

Thanks.

---

