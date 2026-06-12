---
title: "[Closed]Booting Arch from Ubuntu grub causes delay in booting and swap problem"
date: 2014-06-07
forum: Any Other OS
---

### Post by ubume2 on 2014-06-07
I am booting Arch from Ubuntu using this line in my custom grub (06_custom). Arch is my toy distro. I don't rely on it
for day to day computer work. Just fun to play with, but can't rely on it because of its reputation for breaking.

menuentry "Arch (on /dev/sda8)" {
        set root=(hd0,8)
        linux /boot/vmlinuz-linux root=/dev/sda8 ro
        initrd /boot/initramfs-linux.img

This hasn't been a problem until recently. Now when Arch boots it stalls at the message 'a start job is running ...disk-by /x2duuid/[UUID of swap].device'. It counts down 1 min 30 seconds and boots into desktop, but swap is not mounted.
All the UUID's are correct in fstab. I ve even tried changing fstab to /dev/sda9 swap none defaults  0 0, but that doesnt help.
The only thing that does not cause the 1:30 countdown is if I add a /swapfile and make the changes in fstab.

I can use the grub-generated line for Arch with no problems at present in my 06_custom file, but wondering if there is a fix so I can use the much simpler boot entry above?

  Seems funny that this is only a very recent problem and it affects swap.  The custom lines above are from Arch's wiki on grub.

Thanks

Edit: May 10: I don't think it is a grub problem, Ubuntu or Arch.  I apparently messed something up with Arch causing it to be persnickity about grub. The above grub line should work for Ubuntu/Debian like installs. (You need to change last line to initrd /initrd.img  )

---

