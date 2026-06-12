---
title: "Triple Boot =&gt; Mac OS X (HFS), Boot Camp (WinXP SP2) (NTFS), How could I add Ubuntu?"
date: 2007-03-30
forum: Apple Intel Users
---

### Post by orlandopozo on 2007-03-30
Hello folks,

I installed Mac OS X (HFS Partition), and Windows XP SP2 (NTFS Partition) natively by using boot camp.

I really want to add Ubuntu (Edgy or Feisty) natively to the group to create a triple boot, the problem is that all the articles that I have been reading regarding triple boot use diskutil to resize the Mac OS partition and make 2 partitions for Windows and Linux, that is, they don't use bootcamp to make the partition for Windows.

I was thinking to use iPartition  (partition resizing tool similar than partitionMagic for windows) or the same diskutil to resize again the Mac OS X (HFS Partition) in order to create a free space to mount the linux (ext3) partition there. After that, I will install refit in Mac OS X to get the triple boot menu, then I will boot with the Ubuntu CD, and after grub fails, I will install LILO and refit.deb.

Any thoughts?

---

### Post by jsc1959 on 2007-03-31
Sounds like a good idea. Its about the same thing I did except I used Vista. diskutil works just fine by the way. Its really nice you can use it while your in the os!

Jeff

---

### Post by jsc1959 on 2007-03-31
One other thougt. I put grub only on my ubuntu partition. Use the advanced menu right during the install to specify your partition. I used (hd0,3). Since you can only have 4 primary partions. Refit works pretty well.

---

### Post by ronocdh on 2007-03-31
Perhaps I should start yet another thread about this, but I still haven't gotten Ubuntu going on my Macbook Pro. I have OS X (of course) and XP running very smoothly, but I still cannot boot into Ubuntu using rEFIt. I've waited for GRUB to fail on the installation, installed LILO, configured it, synched my MBR a thousand times... I just cannot get it!

When I boot from a Live CD and mount my directories and chroot everything, I have a fully working system, and my LILO config files look pristine to me. Does anyone have any tips for how to get Ubuntu to show up on the rEFIt screen?

=(

---

### Post by Chrisj303 on 2007-04-01
I hate to state the obvious, but have you "activated" LILO when chrooted into your ubuntu install?
I.e  sudo lilo

I was a TOTAL linux virgin when i setup my triple boot - it took me days to realise this!

---

### Post by ronocdh on 2007-04-01
Chris,

I had followed every guide to the T. Of course, different guides had the LILO activation process slightly different, as certain tags were necessary on Edgy that weren't on Dapper, for instance. In the end, I just used [a href=https://help.ubuntu.com/community/MacBook]this guide[/a] and it worked like a charm! Now my only issue is:

When I select either Ubuntu or WinXP from the EFI boot loader, I'm sent to GRUB... but 9 times out of 10, my arrow keys don't work, so I can't select anything! Now, usually that's OK because I just want to use Ubuntu anyway ;) but it's not exactly optimal. Any advice?

---

### Post by ronocdh on 2007-04-01
And while we're at it, someone please teach me either A) to use links properly on this forum or B) to preview my dern posts. =D

---

### Post by Chrisj303 on 2007-04-01
^ I was in the exact same situation with grub. I searched high and low for a soloution but to no avail. I had to use LILO instead.
Now when i select windows from the rEFIt menu, it boot straight into XP - no bios-like bootload menu to navigate whatsoever.

The cursor problem SEEMS to still be an issue with LILO - check out the thread i started earlier today. But if windows boots straight away when selected (refit) like it does in my case, then it is not really a problem.

Via my LILO.conf file, i have only pointed lilo towards my ubuntu install. I assume that windows is booting using it's own bootloader.

Have you checked out the 'onmac' triple boot guide? - that one worked great for me.

chrisj303

---

### Post by ronocdh on 2007-04-01
Chris,

The OnMac one is where I started. I loved the detail of it, but unfortunately after I synched my GPT and MBR, I still didn't have Linux as a HD install in EFI. A damn shame, I'd much prefer LILO over GRUB, but for some reason all the various edits and strings I tried to configure LILO, although they matched the (various ;)) guides perfectly, wouldn't cut it.

The MacBook GRUB-only guide was a snap! Now I just have to work on ndiswrappers and resolution... :guitar:

---

### Post by praywaror2 on 2007-04-01
Why not use "Parallels" software ? Now I have set-up several triple boot PC's, but on my main machine a Apple MacBook Pro I have been using paralles to use 5 different OS's and they seem to run very fast, not slower as I would have suspected compared to have three partitions, which I set using Apples disk utility as 1.) HTFS 2.) NTFS 3.) empty (non-formatted) for Ubuntu , then I use install OSX86 first, Then, Win XP, and Last Ubuntu . Now You lose OSX so I run apples disk utility from the DVD and repair the permissions and verify everthing, Now sometimes you have to add a line to grub, but not always, this may depend on the distro, have figured this out yet. But as I said I have found Parallels to be better for my personel needs for now. One problem though parallels uses only the versa video drivers so your video card potential gets dumbed down a bit, now if I was a gamer this would be a big issue indeed.

John

---

### Post by Chrisj303 on 2007-04-01
> **praywaror2 said:**
> Why not use "Parallels" software ? Now I have set-up several triple boot PC's, but on my main machine a Apple MacBook Pro I have been using paralles to use 5 different OS's and they seem to run very fast, not slower as I would have suspected compared to have three partitions, which I set using Apples disk utility as 1.) HTFS 2.) NTFS 3.) empty (non-formatted) for Ubuntu , then I use install OSX86 first, Then, Win XP, and Last Ubuntu . Now You lose OSX so I run apples disk utility from the DVD and repair the permissions and verify everthing, Now sometimes you have to add a line to grub, but not always, this may depend on the distro, have figured this out yet. But as I said I have found Parallels to be better for my personel needs for now. One problem though parallels uses only the versa video drivers so your video card potential gets dumbed down a bit, now if I was a gamer this would be a big issue indeed.

John

I used parallels from build 1970 all the way up to 3186 - i got sick of waiting for parallels to release the Tools for linux. I also much prefer the increased performance native booting brings. The thing is, is that i have no need to run 2 OS side-by-side - i'd rather have 3D acceleration thanks!
I still use VMware fusion beta to test linux distro's.

cheers,
chrisj303

---

### Post by orlandopozo on 2007-04-03
Mainly, the problem I have, is that I didn't begin with diskutil command, I installed Mac OS X, and then I installed WinXP by using bootcamp, I want to add Ubuntu to the group.

Have anyone installed Ubuntu by following the procedure stated above?

I know if I reformatted everything, and then I installed Mac OS X and make the partition by using diskutil instead of bootcamp, it will work fine, that is the approach used by onmac.net and others.

Any thoughts?

---

### Post by Chrisj303 on 2007-04-03
> **ronocdh said:**
> Chris,

The OnMac one is where I started. I loved the detail of it, but unfortunately after I synched my GPT and MBR, I still didn't have Linux as a HD install in EFI. A damn shame, I'd much prefer LILO over GRUB, but for some reason all the various edits and strings I tried to configure LILO, although they matched the (various ;)) guides perfectly, wouldn't cut it.

The MacBook GRUB-only guide was a snap! Now I just have to work on ndiswrappers and resolution... :guitar:

Wait, your triplebooting with GRUB? and you don't have any issue with the keyboard not responding to the GRUB menu about 80% of the time? If so, then your the first i've heard of.
the configuration of LILO is really no different to GRUB there are some great guides out there.

---

