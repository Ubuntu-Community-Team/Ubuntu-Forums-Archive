---
title: "Asus K53SJ internal harddrive WDC WD3200BVPT partitions misaligned"
date: 2012-05-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Superpelican12 on 2012-05-06
Hello,

I have an Asus K53SJ-SX216V laptop which' s internal HDD is a Western Digital WD3200BVPT-80ZEST0. It has a quad core Intel Core i3-2100M processor (2nd generation Sandy Bridge) running @ 2,1 GHz. It came with Windows 7 stock. However I installed Ubuntu 11.10 on it. Than I upgraded to 12.04 and then I decided to delete the "Ubuntu-Desktop package" and install "Xubuntu-Desktop" (XFCE etc.) to kind a like transition Ubuntu to Xubuntu.

However I find the boot time quite long for a modern quad core processor @ 2,1 GHz (may be I'm wrong). I was interested if I could shorten the boot time. After a bit of searching I found a article in the Ubuntu Documention about DMA. It suggested to run a hdparm command. But I needed to know which parameter (which disk) I must add. So I used Disk Utility to determine the right disk (sdx)and it says that the Windows Recovery partition is misaligned by 512 bytes, the Windows "OS" partition is misaligned by 1536 bytes. While I also have a Extented partition which houses the Windows "Data" partition, my Linux Swap partition and my Ext4 home partition. When I click on the extended partition in Disk Utility it says that it is misaligned by 1024 bytes. However when I click on one of individual partitions (which the Extended Partition contains) it doesn't show a warning. 

Now I have 3 questions:

1. If the Extended Partition is really misaligned will the partitions which it contains (the Ext4 home partition, the Swap and the Windows Data partition)also be affected? Will this affect my system' s performance if the Ext4 home partition and/or the Swap are misaligned?

2. Should I worry about the messages "The partition is misaligned by x bytes. This may result in very poor performance." Or isn't it that important or is it a bug?

3. Could this really increase my boot time?

The system is fine while using it. No lag, resource usage is very low (Xubuntu is great! :) ) as it should be. The only thing I notice is the boot time.


Also I have read about that some WDC harddisks use the "Advanced Format" system and blocks of 4048 bytes/4K. And this seems to result in very bad performance on Linux. Sadly I found out that my internal (stock) WD3200BVPT harddisk seems to also use Advanced Format. Maybe this has something to do with the misalignment warning.

---

