---
title: "iMac 9,1 installation help needed"
date: 2010-01-23
forum: Apple Hardware Users
---

### Post by liberalist on 2010-01-23
Hi everyone,

I had Kubuntu 9.10 installed and it worked for a few weeks. The problem was that the partition tables could not be synced according to rEFIt, because Grub2 created a partition of the type "Unknown". As a result, Ubuntu had the Windows logo, but it still could boot for some time. To fix it, I looked over the internet and found a (to me) very [complicated procedure]("http://ubuntuforums.org/showthread.php?t=1297229"). 

Now, I learned that installing Ubuntu 9.04 creates less trouble. However, I wonder if I delete all the Linux partitions in gparted and install Ubuntu 9.04 again on free space, will I risk rendering my system unusable? Will it wipe out everything on my disk? I realise I need to install grub (1) to sda3. 

What is the easiest thing to do? A reinstallation? Or does 9.04 not fully support my quite new computer from March '09 (Apple iMac 20"). On a different note, I had those annoying warning beeps after the installation, which were quite upsetting. Is Ubuntu a good idea for Apple computers or should I only run it virtual or on a PC?

Thank you very much.

---

### Post by linuxopjemac on 2010-01-23
I guess you can easily try 9.04 but I am afraid that this extra partition is still there. It might give you the same trouble, unless you would delete that strange partition from within gparted (the partitioner in the installer). I also installed Karmic after Jaunty. Jaunty gives Grub1 and installs fine. You can then do an installation of Karmic over /dev/sda3 where very likely your / will be.

---

### Post by liberalist on 2010-01-23
Thanks for your kind reply. Do you know if gparted deletes everything on your drive when deleting a partition? I am still a bit hesitant: it really doesn't destroy my Mac?

---

### Post by linuxopjemac on 2010-01-23
if you go advanced and you do not select to touch your OSX partiton. Also leave that EFI partition there. Just delete the linux and that small other partition.

I would make a copy of your OSX anyway before doing all this with carbon copy cloner to some other drive.

---

