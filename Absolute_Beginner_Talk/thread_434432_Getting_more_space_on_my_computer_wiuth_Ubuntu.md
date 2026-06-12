---
title: "Getting more space on my computer wiuth Ubuntu"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-05-05
I've been using Ubuntu for the first time and am on Feisty. The hardest thing for me is getting used to the difference between Linux and Windoes --especially when it comes to usage and partitions.

After installing a few packages  my computer (esp multimedia)is freezing up especially when  I have Firefox running. 

This confuses me because I had installed a second hard drive on it to up its capacity to function. 

My File Systems table says:

/                                 2.2GB available 74%
/media/disk/                726.4MB available 70%
/media/disk 1               9.7GB available 1%
/proc/fs/nfsd                0 bytes  0%
/var/lib/nfs/rpc_pipefs   0 bytes  0%

Feisty: 
Hardware:
Memory 313.4 MB
Available disk space: 2.2GB

Originally when I installed Ubuntu -- Dapper -- four weeks ago, I configured the computer I thought for double booting with XP but I've not been able to find Windows or access anything that was on the hard disc originally So I've assumed that I displaced it with Ubuntu and didn't actually configure for the Windows boot option.. 

No loss. I prefer Ubuntu.

However if I need more space is there a way to now reconfigure the partitions to create more and "get rid" of any Windoes components without having to reinstall Ubuntu? Unless I can work through that I cannot later diagnose what may be an operations problem on this  pc.

I also need to know if Ubuntu has taken up all of my pc or not.

On Windoes I could monitor and tweak my reserves by deleting files and programs but with Ubuntu I haven't got access to the same measure nor the ready representation of what I have and haven't got to spare..

---

### Post by kfrance on 2007-05-05
I'm not sure exactly what your question is.  I would install gparted if it isn't already installed.  You can then look at the disks and see what is available and repartition things as you want.  You can install gparted from the command line with "sudo apt-get install gparted" or opening up synaptic, searching for the package and then installing it.

---

### Post by ratbagradio on 2007-05-06
Yes. gparted is fine. I sintalled it. All I need do is work out the DIY. (And read up more on partitioning).Thanks.

---

