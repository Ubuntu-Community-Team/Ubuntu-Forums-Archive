---
title: "Sync Partitions on External Drive"
date: 2009-07-02
forum: Apple Hardware Users
---

### Post by jerz on 2009-07-02
Hi,

I have followed the instructions [here]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") for dual booting OS X and Ubuntu. They are both on a external USB drive. I cannot boot into Ubuntu because the partition tables are not in sync. Refit says they are, but I am pretty sure that's because it's trying to sync the internal drive's partition tables. 

I need to sync the external drive's partition tables.

Any help is appreciated.

Thanks,
Jeremy

---

### Post by Richardcavell on 2009-07-02
Jeremy,

Ubuntu cannot be booted from an external USB drive on a Mac without using advanced techniques. This is probably the reason why your dual boot is failing.

Richard

---

### Post by jerz on 2009-07-02
Richard,

Thank you for the information. Regardless, I'd like to sync my external drive's GPT. I am fairly certain that is at least part of the issue. Refit is only syncing the internal disc. 

Any help is appreciated.

Thanks,
Jeremy

---

### Post by Richardcavell on 2009-07-03
Jerz,

Then install rEFIt on the external drive, bless it using the included refitblesser script, and boot to it.

Richard

---

### Post by jerz on 2009-07-06
Richard,

rEFIt is installed and blessed on the external drive. It is still only syncing the internal drive. I was wondering if there's another method to sync the external partition table.

Thanks.

---

### Post by cyberdork33 on 2009-07-06
rEFIt can only sync the main hard drive... you can install gptsync in ubuntu and specify what drive to sync.

---

### Post by jerz on 2009-07-06
As I thought. However, I cannot boot Ubuntu at the moment. Is there any gptsync binary for OS X? Or some/any other way to get this done?

---

