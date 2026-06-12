---
title: "Triple Boot OSX + UBUNTU + PCBSD?"
date: 2011-02-22
forum: Apple Hardware Users
---

### Post by Colin Rovis on 2011-02-22
Hi!

I wondered whether it is possible to add a PC-BSD system to my existing OS X 10.6.6 + UBUNTU (using rEFIt)

Can anyone tell me how to resize the partition with linux and installing PC-BSD 8.1 on my Mac?

First I installed OS X and updated it to 10.6.6
Then I created a BOOTCAMP-Partition using the bootcamp-utility
Then I installed rEFIt
Then I installed UBUNTU (and the dual-boot works very well)
Now I want to add a PC-BSD

May I change the partition-size of the UBUNTU-partition without destroying MBR oder rEFIt?
If yes, will rEFIt recognize the newly installed PC-BSD?

Its sort of OSX+Multi-Linux. There is a wonderful page at 
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
but unfortunately the section is not updated yet.

Any Hints?
Thx
Colin

---

### Post by Hatsune Miku on 2011-02-23
> **Colin Rovis said:**
> Hi!

I wondered whether it is possible to add a PC-BSD system to my existing OS X 10.6.6 + UBUNTU (using rEFIt)

Can anyone tell me how to resize the partition with linux and installing PC-BSD 8.1 on my Mac?

First I installed OS X and updated it to 10.6.6
Then I created a BOOTCAMP-Partition using the bootcamp-utility
Then I installed rEFIt
Then I installed UBUNTU (and the dual-boot works very well)
Now I want to add a PC-BSD

May I change the partition-size of the UBUNTU-partition without destroying MBR oder rEFIt?
If yes, will rEFIt recognize the newly installed PC-BSD?

Its sort of OSX+Multi-Linux. There is a wonderful page at 
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
but unfortunately the section is not updated yet.

Any Hints?
Thx
Colin


BSD Kernel does not boot on any of the newer Mac models for w/e reason.

---

### Post by Colin Rovis on 2011-02-27
Thx a lot!

What are w/e reasons?

ss

---

