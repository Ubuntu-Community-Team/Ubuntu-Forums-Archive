---
title: "Error: No Suitable Mode Found during USB Installation"
date: 2014-01-22
forum: Any Other OS
---

### Post by bikeracer4487 on 2014-01-22
So I'm trying to install SteamOS. I'm posting here because all the official Steam forums I've posted in have been a bust, and the only useful links have all pointed to this forum. When I try to install I get the error "No suitable mode found" with "Booting however" on the next line. I saw this same error when I had previously installed Ubuntu 12.04 LTS on the same laptop...except in that case it still booted into Ubuntu just fine. When I get the error with SteamOS, it just sits there indefinitely and doesn't continue. I've found plenty of fixes for the UBUNTU issue, but the problem is that the files that need to be edited don't exist on the SteamOS USB. There is a grub.cfg file in the \boot\grub folder of the USB, but the text doesn't match the text in the grub files in Ubuntu. I've posted the complete text below, in case it is of use. (I can put it in PasteBin if people think it's too much for a single forum post, but it's rather small).

```
if loadfont /boot/grub/font.pf2 ; then
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
  insmod gfxterm
  insmod png
  terminal_output gfxterm
fi

set theme=/boot/grub/theme/1
menuentry 'Automated install (WILL ERASE DISK!)' {
    set background_color=black
    linux    /install.amd/vmlinuz preseed/file=/cdrom/default.preseed DEBCONF_DEBUG=developer desktop=steamos auto=true priority=critical video=vesa:ywrap,mtrr vga=788 -- quiet 
    initrd   /install.amd/gtk/initrd.gz
}
menuentry 'Expert install' {
    set background_color=black
    linux    /install.amd/vmlinuz preseed/file=/cdrom/default.preseed DEBCONF_DEBUG=developer desktop=steamos priority=low video=vesa:ywrap,mtrr vga=788 -- 
    initrd   /install.amd/gtk/initrd.gz
}
menuentry 'Rescue mode' {
    set background_color=black
    linux    /install.amd/vmlinuz preseed/file=/cdrom/default.preseed DEBCONF_DEBUG=developer video=vesa:ywrap,mtrr vga=788 rescue/enable=true -- quiet  
    initrd   /install.amd/gtk/initrd.gz
}


```

---

### Post by grahammechanical on 2014-01-22
You should have posted this in the Other OS/Distro Support section as that is what Steam OS is, Other OS. It is now built upon Debian and not Ubuntu. 

Do you have an OS already installed on that machine? Is it windows 7 or 8? This problem might be connected to problems with UEFI - GPT and stuff like that. Does Steam OS have a Linux kernel that has been signed with an encryption key that is compatible with Microsoft's Secure Boot requirements? You could try running a Ubuntu live session. Make sure it is 64 bit and see what happens then.

This is part of a Ubuntu Install disk grub.cfg

> if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}

I notice that Steam OS does not use Casper as Ubuntu does but that should be not the problem.

Regards.

---

### Post by Iowan on 2014-01-22
> **grahammechanical said:**
> You should have posted this in the Other OS/Distro Support section ...
Done!

---

