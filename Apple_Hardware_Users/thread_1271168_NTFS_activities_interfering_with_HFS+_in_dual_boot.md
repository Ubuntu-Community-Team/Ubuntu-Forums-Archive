---
title: "NTFS activities interfering with HFS+ in dual boot?"
date: 2009-09-20
forum: Apple Hardware Users
---

### Post by platinumlolita on 2009-09-20
I've recently resized a HFS+ partition on an x86 iMac and replaced the remaining space with an NTFS partition running Windows 7 Ultimate. This was approximately (give or take a week) when a user began complaining about flakiness in his log in process in Mac OS Leopard on the HFS+ partition. An administrator claims that the Windows partition is "slowing down" the Mac OS partition, and that it is producing serious parental control errors in managed accounts. However, only one managed Mac account is "flaky," and I can attribute this directly with the user's poor maintainence with the file system. What I am asking is if my administrator's claims are correct and if the Windows operations in an entirely different session on an entirely different partition are changing any operations in the Mac OS partition.

---

### Post by platinumlolita on 2009-09-20
Oh, and it's important to note that I have never installed drivers for HFS+ on the Windows partition, and all HFS+ partitions connected during a Windows 7 session are entirely unreadable. I've also never installed drivers in the Mac OS partition that allow users to write NTFS partitions. This eliminates any possible way for the partitions to write on eachother, thus eliminating the possibility for them to be altering each other's data.

---

### Post by execneaux33 on 2009-09-20
That second post concludes it! If the operating systems can't write on each other, there isn't going to be a problem like that. When you say poor maintenance, what do you mean? Do you mean like multiple temporary directories staying in the RAM and resetting internal clocks? Ever see unusual changes in the Mac clock system, screwing with time limits in Leopard?

---

### Post by drrobygail4a on 2009-09-20
> **execneaux33 said:**
> That second post concludes it! If the operating systems can't write on each other, there isn't going to be a problem like that. When you say poor maintenance, what do you mean? Do you mean like multiple temporary directories staying in the RAM and resetting internal clocks? Ever see unusual changes in the Mac clock system, screwing with time limits in Leopard?

That might be too abstract. It could be something as simple as having too many really small files in a particular directory, particularly code snippets or photos. I'm sure that the backing up of the "flaky" account's files, deletion of the account, and creation of a new account where the backed up files would be put will fix everything. Come back to us on this!

And if the administrator decides to delete the NTFS partition, he'll just have a flaky account and loads of space that can't be resized again into the HFS+ partition; basically, a headache and an angry user. Just take my advice and tell me what happens.

---

### Post by execneaux33 on 2009-09-20
> **drrobygail4a said:**
> That might be too abstract. It could be something as simple as having too many really small files in a particular directory, particularly code snippets or photos. I'm sure that the backing up of the "flaky" account's files, deletion of the account, and creation of a new account where the backed up files would be put will fix everything. Come back to us on this!

And if the administrator decides to delete the NTFS partition, he'll just have a flaky account and loads of space that can't be resized again into the HFS+ partition; basically, a headache and an angry user. Just take my advice and tell me what happens.

Nice answer! I hope it works.

Really, a partition and a bunch of free space for junk is just a migraine. Save the admin a heap of trouble and just do what drrobygail4a says.

---

### Post by platinumlolita on 2009-09-20
Thanks, guys! That's really helpful! The flaky account in question is indeed full of hundreds of LOLcat photos and almost a year of uncleared browser history, as well as doubled downloads and such. This should save us all some space.

---

### Post by drrobygail4a on 2009-09-20
\\:D/
Hehe if it's lol cat then there's no way theres code snippets. And lemme guess, streamed videos being downloaded in bulk batches?

Yeah sounds like an 11 year old.

---

### Post by platinumlolita on 2009-09-20
> **drrobygail4a said:**
> \\:D/
Hehe if it's lol cat then there's no way theres code snippets. And lemme guess, streamed videos being downloaded in bulk batches?

Yeah sounds like an 11 year old.

Nope! A wannabe 12chan with nothing to do! But haha

---

