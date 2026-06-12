---
title: "Ubuntu on Macbook 2,1 boot problems"
date: 2013-04-01
forum: Apple Hardware Users
---

### Post by akston on 2013-04-01
Hey guys,

I'm trying to boot Ubuntu's live CD on my Mid 2007 MacBook 2,1.

I'm using rEFInd.

I've tried the 32bit i386 ubuntu 12.10 iso. rEFInd sees it, but it won't boot.
I've tried the AMD64 version of ubuntu 12.10. rEFInd sees a grubx64.efi and a bootx64.efi option. Neither boots, because

```
"Error : Unsupported while loading grubx64.efi".
```

According to 

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

```
"[COLOR=#333333][FONT=Ubuntu]Pre-2008 Macs usually have i386-efi firmware while >=2008 Macs have mostly x86_64-efi. 
All Macs capable of running Mac OS X Snow Leopard 64-bit Kernel have x86_64 EFI 1.x firmware.[/FONT][/COLOR]
```

and

[COLOR=#333333][FONT=Ubuntu]```
On Mac, if after you've installed and configured, when you reboot, rEFIt/rEFInd reports 
"Error: Unsupported while loading grub.efi", it is likely you compiled the wrong version (64 vs 32 bit). Try the other EFI architecture.
```[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]


Now, I'm not entirely sure what to do with this.. Where can I find an image which has the i386 EFI stuff?

Can anyone please point me in the right direction?

Thank you so much,
Akston

---

### Post by akston on 2013-04-02
So yeah, I guess my question is basically which ISO or image has this [COLOR=#333333][FONT=Ubuntu]EFI/BOOT/BOOTIA32.EFI[/FONT][/COLOR] thing on that I seem to need?

Thanks guys..

---

### Post by akston on 2013-04-03
Hey guys,

Ok, well, I've tried getting the AMD64+mac image to boot, and well, It doesn't boot either.

I'm at a bit of a loss guys.

How can I get ubuntu running on my MacBook 2,1?

I should probably mention that I'm booting the images from a USB thumb drive because the MacBook's CD Rom is buggered.

None of the images work boot, not natively, not using rEFInd. 
All of them work on my MacMini.

I don't know what to try next?

---

### Post by Fet600 on 2013-04-05
Hi,

I have a MacBook 2,1 and found I had exactly the same problem as you did.  I've never managed to get it to boot from a USB thumb drive (my internal CD drive also died, so I feel your pain) but I found that it was happy to boot from a live CD using an external USB CD drive.  I bought a cheap one from Amazon for about £20 and this made my life much easier.

I found this method works for both rEFIt and booting natively.

Hope this helps :P

---

### Post by quanpt on 2013-04-10
I have just install Precise on MacbookAir 2,1 without USB Drive (broken) or CDROM :)
[https://help.ubuntu.com/community/MacBookAir2-1/Precise](https://help.ubuntu.com/community/MacBookAir2-1/Precise)

---

