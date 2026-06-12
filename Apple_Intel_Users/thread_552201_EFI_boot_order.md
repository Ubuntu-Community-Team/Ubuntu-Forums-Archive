---
title: "EFI boot order"
date: 2007-09-16
forum: Apple Intel Users
---

### Post by blippy on 2007-09-16
My brain hurts. I'm using a tribal version of Gutsy on my Intel iMac. I've got rEFIt installed, OS X and Ubuntu, too. I can successfully boot either OS (I almost exclusively boot Ubuntu) using rEFIt as the boot manager.

rEFIt default boots OS X, and so my question is: how do I get it to default boot Ubuntu?


I recently installed efibootmgr, but it complains about efivars. I did modprobe efivars, but it complains
FATAL: Module efivars not found.
I reported this as a bug.

I had tried sidux a while ago, and managed to create something approaching a boot option for it in sda1. It shows up in rEFIt, but IIRC it never really worked. I've since zapped both sidux (too bothersome to administer) and the loader option.

I get the impression that the whole boot issues are a series of square pegs in round holes - grub incompatabilities in GPT+MBR tables, bugs in Mac firmware preventing proper keyboard operation sometimes, and non-standard Mac EFI boot behaviour. Is this a fair characterisation?

What I'm slightly puzzled with is the following: I thought sda1 is supposed to be for EFI booting, but there is nothing in there (there used to be when I had the sidux option). I take it that the Mac tries to work out what can be booted by looking at an HFS+ partition (or whatever it's called), then adds in what it finds in sda1. Is that right? It's very confusing. Sounds like it'll be years before all this nonsense is ironed out.

---

### Post by pxwpxw on 2007-09-16
**blippy**
You can change the refit default in the macosx /efi/refit/refit.conf by uncommenting the #legacyfirst option.

The best explanation of the startup procedure and the Apple implementation is in the rEFIt  documents and the intel links there.
 [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Square pegs and round holes - yes not bad.

---

