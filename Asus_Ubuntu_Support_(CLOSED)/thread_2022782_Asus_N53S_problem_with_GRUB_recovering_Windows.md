---
title: "Asus N53S problem with GRUB recovering Windows"
date: 2012-07-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by diegocaprioli on 2012-07-11
Hello,

I have a new Asus N53S, which came with a Windows 7 default installation. I'm not a big fan of Windows, so my idea was to delete Windows and install Ubuntu, but mantaining the hidden recovery partiton, so I can recover Windows 7 later if I need to sell it. I created the recovery DVDs (5 DVDs) just in case also.

So, my first step was to delete the Windows partitions, and mantain the hidden one. Then I created the Linux paritions (/, /home, and swap). The Ubuntu installation went great, and Ubuntu worked fine. Also GRUB recognized the Recovery partition and listed it in the menú options during boot.

So confident in this, I tryed to do a Windows Recovery just to test it, and verify that all went well. I restarted the notebook, and selected the Windows Recovery Partition from the GRUB menu, and the process started. The recovery completed ok, but on the next restart, it didn't boot properly on Windows, but instead throws an error, indicating that a partition is not present, and shows what it seems to be a GRUB console...

I don't know what to do from here. I'm sure that the recovery partition is fine, because the process went well. It seems that GRUB is still somewhere trying to read the boot configuration of Ubuntu, but its not there anymore... Is there any way to remove grub and let the system boot correctly from the recovered Windows partition?

Thanks in advance!

---

