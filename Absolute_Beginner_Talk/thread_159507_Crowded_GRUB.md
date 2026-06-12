---
title: "Crowded GRUB"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by mrchrisblau on 2006-04-13
So I'm dual booting between xp (its for the games! I swear!) and Ubuntu 5.10. It all works fine, thats not the issue. The problem is that when GRUB opens up there is a list of 9 different Ubuntu possibilites. I always pick the one marked Default because a) it has worked in the past and b) Default sounds about my speed :D . 

My questions are these: 
Can I just delete all the other entries in the /boot/grub/menu.lst file besdies the xp entry and the Default ubuntu entry? 
Alternativly, could I just comment out all the other ubuntu entries that I don't need (everything but Default)? 
And, Is Default even the right one to be booting (with 9 choices you can never be to sure)?

I would normally just mess around with the file and pray for the best, but messing with GRUB when I don't know exactly what I'm doing is not the best of ideas methinks (as it could stop me from booting ubuntu or windows or both.. and that would not make me happy). 

Thanks in advance!

---

### Post by mrchrisblau on 2006-04-13
Oh, almost forgot...

This is what my /boot/grub/menu.lst looks like (or at least the part of it concerning the list of possible boot options):

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous 
root		(hd0,2)
kernel		/boot/vmlinuz.old root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz.old root=/dev/sda3 ro single
initrd		/boot/initrd.img.old
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by KansasJoe on 2006-04-13
go to synaptic and you'll want to search for linux-kernel and remove the ones you are not using...this will get rid of them and clean up that grub menu

---

### Post by mrchrisblau on 2006-04-13
[QUOTE=KansasJoe]go to synaptic and you'll want to search for linux-kernel and remove the ones you are not using...this will get rid of them and clean up that grub menu[/QUOTE]

Should I remove all the ones but Default (as that is the one I have been using)? Or is there another one I should use?

---

### Post by KansasJoe on 2006-04-13
remove the 2.6.12-9

---

### Post by mrchrisblau on 2006-04-13
[QUOTE=KansasJoe]remove the 2.6.12-9[/QUOTE]

Hmm, all I see is linux-kernel-headers when I search for linux-kernel in Synaptic...

---

### Post by KansasJoe on 2006-04-13
i'm on windows cause i just got off americas army but if it has 2.6.12-9 after it then that's the one you want

---

### Post by mrchrisblau on 2006-04-13
[QUOTE=KansasJoe]i'm on windows cause i just got off americas army but if it has 2.6.12-9 after it then that's the one you want[/QUOTE]

Yep. Searched for kernel and found a whole bunch of stuff but removed the 2.6.12-9.

---

### Post by mrchrisblau on 2006-04-13
Ok, after doing what Joe reccomended I went ahead and commented out the two non-"Default" options in GRUB. I left the memtest86+ as I didn't know what that did.

While we're talking about it, what does the boot option memtest86+ do?

---

### Post by xenmax on 2006-04-13
It is diagnostic program for memory. It is a stand alone memory test for x86 architecture computers - apart from the memtest which your BIOS has. It does some random pattern writes to memory and i guess reads them back.

---

