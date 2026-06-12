---
title: "I am dual-booting 6.06 (Dapper) and 7.04 (Feisty) and the boot menu is enormous!"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2007-05-26
Hi all,

I am up against a curious problem and am not sure what to do. This afternoon I decided to try it do a brand new install of Feisty on the laptop that I have been running Dapper on (a T23 ThinkPad). I installed from a live CD that I downloaded. Anyway, everything went fine. I chose to use the "guided" install method that only partitioned the empty 14+ GB of free space on the HDD. 

Here's the problem. Now my GRUB bootmenu looks like this: (sorry, it's an attached JPEG since I'm on my iBook right now and can't just provide a screen grab)

Why do I have eight load options for Dapper and what do I do about it?

TIA for any suggestions. I have other issues (like my RAM being maxed out) but I'll take one fix at a time.

Thanks again, 

KC

---

### Post by rusty4r on 2007-05-26
open a terminal and type
```
gksudo gedit /boot/grub/menu.lst
```

then uncomment each line that you dont need with # at the front of each line

---

### Post by rusty4r on 2007-05-26
Here is a section of mine


## ## End Default Options ##



title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Every time a new kernel is added I just add "#" to the old ones that way they are still there but don't show on the menu
hope that helps

---

### Post by Carbonfish on 2007-05-27
Thanks for the reply rusty4r,

I am about to comment out the identical (repeating) entries and I'll get back to you in a minute.

Thanks,

KC

---

### Post by rusty4r on 2007-05-27
usually the first one is the most recent but yours are identical?

---

### Post by rusty4r on 2007-05-27
No looking at your thumbnail I can see the difference They are different versions

---

### Post by Carbonfish on 2007-05-27
Okay rusty4r,

So far so good. After commenting out all of the repeats (I left the memtest at the bottom) I have booted to both iterations (first Feisty, then Dapper) and they both seem to boot fine. My bootmenu is alot cleaner too. Any ideas why there would be all of those unnecessary copies? Also, is there a "known issue regarding screensavers not working properly in Feisty? It looks like a RAM problem to me, or maybe hardware acceleration? Anyway, the screensavers are all jerky and use so many system resources that my pointer jerks around.

Any suggestions?

Thanks again,

KC

---

### Post by Carbonfish on 2007-05-27
Oh MAN! You're right! They are different. Why would I have so many different versions of Dapper on the bootloader? Should I let them live? Whazzup??

Thanks, 

KC

---

### Post by rusty4r on 2007-05-27
look at your thumbnail closely they are not repeats the kernel numbers change for example 2.6.15.28 and the one under it was 2.6.15.27

---

### Post by rusty4r on 2007-05-27
there just updated kernels there ok to leave there just uncomment them as you did

---

### Post by Carbonfish on 2007-05-27
Right. See the post above the one you just made. So what does this mean? Believe me when I tell you that I have RTFM and I didn't read anything about multiple versions of the same release piling up on my machine.

Any suggestions anyone?

---

