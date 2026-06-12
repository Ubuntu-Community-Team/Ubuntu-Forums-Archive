---
title: "reFit - Linux - OSX - EFI partitions - WTF"
date: 2012-08-28
forum: Apple Hardware Users
---

### Post by lizardseverywhere on 2012-08-28
so, i recently installed ubuntu to check out the advances in  the linux world since i last looked into them 10+ years ago... very  impressed, but when i tried to delete ubuntu and remove the various  partitions (which i was able to do just fine using gparted) reFIT still  displayed the damn linux logo from the install i deleted....

this is frustrating...

so i went in and looked around with the remaining partitions and noticed  the EFI partition which hadn't shown before i mistakenly tried to  install another distro over ubuntu after wiping the partition it was  on...

so i erased the EFI partition hoping that this would remove the g-damned  hold out linux boot logo in reFIT... it didn't... now i suppose i can  go back in and create a new EFI partition through gparted but that  stupid linux logo will still be there... and i'll have another problem of getting the proper information back onto the EFI partition, which i am unsure of how to do, or where to even dig up the proper information...

i want to edit my boot mbr or grub or whatever the eff apple comps use  as a boot record so that (or i am using as a boot record since i'm using  reFIT) to get rid of this damn logo, so i can install another distro of  linux and probably windows without having the damn supernumerary  logo...

i would rather not wipe the whole drive (aka the primary partition the  recovery partition) and do a fresh new install of os x (mountain lion)  because i have OSX set up just the way i want it for personal use and  work use... all my various tools and so on... 

i don't use time machine and can't do a "restore" from a previous back up... 

some one please help me out here, what are my options?  am i going to  have to bite the bullet and do a wipe of the entire drive and all its  partitions to get my MBP back to 'normal'???

PS - using a macbook pro late 2011, standard specs, 13"...

---

### Post by philcolbourn on 2012-09-01
rEFIt installs in your OS-X partition from memory.

It will be in /efi/refit in your Macintosh HD partition.

You can delete it (the /efi directory and all contents). 

Probably best to follow [these]("http://refit.sourceforge.net/doc/c1s3_remove.html") instructions - try the manual method.

Deleting your EFI partition is not so good. It has a special partition type code I think.

Use Disk Utility in Ubuntu or Mint or whatever, to recreate it: Type EFI System Partition. Mine has a label which is also 'EFI System Partition'.

Apple does not seem to use it in my case, so leave it empty. I don't know what other OS-X versions do with it.

In future, don't bother with rEFIt, or use rEFInd - they are both no longer required in my experience. rEFInd is much better in my opinion.

But do install grub-efi and remove grub-pc.

---

