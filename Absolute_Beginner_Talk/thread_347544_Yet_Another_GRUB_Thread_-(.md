---
title: "Yet Another GRUB Thread :-("
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Zero.The.Hero on 2007-01-27
Hello everybody.

I'm kind of new to this forum but not very new to Ubuntu... Still I have this problem with GRUB and I can't figure out how to get past it (I successfully re-installed GRUB several times before, but this time it just doesn't turn out to be OK). Please, bare with me :)

So here's the plot: I have a 200GB HDD with 3 primary partitions (hda1, hda2 and hda3) and and extended partition which contains 5 logical partitions. Here's the exact layout of my HDD:

[html]
/dev/hda1 ------- 15GB ---- FAT32 ---- Primary
/dev/hda2 ------- 15GB ----  N/A  ---- Primary
/dev/hda3 ------- 15GB ----  N/A  ---- Primary
/dev/hda4 ---------------------------- Extended
      /dev/hda5 -- 1GB ---- swap ----- Logical
      /dev/hda6 - 15GB ---- EXT3 ----- Logical
      /dev/hda7 -- 8GB ----- N/A ----- Logical
      /dev/hda8 - 80GB ---- EXT3 ----- Logical
      /dev/hda9 - 37GB ---- EXT3 ----- Logical
[/html]Alright. The /dev/hda2 , /dev/hda3 and /dev/hda7 are not currently used.
My current Edgy install is on /dev/hda6 (and I use /dev/hda8 and /dev/hda9 as storage partitions) and here goes the problem... I just installed Windows XP on the /dev/hda1 partition. All went fine except when I wanted to "update" my GRUB in order for it to hold both Edgy and XP. I used the "standard procedure", booted off the Live CD and typed in:

```

sudo grub
grub> find /boot/grub/stage1 [returned : (hd0,5) ]
grub> root (hd0,5)
grub> setup (hd0)
grub> quit

```and then rebooted. Alright, I could boot in Ubuntu but, well, GRUB did not "see" the XPain install. So I figured I had to edit the /boot/grub/menu.lst file by myself, which I did. So here is the relevand part from my /boot/grub/menu.lst file:

```

## ## End Default Options ##

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro 
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

[I]title        Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader+1[/I]

```Needless to say, all I did was to add the section in italics above. And then again, needless to say, I *can't* boot in XP. I even tried to change "root (hd0,0)" into "root (hd0,1)" but to no avail... :(

Needless to say, I feel completely idiotic and I can't seem to find a way to have a functional setup although I did install XP a few time ago on another box, but I guess the partitioning scheme was simpler than this one and GRUB automatically detected the XP install...

I hope somebody can help me out, I really don't have any other ideas on what I could do...

Regards,

Zero.The.Hero

---

### Post by Zero.The.Hero on 2007-01-27
Alright, never mind, I guess the rage against the fact I'm obliged to use XPain after all simply blinded me :lol:

The problem was THE SPACE ouch which I forgot to place here:

```
**chainloader +1**
```

Never mind, problem solved and I'm sorry I posted without looking twice. Sheesh. I won't delete my post though, maybe some other person will find that useful LOL.

Regards,

Zero.The.Hero

---

