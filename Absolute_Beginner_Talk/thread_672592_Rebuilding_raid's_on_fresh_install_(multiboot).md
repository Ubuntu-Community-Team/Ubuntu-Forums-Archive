---
title: "Rebuilding raid's on fresh install (multiboot)"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Maxymillion on 2008-01-19
Hello,  no lost data or anything, just wanted some clarification on whats actually happening.

- I have a multiboot between Ubuntu/KDE4. 
- The OS hard drive is completely seperate from the raid
- raid was setup/working in Ubuntu using mdadm

Now to configure the raid in KDE4 i would just install mdadm / rebuild for 10 hours I presume, however will the raid have to be rebuilt again when i reboot back into Ubuntu?!

What happened to me, is i installed KDE4, but i never setup the raid, no devices from raid where mounted / touched at all.  I simply saw that KDE4 installed / worked, and i rebooted back into Ubuntu and during KDE4 rebooting I saw a group of messages saying "Synchronizing disk's". Of course when i got into Ubuntu i had to rebuild for 10 hours to get my data back. 

If someoone could be so kind as to clarify why  
a) the disk's synch'd when KDE4 shouldn't have seen them
b) if i rebuild the raid in KDE4,  and rebuild the raid in Ubuntu,  will i be able to multiboot between them without rebuilding everytime?!?!

Thanks for any help

---

### Post by Maxymillion on 2008-01-19
Someone pointed out Ubuntu/KDE4 multiboot doesn't make sense, so ill clarify :P

OS HDD:
Partition 1 - Ubuntu 7.10 with mdadm + raid configured
Partition 2 - Ubuntu 7.10 + KDE4 + clean install
Partition 3- Swap


Booting into Partition 2 will leave the raid broken in Partition 1 forcing a rebuild.

---

