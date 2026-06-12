---
title: "Ubuntu without macosx in mac mini"
date: 2008-01-30
forum: Apple Intel Users
---

### Post by peio on 2008-01-30
Hello,
Yesterday I installed Ubuntu 7.10 in my new c2d mac mini and everything works great. maybe except suspend to ram than only works sometimes.
Now I would like to use the whole hdd for linux and remove mac os x. Is it posible? somebody has get it? Any howto?
Thanks in advance
p.

---

### Post by hajk on 2008-01-30
Well, I've done it on a CD MacBook, just a matter of installing GNU/Linux to the internal HD using an old-fashioned MBR partition table and installing GRUB to it (yes, EFI will load such a legacy OS). However, consider that you need Mac OS X to install firmware updates (or even when installing Psst to silence that awful Apple boot chime); I copied my Mac OS X install to an external FireWire drive with CarbonCopyCloner exactly for that purpose (yes, Mac OS X will boot from an external drive when plugged in). In the meantime I got tired of that arrangement, installed a larger HD in the MacBook, and reinstalled Mac OS X plus Ubuntu Gutsy in a dual-boot arrangement using rEFIt, see the links provided in the Sticky.

---

### Post by entangled on 2008-01-31
I think I prefer hajk solution, use rEFIt to boot either MacOSX or Linux from the same internal hard disk. I found the standard 60G was enough.

peio - have you got your mac Mini to suspend to Ram? I use a first generation Intel Mac Mini Solo and I found that suspend to ram didn't work at all on Ubuntu 7.04.
On 7.10 I can get suspend but there seems no way to wake it up again. Keyboard or mouse have no effect. Pressing on the power button brings the power light up but the video is dead. Only thing is to reboot.

I can get suspend to disk to work but this is not much quicker than shutdown and reboot.

---

### Post by cyberdork33 on 2008-01-31
have you tried making this change:
edit /etc/default/acpi-support in the following way:
change POST_VIDEO=true into POST_VIDEO=false 
reboot

---

### Post by peio on 2008-01-31
After your advices by now I am going to keep mac os x partition. I will wait to learn more abour efi to get  an standalone ubuntu system :)
p.
entangled: About suspend to ram. One of my friends point to me to this wiki entry where they say to use 2.6.22-12 kernel. :
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
I haven't  try it yet...



> **entangled said:**
> I think I prefer hajk solution, use rEFIt to boot either MacOSX or Linux from the same internal hard disk. I found the standard 60G was enough.

peio - have you got your mac Mini to suspend to Ram? I use a first generation Intel Mac Mini Solo and I found that suspend to ram didn't work at all on Ubuntu 7.04.
On 7.10 I can get suspend but there seems no way to wake it up again. Keyboard or mouse have no effect. Pressing on the power button brings the power light up but the video is dead. Only thing is to reboot.

I can get suspend to disk to work but this is not much quicker than shutdown and reboot.

---

### Post by entangled on 2008-01-31
Thanks for the advice cyberdork33 and peio.
Unfortunately POST_VIDEO=false didn't do anything.
I also tried uncommenting
SAVE_VIDEO_PCI_STATE=true
and commenting
USE_DPMS=true
but no luck. Just the same, still no video.

I looked at the macbook link. 
Sounded relevant but I think the 2.6.22 kernel was in 7.04, which didn't even start suspending on this box. I wonder if the 2.6.24 kernel is any better?

Frustrating, when you see how well MacOSX does it on the same box. Suspends in about 5s and resumes in 3s.

---

### Post by ronocdh on 2008-01-31
> **entangled said:**
> Frustrating, when you see how well MacOSX does it on the same box. Suspends in about 5s and resumes in 3s.
Effortless suspend is the feature I miss most, as I don't often have it in Ubuntu. I never got it at all with Edgy or Feisty, but with Dapper I swear I did. Weird things, suspend features.

Regarding the OP, it's been said a thousand times before, but I recommend you have at least a minimal install of OS X present for firmware updates. You can adjust rEFIt to boot right into Ubuntu by default instead of OS X if that suits you better. That way OS X can be your "other" OS.

---

### Post by ssnape on 2008-02-01
Well, I run Ubuntu (gutsy) on a new Core 2 Duo Mac mini with no OS X on the disk at all.  I just told the nice ubuntu amd64 install to use the entire disk.  Easy and painless except for a few things in ubuntu or rather 64 bit linux land that don't quite work seamlessly like flash.   The mini boots straight into linux just fine.   Since I use it as an always on ultra quiet linux desktop I never worried about whether it could sleep or not.

---

### Post by ssnape on 2008-02-01
> **ronocdh said:**
> Effortless suspend is the feature I miss most, as I don't often have it in Ubuntu. I never got it at all with Edgy or Feisty, but with Dapper I swear I did. Weird things, suspend features.

Regarding the OP, it's been said a thousand times before, but I recommend you have at least a minimal install of OS X present for firmware updates. You can adjust rEFIt to boot right into Ubuntu by default instead of OS X if that suits you better. That way OS X can be your "other" OS.

Well, if I really want a firmware update then I can just plug in a firewire leopard external disk and boot into that, right?

---

### Post by peio on 2008-02-01
>I looked at the macbook link. 
>Sounded relevant but I think the 2.6.22 kernel was in 7.04, which didn't even start >suspending on this box. I wonder if the 2.6.24 kernel is any better?

In a gutsy box:
[peio]@[gorbea]:~$ uname -r                                                                                            
2.6.22-14-generic

p.

---

### Post by peio on 2008-02-01
> **ssnape said:**
> Well, I run Ubuntu (gutsy) on a new Core 2 Duo Mac mini with no OS X on the disk at all.  I just told the nice ubuntu amd64 install to use the entire disk.  Easy and painless except for a few things in ubuntu or rather 64 bit linux land that don't quite work seamlessly like flash.   The mini boots straight into linux just fine.   Since I use it as an always on ultra quiet linux desktop I never worried about whether it could sleep or not.

Snape: I have readed in other sites that you lost 3d hardware acceleration without boot camp method(without mac os x). Is this true?
p.

---

### Post by cyberdork33 on 2008-02-01
> **peio said:**
> Snape: I have readed in other sites that you lost 3d hardware acceleration without boot camp method(without mac os x). Is this true?
p.
I think you are misinterpretting. You lose 3D acceleration if you try to boot directly from EFI... although, there are some patches to do this available only for Mac Mini. Not something that I would venture after right now though. 3D acceleration should work fine for you.

2.6.24 has a lot of improvements all around. It might be worth the try.

Also, yes, keeping an install of OSX on a bootable external drive is a good solution.

---

### Post by entangled on 2008-02-03
Just a quick note - not really on topic but we have mentioned the subject - and it is a first AFAIK.
Ubuntu DOES suspend and resume on Intel Mac Mini with the 2.6.24-5 kernel currently in Hardy Heron.
I installed that kernel and got proper resume by touching the power button - not from mouse or key click.
I intend to stick with the new kernel.

---

### Post by peio on 2008-02-03
I have been playing with the mac mini last night .Now I have a working ubuntu stand alone instalation. But I haven't  remove /dev/sda1 recogniced like EFI partition.

Somebody knows if I can remove this partition? And why could I need to upgrade efi firmware?
p.

---

### Post by cyberdork33 on 2008-02-04
> **peio said:**
> I have been playing with the mac mini last night .Now I have a working ubuntu stand alone instalation. But I haven't  remove /dev/sda1 recogniced like EFI partition.

Somebody knows if I can remove this partition? And why could I need to upgrade efi firmware?
p.That is the EFI parition. It is part of the EFI specification to have it on the disk. You can remove it if you want, but it is really better to keep it.

You might need to upgrade the firmware, if, for instance, there was a bug in the software that causes the thing to burst into flames... Not that this is the case... just an example.

---

