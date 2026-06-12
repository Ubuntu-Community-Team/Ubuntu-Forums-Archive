---
title: "Can't run linux installer on Mac Mini 5,1"
date: 2012-09-16
forum: Apple Hardware Users
---

### Post by max_spb_ru on 2012-09-16
Hello, everybody.
I've spent three nights attempting to run Linux installer, but finally need an advice. I have rEFIt installed and mac was updated with latest firmware. I have no external CD drive, so my choice is USB flash Transcend 32GB.
I've already tried a different combinations of desktop 12.04/11.04, alternate 12.04, debian (everything is amd64) with unetbootin, dd and dd to hard drive partition. My favorite results:
[LIST=1]
[*]"Missing operating system"
[*]GRUB Prompt
[*]Ubuntu Unity installer's desktop is loaded, but no usb devices working (not a hung up because the clock is ticking), so it's very close, but useless as before.
[/LIST]
1) and 2) - different Unetbootin combinations. GRUB prompt is also an option for [ISO 2 USB EFI Booter for Mac]("http://www.ocztechnologyforum.com/forum/showthread.php?95640-BOOTING-UBUNTU-with-USB-on-MAC") with alternate Ubuntus and debian.
3) occurs when I use desktop 12.04(or +mac release) with "ISO 2 USB EFI Booter for Mac" from hdd partition (with USB flash drive installer crashes:
> (initramfs) could not find the ISO /efi/boot/boot.iso 
This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of removable device without first unmounting or ejecting it 
To fix this, simply reboot into Windows let it fully started, log in, run 'chkdsk /r', then gracefully shutdown and reboot back into Windows. After this you should be able to reboot again and resume the installation.)

---

### Post by shawnlyu on 2012-09-16
Man I spent two nights, waste my weekend. I guess Apple just deliberately don't wanna us to use other OS. Shame on them. 

Good luck on your installation, hope someone would help you.

---

### Post by max_spb_ru on 2012-09-17
I've decided to take one's success story and thoroughly analyze it. If I follow the "[How to create a bootable USB stick on OS X]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx")" instruction, I wonder if the third step is necessary - size and md5sum of iso and img files are the same.

---

