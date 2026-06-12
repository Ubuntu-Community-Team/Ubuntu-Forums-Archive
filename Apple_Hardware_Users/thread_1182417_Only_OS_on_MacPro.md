---
title: "Only OS on MacPro"
date: 2009-06-08
forum: Apple Hardware Users
---

### Post by fatum on 2009-06-08
I have decided to get rid of OS X completely. Installed Ubuntu Jaunty on my Mac Pro and for now am booting from the rEFIT CD image that I burned. Is there a way to boot without a CD in the tray? I have been doing research but everything I find is depending on a Mac partition. I installed grub2 efi but it still does not boot without rEFIT. Any help is greatly appreciated. Thank you

---

### Post by pxwpxw on 2009-06-09
> **fatum said:**
> I have decided to get rid of OS X completely. Installed Ubuntu Jaunty on my Mac Pro and for now am booting from the rEFIT CD image that I burned. Is there a way to boot without a CD in the tray? I have been doing research but everything I find is depending on a Mac partition. I installed grub2 efi but it still does not boot without rEFIT. Any help is greatly appreciated. Thank you

Have you got the OSX install DVD?
You need to bless grub.efi then it wil boot without refit, and you can bless it using the OSX DVD.

Or grub.efi can be built with a hfspbless module, and can then bless itself.

---

### Post by fatum on 2009-06-09
Thank you for the reply. Doing some more research I found that with booting grub.efi that I would have to bypass 3D acceleration on my graphics card. The only way I have found to keep that is with rEFIT booting. So for now thats what I am going to have to do. I am looking into eLilo to handle the booting which to my research does not have the graphics issues.

---

### Post by pxwpxw on 2009-06-09
> **fatum said:**
> Thank you for the reply. Doing some more research I found that with booting grub.efi that I would have to bypass 3D acceleration on my graphics card. The only way I have found to keep that is with rEFIT booting. So for now thats what I am going to have to do. I am looking into eLilo to handle the booting which to my research does not have the graphics issues.

I don't understand, are you booting grub.efi with refit and getting 3d accel?
Edit-
Ah, if it boots from refit without using grub.efi, you must have installed grub-pc I think? That will give 3d accel.
and should be bootable without the refit CD using the option key. But I am not sure what you have there, there could be other possibilities.

---

### Post by cyberdork33 on 2009-06-11
> **pxwpxw said:**
> 
Ah, if it boots from refit without using grub.efi, you must have installed grub-pc I think? That will give 3d accel.
yep, and blessing that partition should get it to boot by default as well.

I am pretty sure that elilo has the same issues as grub-efi since it is booting via EFI that presents the issue...

---

### Post by fatum on 2009-06-15
I tried booting by holding option at the startup and for some reason it would hang with a folder icon with a ? blinking on screen. This happens with either holding down option or not. What I ended up doing is taking an extra HD I had putting OS X on that and now I have a small OS X disk with rEFIT on it and set it up to automatically boot into Ubuntu. After thinking about it longer I think it is a good idea to have OS X there just for firmware updates, plus I had to go back and start using my old airport extreme since my Linksys died the other day.

---

