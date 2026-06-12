---
title: "Grub editing problem"
date: 2011-11-27
forum: Any Other OS
---

### Post by Alistair George on 2011-11-27
Hi I have tried various grub editors, but none seem to make any sensible change to the grub boot.

EG startup-manager is defined with Mint as the default system & 640 x 480 but the result for both settings are completely different. First item in the list is always selected.
Also used grub-customizer and that doesnt change grub either.
Any ideas?

---

### Post by Alistair George on 2011-11-28
OK, the plot thickens. I went to GNU Grub and checked how to edit grub manually.
My grub file in /boot/grub/grub.cfg is showing completely different to whats happening on the grub boot screen.

This is the problem everything else is working to modify grub.cfg except grub boot is not being modified.

Any takers?

---

### Post by drs305 on 2011-11-28
The most likely reason is that the Grub menu you are editing is not the Grub menu being displayed at boot. 

This happens when you have multiple linux os's which use Grub 2. When you update grub, it updates the grub menu on the OS you are currently running. If you install a new linux os with it's grub, that grub normally is written to the MBR and will control the boot, *even if it is not the default os or is one you rarely use*.

If you haven't modified the order of the menuentries, you can tell which grub is controlling the boot by looking at the actual grub menu during boot. The controlling grub will list its own kernels first.  If you aren't sure, the partition isn't listed in the menu, or you have the same kernel on multiple os's, you can inspect it further by highlighting the first entry and pressing 'e' to see the details.

To change the controlling grub, boot into that OS and then run: 
```
sudo grub-install /dev/sdX
```
with X being the drive letter.

---

### Post by gman16000 on 2011-11-28
it would help to know which version of grub / ubuntu you are using and what you mean by completely different (wrong menu items vs incorrect graphics mode for example)

on my 11.10 version, it is ill advised to directly edit the /boot/grub/grub.cfg since this is a generated file.  on my system, i edit /etc/default/grub and then run update-grub

you can check this by maybe seeing if you have a /etc/default/grub and something in there matches what you are seeing in your menu.

---

### Post by drs305 on 2011-11-28
*gman16000's* post brings to mind another point. 

If you are manually editing the grub.cfg file and then running 'update-grub' afterward, it's going to erase any edits you have made to the grub.cfg file...

---

### Post by Alistair George on 2011-11-28
> **drs305 said:**
> *gman16000's* post brings to mind another point. 

If you are manually editing the grub.cfg file and then running 'update-grub' afterward, it's going to erase any edits you have made to the grub.cfg file...
No, wouldnt do that as it clearly advises against that in the header.
I did read something about drive define in grub2 differs from grub1 so Im a bit concerned doing what your first post says as I might get the drive definition wrong.
Here is what I have in boot grub screen:
1st item Pinguy with no drive showing apart from
set root='(/dev/sdb,msdos4)'

My preferred item is Mint (see the attached) and the first Mint item in menu drive definition says:
Mint on /dev/sdb2

Regards, Al.

---

### Post by grahammechanical on 2011-11-28
According to your first screenshot I would say that Pinguy OS was the last OS installed or the last OS to have its kernel updated. Would I be correct?

I would say that you have two options.

Make the changes to Grub menu in the Pinguy OS or wait until Mint updates its kernel. This will trigger a update-grub command which will put the Mint Grub in charge and then always update the mint kernel after the kernel updates of the other OSes. Once the Mint kernel is in charge then make any changes to Grub through Mint.

I have a few versions of Ubuntu and that is how I found out that the last Ubuntu to update the kernel was the Ubuntu that went to the top of the menu list.

I have Grub Customizer installed only on my working Ubuntu and when an update in the other Ubuntus changes the Grub menu I simply go into my working Ubuntu and use Grub Customizer to set things right.

I shall do this later on tonight as I am going to try out Mythbuntu and I know it will mess up my Grub menu with its background image. Grub Customizer in my working Ubuntu will fix it.

Regards.

---

### Post by Alistair George on 2011-11-28
Grub Customizer in Pinguy worked. I had not installed it and had tried startup-manager there, but that did not work.
Now I have the correct menus and menu resolution thanks vm.

I'd still like to try sudo grub-install /dev/sdX in Mint, but a bit wary if I get the wrong drive!
Cheers,
Al.

---

### Post by drs305 on 2011-11-28
I don't know what you have on sda, but both your Grub menus appear to be on sdb partitions.

Boot into Mint, then run:
```
sudo grub-install /dev/sdb
```

This will make Mint the controlling Grub as long as your BIOS boots the sdb drive first. You could also put it on sda if you wanted your system to boot to Mint regardless of which drive BIOS booted first, but without knowling what is on your sda drive I would probably not recommend it at this point. 

As was mentioned, if another OS updates a kernel or it's Grub package files (not with a simple 'update-grub' command), you will have to repeat the above command in Mint if your Grub menu reverts to the other OS.

---

