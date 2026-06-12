---
title: "Edgy, VMware, and Xen"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Asteroza on 2006-11-07
Hello all. I thank you in advance for reading this because it's pretty long.

Important information first. I have a small amount of experience with linux, mostly debian and redhat. The machine I wish to install Edgy on is a Dell Dimension 9200. I plan on dualbooting windows XP and Edgy. My plan is to experiment with Xen and VMware server on Edgy. This is a work computer that is mostly mine to do with as I please, but I have to be prepared for the possibility that the machine may be given to someone else in the future. I have read some of the howtoforge articles on Edgy, Xen, and VMware.

Notes

1. I have read that Dapper Drake will install on the Dell, but that the NIC driver is not on the install disk. The driver does exist on the Edgy install disk however, so it seemed reasonable to jump up to Edgy for installation.

2. Based on what I have read so far, VMware server is currently not very happy on Edgy. People have reported mixed success, and the threads are mess when it comes to finding a unified set of solution steps. Some have reported better success with VMware player, but again, the solution steps are a little hard to follow or determine if they were at all effective.

3. VMware uses kernel modifications that do not play nice with Xen.

4. Based on various howto articles, it appears for Xen that a better choice as far as partitioning is a 128MB /boot partition, followed by a primary monolithic partition with LVM, and dump the other major / directories as individual LVM partitions, preferably as ReiserFS so they are resizeable.

5. I plan on attempting to use VMware guest OS images to be available to both windows XP and Edgy.

6. I am not using SATA RAID


So, my initial thoughts are to arrange partitions something like the following;

1. Dell recovery partition (figure I shouldn't kill it if I don't have a pressing need)
2. XP NTFS 40GB
3. shared virtual machine guest OS image partition (FAT32 or ext2?)
4. /boot
5. big LVM partiton with the rest of Ubuntu

The shared partition is a problem point. I could go FAT32, but I could use the IFS kit mod for XP to allow ext2 access. Since it will be tens of GB, I am not sure what to do. Perhaps two partitions, one of each kind, to spread the risk?

I don't know if I should be concerned with allowing GRUB to install in its usual place. I have never dualbooted before. This is with regards to potentially having to hand over the computer to someone else. I suppose the next person will just do a nuke and pave install, but is there anything I should be concerned about?


The big issue I face is running Xen and VMware. Aside from the fact that getting VMware Server to run on Edgy seems to be a teeth pulling experience, the big question is the kernel. I am sadly underinformed on this issue. However, my first thought is to simply have two kernels, one for VMware and one for Xen, and boot the one I wish to use when booting into Edgy. This seems logical and simple, which means it's probably not correct.

I do not know how such a two kernel situation plays out in terms of partitioning and allocation of directory structure. Also I do not know how that plays out in terms of additional software installs, but I imagine I will need to download most if not all kernel headers. I also do not know how things work with dom0 when switching between Xen and non-Xen boot situations. The naive part of me says if the main install doubles as dom0, as long as I have the necessary source and headers, the apps and packages I install (as long as they are source packages) should work in both modes.


The usual first response to something like this has usually been to give up on trying to have two different virtualization methods installed on the host OS, somehow get VMware Server installed, and play with Xen within a virtual machine running on VMware Server, despite the performance hit. Some have suggested figuring out how to get the necessary NIC driver and steal it from Edgy to install on Dapper Drake, since VMware Server behaves much better on Dapper Drake currently. I am however avoiding Dapper Drake, not because it is older, but because if I want to upgrade to Edgy in the future, I would face a rather bad situation and it seems better to go for a clean Edgy install.


So folks, the big questions are;

1. Is the partition scheme I am thinking of using okay?
2. Is the two kernel route reasonable?
3. For the love of god is there a concise walkthrough to shoehorn a working install of VMware server onto Edgy?
4. Is a VMware installation compatible with Xen, as long as only one or the other is running (the dom0 issue)?
5. For this situation, what would be the recommened installation steps/order (Ubuntu->Xen->VMware Server)?
6. Is this a really bad idea and I should just use VMware Server on windows XP, and use Xen on Edgy exclusively?

---

