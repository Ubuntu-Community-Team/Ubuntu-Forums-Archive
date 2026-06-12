---
title: "Bootloader (LILO) not loading my OS!"
date: 2012-06-24
forum: Any Other OS
---

### Post by Declanthedork on 2012-06-24
So for the past three days I've been in a constant state of facepalm. I installed Linux Mint 13 and GRUB wouldn't even open. The farthest I got was "GRUB Loading." when I held down shift. 

So I decided instead of messing with it I'd just get LiLo. I got that all set up, but when I select my OS it just says "booting......" and every once in a while another dot comes up. I left it for up to an hour but it still just said "booting" with a lot of dots. 

Here is my lilo.conf file:
```

boot=/dev/sda
default=FBGM
map=/boot/map
compact
install=/boot/boot.b
prompt
timeout=10
image=boot/vmlinuz-3.2.0-23-generic
    label=FBGM
    initrd=/boot/initrd.img-3.2.0-23-generic
    root=/dev/sda1
    read-only
image=/boot/memtest86+.bin
    label=memtest
    read-only

```

If there's any other log files or confs I could post that would help, please tell me! I really appreciate any answers, even if you don't think they'd be that helpful! Thank you

---

### Post by efflandt on 2012-06-25
Is that a typo when you posted or are you missing a slash in actual lilo.conf:
[FONT=monospace]
[/FONT]image=boot/vmlinuz-3.2.0-23-generic

Should be:
[FONT=monospace]
[/FONT]image=/boot/vmlinuz-3.2.0-23-generic

That is the only thing I spot right off the bat, but I have not used LILO since Mandrake 7.0 and RedHat 6.2

---

