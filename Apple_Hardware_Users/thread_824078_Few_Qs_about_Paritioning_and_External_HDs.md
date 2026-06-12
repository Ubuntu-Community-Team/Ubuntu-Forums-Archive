---
title: "Few Qs about Paritioning and External HDs"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by WillJeffery on 2008-06-09
Hey guys,

I have a few questions about partitoning and using exteranl HDs for ubuntu.

- What type of partition should I use? I'm using an app called "iPartitoner" which can format to pretty much any format under the sun, so does Linux prefer HFS+ or FAT32? Which would be the best?
- Also, what size is the minimum? I'm probabling going to go for around 30 GB..

- As for the actual installation, how do I select my external HDD (LaCie 160GB Firewire) as my installation partition? If I have it plugged in will the installation recognize it right away?

- And finally, are there any major compatibility issues if I use AMD64 vs. x86?

EDIT: -Also if you have any information about using Parallels with Ubuntu on an external HD that would be greatly appreciated :) (i.e. can it be done, will it recongnize it automaticily like it does with most Windows boots)

Thanks in advance!!

---

### Post by cyberdork33 on 2008-06-09
> **WillJeffery said:**
> - What type of partition should I use? I'm using an app called "iPartitoner" which can format to pretty much any format under the sun, so does Linux prefer HFS+ or FAT32? Which would be the best?
neither. Use a Linux-native filesystem like ext3.

> **WillJeffery said:**
> - Also, what size is the minimum? I'm probabling going to go for around 30 GB..That should be plenty. You can even go smaller than that if needed.

> **WillJeffery said:**
> - As for the actual installation, how do I select my external HDD (LaCie 160GB Firewire) as my installation partition? If I have it plugged in will the installation recognize it right away?

- And finally, are there any major compatibility issues if I use AMD64 vs. x86?

Since I assume you have an Intel Mac, I am going to point out that installing on external drives will seem to go fine, but you will not be able to boot. See the thread in the Intel FAQ in this foum.

> **WillJeffery said:**
> EDIT: -Also if you have any information about using Parallels with Ubuntu on an external HD that would be greatly appreciated :) (i.e. can it be done, will it recongnize it automaticily like it does with most Windows boots)
The VM will not care if it is on an external drive, it just mounts the hard drive image, and is only limited by the host OS access to the image file.

I would recommend VirtualBox before parallels (and actually vmware fusion before parallels.)

---

### Post by WillJeffery on 2008-06-10
Many thanks!

---

