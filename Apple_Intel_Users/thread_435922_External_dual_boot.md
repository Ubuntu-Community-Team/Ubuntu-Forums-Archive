---
title: "External dual boot"
date: 2007-05-07
forum: Apple Intel Users
---

### Post by Didacsoy on 2007-05-07
Hi all there.

I'm a Macbook user, and though I'm very happy with OSX I'd like to give Ubuntu a try. I thought I'd use Boot Camp to dual boot, but unfortunately my internal disk is too small to handle my needs AND dual boot. However, I've got myself an external drive (both Firewire and USB) I can toy and experiment with, so I thought that if I could get to run Ubuntu from there I would be good to go.

Easier said than done, though! After some research I still don't understand why I won't run (Feisty would install just fine via firewire, not a single error or warning message during installation). I searched the forums but I couldn't find an answer to my problem. Has anyone tried (and I hope) managed to boot Ubuntu from an external drive?

Thanks for your time reading ;)

---

### Post by btrvalik on 2007-05-07
I'm having the same problem.. posted a thread but have not heard suggestions yet..

---

### Post by Chrisj303 on 2007-05-07
> **Didacsoy said:**
> Hi all there.

I'm a Macbook user, and though I'm very happy with OSX I'd like to give Ubuntu a try. I thought I'd use Boot Camp to dual boot, but unfortunately my internal disk is too small to handle my needs AND dual boot. However, I've got myself an external drive (both Firewire and USB) I can toy and experiment with, so I thought that if I could get to run Ubuntu from there I would be good to go.

Easier said than done, though! After some research I still don't understand why I won't run (Feisty would install just fine via firewire, not a single error or warning message during installation). I searched the forums but I couldn't find an answer to my problem. Has anyone tried (and I hope) managed to boot Ubuntu from an external drive?

Thanks for your time reading ;)

You could always just create a SMALL partition with bootcamp, unlike OSX/VISTA, a 5 gb partition would be fine for a trial period.

---

### Post by benanzo on 2007-05-07
is the problem that the EFI bootmenu doesn't see your USB or Firewire drive attached?  Did you hold Option while booting?

I would be curious about this as well since I am planning a USB stick install of Ubuntu soon.

---

### Post by Didacsoy on 2007-05-07
> **benanzo said:**
> is the problem that the EFI bootmenu doesn't see your USB or Firewire drive attached?  Did you hold Option while booting?

I would be curious about this as well since I am planning a USB stick install of Ubuntu soon.


That is precisely the problem. I tried 2 methods: the first one editing the files in the Live CD so the EFI would look for exactly the partition where the kernel was in (USB connection)... didn't work.

The second was to attach the same drive via Firewire and try a normal install from the Live CD. The process went smoothly: partition the new drive, formating partitions and installing, but later the EFI boot menu would only show my Mac OSX disk (and yes I got there by pressing the option key at boot time). The thing is that everyone says different things: I should use Boot Camp, or rEFIt or LILO or eLILO or several conjunctions of those, but I don't really know what would work (or if any would). Besides I don't know how to do what where and why, so I'm quite lost.

My hopes where put on someone having developed a 'foolprof' method (or kind of) that I could follow step by step and study later. I would be too much effort to acquire deep knowelege on how linux works and boots just to get a taste of how it works. I don't know if I've explained it properly, but I guess it would be quite like studying a full course on anatomy so you could try on a new shirt.

---

### Post by ronocdh on 2007-05-07
> **Chrisj303 said:**
> You could always just create a SMALL partition with bootcamp, unlike OSX/VISTA, a 5 gb partition would be fine for a trial period.
I just wanted to support this method. I know it's not what the OP requested, but for anyone else reading, it should be known that 5GB is plenty for Ubuntu!

I don't know very much about the issue at hand, but as I understand it, the Intel Macs don't boot from USB, which was a deliberate decision by Apple. Apparently it's easier to boot from a USB volume if it's formatted to HFS+, but that doesn't help us much here. Please post back every bit of progress you make, because it is a popular but relatively unresolved issue in this forum.

---

