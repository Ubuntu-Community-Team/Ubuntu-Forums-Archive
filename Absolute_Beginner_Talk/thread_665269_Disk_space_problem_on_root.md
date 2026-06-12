---
title: "Disk space problem on root"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Khane on 2008-01-12
I am using Kubuntu for something like 2 weeks and during this period of time I never checked the state of my disk space. Then I decided to install Ubuntu on Kubuntu to be able to switch between them and see which one I prefer but during the process I encountered several problems and at some time I got a "*dpkg: failed to write status record about `librsvg2-2' to `/var/lib/dpkg/status': No space left on device*" message. With the help of one of the forum poster I found that I had a lack of free space on my Ubuntu root (/dev/sda6   Size: 2.8GB   Used: 2.8GB   Available: 0  Used:  100% ). Running "sudo apt-get clean" and "df -h" I got some free space --> /dev/sda6   Size: 2.8GB   Used: 2.3GB   Available: 341  Used:  88%. Then I ran "*sudo apt-get update*" and "*sudo apt-get install ubuntu-desktop*" and now I can log into Kubuntu and Ubuntu.

I checked again my disk space and got this result for /dev/sda6 --> Size: 2.8GB   Used: 2.7GB   Available: 0 Used: 100% (the state of /home is -> /dev/sda8  Size: 9.2GB   Used: 553M   Available: 8.2GB  Used: 7%)
 

I am no computer geek, I am new to Kubuntu/Ubuntu and I still don't have a clear idea how things work; I would like to know if what seems to me as disk space problem on root is not going to pause a problem. Is it normal and if not then how is it possible (if needed at all) to free some more space ?

Thanks
Khane

---

### Post by fiddledd on 2008-01-12
if you want to increase the size of your root partition, run the LiveCD and use GParted. you can then shrink Home partation and resize root.

---

### Post by Khane on 2008-01-12
> **fiddledd said:**
> if you want to increase the size of your root partition, run the LiveCD and use GParted. you can then shrink Home partation and resize root.

Thanks, I'll try that
Khane

---

### Post by Khane on 2008-01-12
I can't find Gparted on Ubuntu 7.10 live cd  (downloaded two weeks ago)  :confused:

Khane

---

### Post by dcstar on 2008-01-12
> **Khane said:**
> I can't find Gparted on Ubuntu 7.10 live cd  (downloaded two weeks ago)  :confused:

Khane

System-Administration-Partition Editor

---

### Post by JaBa02 on 2008-01-12
maybe you need clean old packages:
```
apt-get autoclan
apt-get clean
```

---

### Post by Khane on 2008-01-12
> **dcstar said:**
> System-Administration-Partition Editor

Woops :oops:

I did it but something strange happened. I resized /home from 9.2GB to 8.2GB to get 1GB free for root. When it was done I saw that /home was now 3.8GB and that there was now a bit more than 1GB free.

I configured Gparted to resize root from 2.8 to 3.8 but right after the beginning of the process I felt that I was no sure about what I was doing and I decided to stop the process and read a bit the Gparted help files before going on. I clicked on the "Cancel" option. It took some minutes for the process to stop and then when Gparted opened again I saw that root was not 2.8GB anymore but 3.8GB as if I did not cancel the process. I also saw that the used part of of root was 3.7GB and that there was still not free space in root. The strange thing is that when I logged into Kubuntu and ran "df -h" , contrary to Gparted the result for root was still 2.8GB with 2.7 used with no free space (exactly like before using Gparted) and /home was indeed resized from 9.2GB to 8.2GB

So who is right, Gparted or the results of "df -h" ?

---

