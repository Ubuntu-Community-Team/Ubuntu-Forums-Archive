---
title: "Brand new to Linux, can't install."
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by aztec1 on 2006-09-18
Hello everyone,

I want to move away from Windows, and heard about Ubuntu and thought I'd try it. This is the first time I have ever tried Linux. However, I cannot get it to install to the hard drive. I was trying to dual boot and read extensively about it...I think I did everything right and everything went good until the reboot.

Here's what I've tried so far:
1- Install from live CD: booted back into Windows, no choice.
2- Use gparted first, before installing from live CD: boots back into Windows, no choice.
3- Tried to repair using alternate CD and reinstalling GRUB: got a halt error 20 when the GRUB reinstall was at 50%.
4- Install from alternate CD: "error loading operating system" after reboot. GRUB was installed on the MBR. Cannot boot into either OS.

My Windows install is borked now, so I am using the live cd now. If anyone can help me, it would be much appreciated. Thanks!

---

### Post by orb9220 on 2006-09-18
Boot with xp cd and enter recovery mode.
type: fixmbr or fixboot I forget at the prompt
that will restore mbr and allow you to boot back to windows.

What is your HD and patitions? Also when back in xp defrag like hell. A fragmented disk will choke gpart.

---

### Post by aztec1 on 2006-09-18
Thank you orb, I will try the recovery mode in XP.

My HD is a 60Gb SATA, partitioned 6GB (NTFS), 6GB (NTFS), 12GB (FAT32),1GB (swap). The rest is unallocated now, was plannig to share it between OSes.

How does defragging another partition affect how the gparted works? Or is this my now-outmoded "Windows" way of thinking? :D 

Thanks again for your help!

---

### Post by aztec1 on 2006-09-18
Many thanks Orb! Windows boots now.

I have defragged every partition on the hard drive that I had access to, it's time to try again...I can't wait to start using Ubuntu!

---

### Post by petri on 2006-09-18
> **aztec1 said:**
> Thank you orb, I will try the recovery mode in XP.

My HD is a 60Gb SATA, partitioned 6GB (NTFS), 6GB (NTFS), 12GB (FAT32),1GB (swap). The rest is unallocated now, was plannig to share it between OSes.

How does defragging another partition affect how the gparted works? Or is this my now-outmoded "Windows" way of thinking? :D 

Thanks again for your help!

I think if you have not defragmented your windows partition which you are going to resize the risk is that some windows data will be left under the new partition and tehy will be gone.

- Are you trying to install Ubuntu on a ntfs formatted? No go. 
- How is your Live-session working?

 There is a couple of good websites about installation:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) and [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Maybe you find something helpful there. However it is important to learn some new things when you start with Linux. See my sig for Linux Lessons for later on

---

### Post by jocheem67 on 2006-09-18
It could be smart to use your xp cd to make the space you wanna use for linux " unallocated " . It's my experience that grub likes it better that way, when Ubuntu can just use unallocated space instead of formatting a fat32 or NTFS partition.

---

