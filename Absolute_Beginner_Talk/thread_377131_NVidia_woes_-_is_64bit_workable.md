---
title: "NVidia woes - is 64bit workable??"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by zybercynic on 2007-03-05
Have a MSI K9N6SGM-V system - nForce 410 chipset, onboard GeForce 6100 (MCP61), onboard sound, NIC etc.

System is dual boot, no problems with Windows XP (32 bit version) - video, sound and NIC functioning without a problem.

Ubuntu 64 bit is another story. Obtained the latest 64bit drivers from NVidia for the above chipset - below is part of the dialog from the install log.
====

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '4086'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

===========================

Would Ubuntu 32 bit be any easier than this. I had to use one of my DLink NICs to get the network working - can anyone advise this newbie?

TIA

---

### Post by PriceChild on 2007-03-05
You need to read the error and realise that X needs to be stopped :)

I advise you read [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and install ubuntu's supported version.

If you need a newer version, then try [udsf]Latest_Nvidia_Dapper[/udsf] or [udsf]Latest_Nvidia_Edgy[/udsf]

---

### Post by zybercynic on 2007-03-06
> **PriceChild said:**
> You need to read the error and realise that X needs to be stopped :)

I advise you read [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and install ubuntu's supported version.

If you need a newer version, then try [udsf]Latest_Nvidia_Dapper[/udsf] or [udsf]Latest_Nvidia_Edgy[/udsf]

Thanks, that worked.

Now for the onboard sound and nic. Clues anyone?

---

### Post by PriceChild on 2007-03-06
> **zybercynic said:**
> Thanks, that worked.

Now for the onboard sound and nic. Clues anyone?Might want to start a new thread to get noticed as those are different topics.

If the nic isn't detected on boot I think you're gonna find it difficult to get working after :(

Pricey

---

