---
title: "Need dd IMG of x86_64 11.04 install"
date: 2011-09-12
forum: Apple Hardware Users
---

### Post by devoda on 2011-09-12
Good day,
I need a dd img (including bootloader) of a standard 11.04 ubuntu 64-bit install. My mac's superdrive died so I cannot install from CD myself.  I have purchased a second hard drive. I would like to dd an image of 64 bit ubuntu install onto the second hard drive. If someone has the time, would they install 64 bit ubuntu, and create a DD image of it.  I can download from you or you can upload to my ftp server.

Thanks for your time.
David

---

### Post by conundrumx on 2011-09-12
Why not boot from a USB drive and install from that?

---

### Post by devoda on 2011-09-12
I have had trouble booting from USB on this Macbook Pro 6,2. I believe some macs can and some cannot. I have used Refit and grub-efi but this method leaves me with out accelerated graphics drivers for my nvidia card. 

D.

---

### Post by computerkid2000 on 2011-09-12
I have known for a while that Macs can Boot off of USB Cd Drives, Would you like to try that?

If you don't have one, all I can say is buy another SuperDrive if USB Does not work

---

### Post by devoda on 2011-09-12
I can get an external usb cd drive. Or try the grub-efi usb boot method again. But if someone has a lot of time on their hand. I could still use the dd image. :D Please PM me!
D.

---

### Post by jonny on 2011-09-12
> **devoda said:**
> I have had trouble booting from USB on this Macbook Pro 6,2. I believe some macs can and some cannot. I have used Refit and grub-efi but this method leaves me with out accelerated graphics drivers for my nvidia card. 

D.You'll probably find that you can boot from a USB drive if you follow [these instructions]("http://ubuntuforums.org/showpost.php?p=11093491&postcount=43").

---

### Post by conundrumx on 2011-09-12
...why on earth would you try some of that horrible nonsense?  You should be able to hold down the Opt (Alt) key at boot and select the boot device from there.

---

### Post by jonny on 2011-09-12
> **conundrumx said:**
> ...why on earth would you try some of that horrible nonsense?  You should be able to hold down the Opt (Alt) key at boot and select the boot device from there.Because some Macs won't boot from a USB image unless it's been set up without any partitions.  I don't know of any GUI tool for creating a live USB in that way, so it's back to the command line.

The only horrible nonsense is Apple applying such ridiculous limitations to its machines.  I'm rather glad that some people - not me - are smart enough to overcome the restrictions that our corporate overlords attempt to enforce.

---

### Post by devoda on 2011-09-13
Well said Johnny. I wouldn't have to ask ridiculous favor if apple didn't implement their own version of EFI.

---

### Post by devoda on 2011-09-13
> **jonny said:**
> You'll probably find that you can boot from a USB drive if you follow [these instructions]("http://ubuntuforums.org/showpost.php?p=11093491&postcount=43").

Thanks!

---

