---
title: "Lost AMD GPU with 5.3 Kernel"
date: 2019-10-31
forum: Apple Hardware Users
---

### Post by mcoyle on 2019-10-31
Hello!

I have a 2011 MacBookPro 17". Using the 5.0.x kernel, both Intel and AMD GPUs work (GPU selected using passed kernel parameters). 
Under kernel 5.3.x, the AMD Turks GPU no longer works. 

Here are the kernel parameters I'm passing via EFI boot and refind.conf:

ro acpi=force quiet splash i915.modeset=0 radeon.modeset=1

Any thought on how to get the AMDGPU back?

Thanks,
Michael

---

