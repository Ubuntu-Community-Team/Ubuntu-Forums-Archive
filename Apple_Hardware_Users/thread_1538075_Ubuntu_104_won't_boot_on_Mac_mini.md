---
title: "Ubuntu 10/4 won't boot on Mac mini"
date: 2010-07-24
forum: Apple Hardware Users
---

### Post by modelmaker on 2010-07-24
Attempt to install U 10.4 to dual boot with OSX on a Mac mini using a new 500 GB internal HD failed. A new 270 GB OSX volume on that drive boots via rEFIt and works OK; the U 10.4 distribution CD boots OK via rEFIt and appears to install OK.

The option to install into the ± 230 GB empty space was selected; otherwise, all settings were default. The Ubuntu installer was allowed to determine the size and placement of the new system volume and swap space. 

Post-install attempt to update MBR to agree with GPT using rEFIt partitioning tool failed.

Error:
    
    "Status: MBR Partition Table is invalid, partitions overlap"
    "Error: 'not found' returned from gptsync.efi"
    
The installed 10-4 will not boot. 

Notes: I have never used Linux, want to learn. Since I have no Linux installed, and Mac OSX will not access the Ubuntu volumes, I have no tools to troubleshoot. And being brand new to Linux, I probably would not know how to use them if they were available.

Thanks for any support --
-- MM

---

