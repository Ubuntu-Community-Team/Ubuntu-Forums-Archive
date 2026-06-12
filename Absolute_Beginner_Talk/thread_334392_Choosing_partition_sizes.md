---
title: "Choosing partition sizes"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by fizikz on 2007-01-08
I'm getting a laptop preloaded with Windows XP MC, and I would like to make it a dual boot setup. How would you recommend splitting up 160GB between an XP partition, a data partition, and a linux partition? I will have some games installed in the Windows partition, so my initial thought was 50/100/10. I would obviously like to maximize the data portion without leaving myself with too little for the OS partitions. What do you think?

---

### Post by philip360 on 2007-01-08
I found this page helpful for deciding partitions.  [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
There are lots of good tutorials on other stuff as well. Philip

---

### Post by glabouni on 2007-01-08
let's assume you know the size you need for windows partition (I would personally never give more than 10GB to windows, and would have installed the games in the big partition)

if you want your big data partition to be usable under both windows and linux, you should go for fat32, avoid NTFS as writing to NTFS from linux is quite stable bue still experimental and writing to ext2/ext3 from windows is quite stable but still experimental.. but be aware that using fat32 for a big partition is a bad choice, big partition would profit of NTFS or ext3.

now for the linux part.

you'll have to plan 3 partitions: 
- a / partition to store the linux system itself, please note that burning DVDs from linux may require up to 4Go of tmp space and I have ubuntu, kubuntu and xubuntu installed along with many other apps and my / is 2.5GB
- a /home partition to store all your personal files and documents (where you can add a link to the big data partition
- a swap partition depending on how much ram you have. I go with a 1GB swap partitionjust in case.

further reading: [linux partition howto]("http://tldp.org/HOWTO/Partition/")

---

### Post by smoker on 2007-01-08
> I'm getting a laptop preloaded with Windows XP MC, and I would like to make it a dual boot setup...

just a word of caution about your xp mc, some laptops will not supply a copy of windows, instead they either  have a recovery disk, or a secret partition, which stores a recovery option. invariably, these recovery options usually default your system to an 'as it left the factory state', therefore, if you ever need to reinstall windows, as is common with that operating system, you may lose your linux partitions. the best way around this is to make an image of your windows partition and keep this safe, therefore, if you ever have to reinstall windows, you can just copy the image over to that partition.

of course, you may receive a windows disk, so above may not be required.

---

### Post by oracle5 on 2007-01-08
I have a 80Gb hd which means its really about 75 and I have 55Gb for windows, 10Gb for Ubuntu and a 10Gb fat32 where I keep most of my documents from both operating systems. Plus I have an external hard drive that I keep all these documents backed up too along with backups of the entire computer.

oracle5

---

### Post by fizikz on 2007-01-08
I just realized that FAT32 has a file size limit of 4GB, and that is obviously not good for the data partition. So, now I need to decide what file systems to use for the different partitions. Windows will be NTFS, linux will be ext3 (I guess. What's the difference between ext2 and ext3?). Now, for the data partition, I no longer want to use FAT32 due to the file size limit. I suppose I could use ext2 and FS-Drive ([http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)) as suggested in the link by Philip. How stable would this arrangement be? 

glabouni, if I were to install the games in the large data partition, would there be problems if I were to reinstall windows? i.e. the games would no longer be in the registry, etc. This is why I thought it best to keep the programs in the Windows partition. Please correct me if I'm wrong.

smoker, thanks for pointing that out. I hope it comes with a CD copy of windows, but I don't yet as I have yet to receive the laptop. I will know soon. ;)

oracle5, thanks for the info. I suppose my 50/100/10 guess wasn't too bad. Now if I can decide on the right file systems...

I'm not sure about how large the swap partition should be, but FYO, the laptop has 2GB of RAM.

---

### Post by oracle5 on 2007-01-08
I use to have a swap partition but I got rid of it since I never use it. I have a little over a gig of ram(a gig stick and a 256 stick). Most people suggest you have one anyway though but I don't have any use for one when I rarely use over 250-300 or so Mb to run everything I want.

oracle5

---

