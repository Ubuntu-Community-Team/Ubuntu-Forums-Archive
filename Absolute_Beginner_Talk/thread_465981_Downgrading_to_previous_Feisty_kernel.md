---
title: "Downgrading to previous Feisty kernel"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by DarkGob on 2007-06-06
Since my NIC is horribly unreliable when downloading anything significant under 2.6.20 [(per this bug)]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109629"), I would very much like to use the previous version until this bug is fixed.  (I switched to Ubuntu after the release of 2.6.20.)  Is this easily accomplished?

---

### Post by Inxsible on 2007-06-06
yes its achievable. but what kernel are you using ? 2.6.20-15 or 2.6.20-16 ?

I have read that many ppl have had problems with -16. The previous one ----   -15 --- is pretty stable
S
earch for "kernel 2.6.20-15" in the synaptic (without the quotes of course) and install these 3 packages
```
linux-headers-2.6.20-15
linux-headers-2.6.20-15-generic
linux-image-2.6.20-15-generic
```

That will install the kernel. if you want support in some other languages, you can install the relevant package(s) too.

---

### Post by Inxsible on 2007-06-06
thats assuming you have the 32 bit version installed !!!

---

### Post by DarkGob on 2007-06-06
It's 2.6.20-16, and it's the 64-bit version.  Looking in Synaptic, it looks as though both -15 and -16 are installed.  So I should be okay with removing -16?

---

### Post by Inxsible on 2007-06-06
I would think so. The Live CD comes with -15, so thats why you already have the -15. YOu must have installed updates which got the -16 down for you.
 
If you do not want to un-install -16, you can change the grub menu to make -15 your default. or simply comment out the -16 until they are fixed.
to get to the grub menu
```
gksudo gedit /boot/grub/menu.lst
```
 
post the output here so I can help you make the -15 as default. 
 
As a side note: when ever you update the kernel, it is always a good idea to keep atleast one older (read stable) kernel around until you are positively sure that the new one works flawlessly.

---

### Post by DarkGob on 2007-06-06
```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=99af5607-7fb2-4ce2-ac94-4db82f06a240 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=99af5607-7fb2-4ce2-ac94-4db82f06a240 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=99af5607-7fb2-4ce2-ac94-4db82f06a240 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=99af5607-7fb2-4ce2-ac94-4db82f06a240 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Inxsible on 2007-06-06
That's not your complete menu.lst But I will try:
 
You can change the default in two ways:
1) Comment out the top two -16 entries by putting a # in front of all the lines of 16
 
OR 
 
2) Look for a line ```
default 0
``` way up top of the file and change it to ```
default 3
```
 
Make sure you do EITHER  1 or 2 ..NOT BOTH.

---

### Post by DarkGob on 2007-06-06
Well, that didn't work.  Problem still persists under -15.

Are there any priests around who can perform an exorcism?

---

### Post by Inxsible on 2007-06-06
What kernel version did your NIC actually work in ?

---

### Post by DarkGob on 2007-06-06
None.  I just switched to Ubuntu last week and downloaded all the upgrades I could, so except for the short time I was using the -15 that the Live CD installed, I've always been under -16.

---

### Post by Inxsible on 2007-06-06
> **DarkGob said:**
> None. I just switched to Ubuntu last week and downloaded all the upgrades I could, so except for the short time I was using the -15 that the Live CD installed, I've always been under -16.
 
Ha ha. Your original post seemed to indicate that it was the kernel which messed it up. Since you have never got NIC working, 
 
1) Do you mean the wireless or wired or both?
2) What NIC do you have?
3) Have you tried ndiswrapper?
4) Does it give you any error? If so, what error?

---

### Post by DarkGob on 2007-06-06
1) Wired.
2) 3Com 3c905C-TX/TX-M
3) No, I'll give that a shot.  Actually, it seems I was told to do that over in Networking, but I never tried it because it seemed to be a wireless driver (I never got an answer back on that when I asked; I must have forgotten).
4) The system log tells me this:
```
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658407] NETDEV WATCHDOG: eth0: transmit timed out
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658415] eth0: transmit timed out, tx_status 00 status 8681.
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658421]   diagnostics: net 0cd8 media 88c0 dma 0000003a fifo 8000
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658424] eth0: Interrupt posted but not delivered -- IRQ blocked by another device?
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658514]   Flags; bus-master 1, dirty 82744(8) current 82744(8)
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658517]   Transmit list 00000000 vs. ffff81003d545700.
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658522]   0: @ffff81003d545200  length 800005ea status 0c0105ea
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658525]   1: @ffff81003d5452a0  length 8000003c status 0c01003c
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658528]   2: @ffff81003d545340  length 8000002a status 0001002a
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658531]   3: @ffff81003d5453e0  length 8000002a status 0001002a
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658534]   4: @ffff81003d545480  length 8000002a status 0001002a
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658537]   5: @ffff81003d545520  length 8000002a status 0001002a
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658540]   6: @ffff81003d5455c0  length 8000002a status 8001002a
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658543]   7: @ffff81003d545660  length 8000002a status 8001002a
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658546]   8: @ffff81003d545700  length 80000042 status 00010042
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658549]   9: @ffff81003d5457a0  length 800005ea status 0c0105ea
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658552]   10: @ffff81003d545840  length 800005ea status 0c0105ea
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658555]   11: @ffff81003d5458e0  length 800005ea status 0c0105ea
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658559]   12: @ffff81003d545980  length 800005ea status 0c0105ea
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658562]   13: @ffff81003d545a20  length 8000003c status 0c01003c
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658565]   14: @ffff81003d545ac0  length 8000003c status 0c01003c
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658568]   15: @ffff81003d545b60  length 800005ea status 0c0105ea
Jun  6 11:27:13 chris-desktop kernel: [ 2511.658571] eth0: Resetting the Tx ring pointer.
```

---

### Post by DarkGob on 2007-06-06
Well, that seems to have done it.  [And that's why you always try.]("http://img105.imageshack.us/img105/1313/jww2uv.jpg")

Thanks times 10^9, Inxsible! \\:D/ (Closest thing I could find to thumbs-up.)

---

### Post by DarkGob on 2007-06-06
*sigh* Seems I jumped the gun.  Had it happen again.  It usually (but not always) happens when I'm trying to download a large file, after about an hour (which was the case this last time).  However, it has also been known to happen when I'm just engaged in more regular internet activity (IMing and web browsing, no file downloads involved), after 3-4 hours.

I'm beginning to think "ooo eee, ooo ah ah, ting tang walla walla bing bang" is my only recourse at this point.

---

### Post by DarkGob on 2007-06-06
So, it seems we're back to my original question.  (Well, in terms of this thread.)  The person who filed the bug description (see first post in this thread) has no trouble under 2.6.17.  Exactly how much of a royal pain would it be to downgrade to this, given that I switched to Ubuntu with 2.6.20?

---

### Post by powder on 2007-06-06
Hi DarkGob,

If you add the edgy main repos to your sources.list, you should be able to install the 2.6.17 kernel via Synaptic.  But don't ask me if it will work or not. ;)

---

### Post by DarkGob on 2007-06-06
What *exactly* do I need to add to my sources.list file?  I found [this]("http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html") but that complete list seems a bit too complete for my purposes.

---

### Post by DarkGob on 2007-06-07
Okay, I've got sources.list updated so I can install Edgy.  I just want to be *absolutely clear*, I'm okay with installing linux-image-2.6.17-10-generic through Synaptic until the 3Com NIC bug in 2.6.20 is fixed?  It's not going to screw anything up?

---

### Post by DarkGob on 2007-06-08
Anyone?  Bueller?

---

