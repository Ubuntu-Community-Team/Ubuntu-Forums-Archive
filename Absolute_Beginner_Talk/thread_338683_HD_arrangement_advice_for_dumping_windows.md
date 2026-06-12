---
title: "HD arrangement advice for dumping windows?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-14
Currently ,my windoze "C"(80GB) drive (hda1) has XP Pro, the second internal, windoze "D"(120 GB) has ubuntu. The first external (30GB is NTFS and empty), will be used for downloaded music storage. It used to be full, but that's another story. The second external is 40 GB (NTFS) with video (too big to copy) so will remain unchanged for now. My inclination is to install ubuntu on  hda1 and save hda2 and the 2 externals for storage. If I installed on hda1, would the system freak out with 2 ubuntu installations? The other alternative is to physically swap the 2 internals and save my ubuntu installation. I think 120 GB is much more than necessary for ubuntu.  If you were in this position, what would you do?

---

### Post by logos34 on 2007-01-14
> would the system freak out with 2 ubuntu installations?
what, you want to run 32- and 64-bit versions of Ubuntu? if that's the case should work fine...you'll just have two kernels and windows to choose from on your grub menu.

I'd maybe swap the internal drives and shrink hda1 and put some ext3 partitions on it.  Don't dump winxp pro completely (you paid for it!)

---

### Post by marx2k on 2007-01-14
> **kliljedahl said:**
> Currently ,my windoze "C"(80GB) drive (hda1) has XP Pro, the second internal, windoze "D"(120 GB) has ubuntu. The first external (30GB is NTFS and empty), will be used for downloaded music storage. It used to be full, but that's another story. The second external is 40 GB (NTFS) with video (too big to copy) so will remain unchanged for now. My inclination is to install ubuntu on  hda1 and save hda2 and the 2 externals for storage. If I installed on hda1, would the system freak out with 2 ubuntu installations? The other alternative is to physically swap the 2 internals and save my ubuntu installation. I think 120 GB is much more than necessary for ubuntu.  If you were in this position, what would you do?

From your topic I was under the impression you want to completely drop Windows.

If so, you already have Ubuntu installed. Just transfer the files you need (music, movies, documents, bookmarks, etc) and convert your NTFS to EXT3 and you're done.  If you want to install Ubuntu to hda1 and remove it from second internal, you can do as well. GRUB will throw it into the boot menu and you can choose it at that time.  Move all of your vital info and config files from the second internal and wipe.  Since you're dumping windows, move the 40GB of video over to the 120GB when you're done moving Ubuntu and convert to ext3.  Convert the 30GB external to ext3 as well.  I'm not sure what you mean by 120GB is much more than necessary for Ubuntu? Do you mean that you should devote more space to Windows? I was under the impression that you're dumping it? If thats the case, no reason to stick with inferior NTFS.  Convert everything to ext3.

---

### Post by kliljedahl on 2007-01-15
> **logos34 said:**
> what, you want to run 32- and 64-bit versions of Ubuntu? if that's the case should work fine...you'll just have two kernels and windows to choose from on your grub menu.

I'd maybe swap the internal drives and shrink hda1 and put some ext3 partitions on it.  Don't dump winxp pro completely (you paid for it!)

What i was referring to was the new installation installation of ubuntu on hda1(the 80GB) and the current one on hda2. I would then wipe hda2 for storage, What I was wondering about would be the initial bootup before hda2 was wiped. I haven't been on windoze in 3 weeks and haven't missed it, so I see little reason to keep it.

---

### Post by kliljedahl on 2007-01-15
I was  planning on reinstalling on hda1 and doing just that. Is there a utility to 
"move all of your vital info and config files from the second internal". or does it have to be done manually?

---

### Post by logos34 on 2007-01-15
> What I was wondering about would be the initial bootup before hda2 was wiped
> 
new installation installation of ubuntu on hda1(the 80GB) and the current one on hda2.

You must be mistaken...You can't have two disks with partitions 'hda_'
Winxp (80gb) and linux / (120gb) are hdb_ and hda_, or vice-versa.  

Maybe I'm missing something, but I would just leave linux on your 120gb as is, wipe the 80 clean (if you really want to dump windows for good) and format it as ext3 (one or several partitions if you like), swap the drives if you want the 120 as master (assuming they're pata drives on the same cable) and then do what the poster above suggested and transfer all your music and movies over to 80 or 120, convert them from ntfs to ext3, and then copy everything back.  

why not just do that?  You can also resize and add partitions to the 120 if you're not happy with it.

---

