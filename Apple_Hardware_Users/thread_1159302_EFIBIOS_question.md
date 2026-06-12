---
title: "EFI/BIOS question"
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by bravo.citoyen on 2009-05-14
Hello!  I'm looking to install Ubuntu 9.04 on my Macbook Pro 5,1 at some point in the near future.  In advance, I consulted some of the guides, and found on the General Mac Intel install page ([https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)) the following information:

"Intel Macs have an EFI instead of a BIOS (such as a typical PC contains). With this change, a different partition table scheme (GPT) is used on the hard drive. The EFI of your Mac, however, is capable of utilizing the older partition table format (MBR) for compatibility. Since the recommended Ubuntu installation methods use the "legacy mode" of the EFI anyway, it make sense for a single-booter to convert their hard drive back to the older style."

Though I don't have a lot of knowledge on this subject, it seems like that's a rather more serious change than partitioning.  After going through the procedure necessary to make this change and installing Ubuntu, if I should ever want to return to OS X, will that pose a problem?  If so, can it be undone by a similar process?

Thanks in advance for any help!

---

### Post by cyberdork33 on 2009-05-14
I'd suggest dual booting first to see if you like things, then you can move to a single boot later. In fact, I am not sure that single booting will work the same as it once did now anyway (you can always try).

OSX will only install to a GPT disk (but it can run from a non-GPT disk). Basically, switching between GPT and a legacy MBR-style table means that you have to wipe the entire drive out. If that is OK, then go for it.

gparted (on the ubuntu livecd at System > Administration > Partition Editor) can switch between the partitioning formats. After starting gparted, go to device > Create Partition Table... In the dialog that pops up, you can click the small triangle next to "Advanced" and choose the table type you want GPT vs msdos. None of the other will make sense for you to use.

---

### Post by maflynn on 2009-05-14
I recommend creating a dual boot solution as well. What I did is I used my bootcamp partition that I created for windows. If you don't have that generated, do that first, and then install ubunutu on that partition. 

I highly recommend you have a recent backup of OSX and your data, I've seen too many people select the wrong partition and install over OSX.

I also recommend you download and install the rEFIt software. This provides a boot between OSX and  Ubuntu.  It saves you from depressing the option key during reboots and then selecting the ubuntu partition.

---

