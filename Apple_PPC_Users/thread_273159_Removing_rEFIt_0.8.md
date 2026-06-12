---
title: "Removing rEFIt 0.8?"
date: 2006-10-07
forum: Apple PPC Users
---

### Post by Greywhind on 2006-10-07
Hello again, everyone - you may not remember me, but I tried a month or two ago to dual-boot Mac and Ubuntu, and ended up getting it working, partly, but then deciding to remove it and start over another time.

I had reinstalled OS X and backed up my hard drive, and I decided to give this another try.

I installed rEFIt 0.8 and installed Boot Camp. I used the enable-always.sh script in rEFIt, and tried to partition with Boot Camp, but it said I should repair the disk with Disk utility. So I did, tried again, and it still failed.

Then I tried using the command line to repartition nondestructively, same result.

I decided it must be rEFIt causing the problem, so I went into the System Preferences, changed the startup disk to Mac OS X 10.4.8, and restarted. This should have removed rEFIt from the startup process, but instead it came up with the rEFIt menu.

I tried it again, and also tried using enable.sh rather than enable-always.sh, but nothing changed - it still loads the rEFIt menu before anything else whether I hold a key or not.

**Is there any way to get rEFIt to stop coming up without wiping my hard drive first?** If not, I'll probably just leave it there, but that will mean that I cannot install Ubuntu, since I can't partition.

Thanks.

---

### Post by hajk on 2006-10-07
Yes, removing rEFIt isn't all that straightforward... Have a look at one of the notes on my site (see sig) that gives instructions on how to do it.

---

### Post by Greywhind on 2006-10-07
Thanks for the advice - I found the advice on your site to select Mac OS X as the startup disk, restart, and remove the rEFIt folder... I had already tried that -

But when I restarted after selecting Mac OS X in System Preferences->Startup Disk, it didn't boot itself without rEFIt coming up first... so I don't want to remove rEFIt, for fear that my computer will then not boot.

Is that normal for this removal? Should I remove the rEFIt folder even though it still appears to be using it at startup? Or did the selection of Mac not re-bless the startup disk? In that case, what should I do to remove rEFIt and not make the computer un-bootable.

---

### Post by hajk on 2006-10-07
Please follow all the instructions! You must first remove the Ubuntu partitions and replace them with a single NTFS partition. Only then do you rebless the Mac HD, etc.

---

### Post by Greywhind on 2006-10-07
Oh - I see. You thought I had already installed Ubuntu. I haven't, so I can't remove it.

Actually, all I have done is installed rEFIt - I never even managed to partition my drive to get Ubuntu installed, which is why I want to remove rEFIt (so I can see if it was preventing me from partitioning).

---

### Post by Greywhind on 2006-10-08
I fixed the problem with help from the creator of rEFIt.

For others who cannot figure out how to remove rEFIt 0.8:

If you installed it by the installer and not by hand, simply delete the efi folder that it placed in your hard drive, and delete the rEFIt helper item from your Library->Startup Items folder.

If you installed it by hand, simply select Mac OS X in System Preferences->Startup Disk to rebless the disk, and then delete the efi folder.

I hope this helps anyone who has this same problem - also, check the documentation at the rEFIt website - it's now updated to reflect this change in removal procedure.

It also turned out that that wasn't my problem for partitioning - but I repaired my disk with the install CD (it said it had to repair a minor header problem) and I will try partitioning again tomorrow.

---

