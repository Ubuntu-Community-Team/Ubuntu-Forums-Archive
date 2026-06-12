---
title: "Sata RAID card issues"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by WElliott on 2007-12-04
I have reclaimed a server and designated it for Ubuntu and VMware. The initial load was 7.04 but I have since upgraded it to 7.10. However, under both version I am unable to access the RAID array. According to Adaptec the PCI card is compatible with linux and should work. There are 4 250Gb SATA drives on this array and I intended to use the space for image storage for VMware. The system sees the array and it is even the name as specified when it was setup. But trying to access it simply generates an error of "Unable to mount media. There is probably no media in the drive."

Any suggestions or help would be greatly appreciated.

---

### Post by nonewmsgs on 2007-12-29
check the bios setting and make sure that's ok first.

then i would look at just testing one of the drives as a stand-alone drive to try to rule out the card just being bad.

---

