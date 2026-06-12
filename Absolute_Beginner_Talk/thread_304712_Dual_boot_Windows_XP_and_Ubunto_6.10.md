---
title: "Dual boot Windows XP and Ubunto 6.10"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by christian_s on 2006-11-22
Hi all,

I'm brand new to linux. Never tried it before. I got a ibm x31 laptop with 512 mb Ram and 40 Gb Harddrive. 

I've tried the Ubunto 6.10 live CD and it looks good. So now I'm trying to install it but are having some problems figuring out what  to mount where on the partitions.

Install step 5 of 6

My partition setup is like this:
/dev/dha1  NTFS  2.96 GiB size  2.22 GiB used  763.38 MiB  boot
unallocated      2.90 GiB

/dev/hda2  Ext   31.40 GIB                                 lba
 /dev/hda6 Unknown 5.86 GiB
 /dev/hda5 Unknown 996.65 MiB
 /dev/hda7 Unknown 24.56 GiB

Windows is installed on dev/hda1 NFTS partitionen.

What I would like to do is to install
hda6: ubuntu
hda5: swap for ubuntu
hda7: common files for windows and linux

In the dialog Prepare mount points I have
/windows      hda1
swap          hda5
/documents    hda7
/             hda6

when I try to use the install wizard and setup the mounts according to above I get the error message
"no root file system".

I tried to follow this tutorial 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Any suggestions on how I should proceed. The main point here is that I would like to be able to dual boot windows and linux. each OS should have 6 Gb space the rest of the 40gb disk should be used as common file space. If that is at all possible.

Other links I have browsed through
[http://ubuntuforums.org/showthread.php?t=54817](http://ubuntuforums.org/showthread.php?t=54817)
[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Any suggestions are warmly welcome
- Chr

---

### Post by akshaysrinivasan on 2006-11-22
Since you have 6.10 ,it should be possible to select the partition for installing ,but it never worked for me.Also the live cd does not allow you to choose the swap partition.

---

### Post by christian_s on 2006-11-22
Thanks akshaysrinivasan!
Do you have any suggestions to what I should do? Should I download another Ubunto 6.10 and install that?
Can the swap partition be made later?

Basically what makes me a bit uneasy with the install process is that I wouldn't like to lose the windows xp boot partition just yet. (if it should happen by accident it's no biggie, but I prefer to keep it).
- Chr

---

### Post by doobit on 2006-11-22
If you are committed to install Ubuntu, then I would recommend:
1. Install 6.06 LTS, not 6.10 because 6.06 has the long term support , that you, as a new user, really will need.
2. Use the alternate install CD because it works better.
3. Read the more detailed instruction on making partitions using the partitioning tool before you install:
[https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28boot%29%7C%28dual%29%7C%28XP%29](https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28boot%29%7C%28dual%29%7C%28XP%29)

---

### Post by christian_s on 2006-11-22
thanks doobit,
I'll check the link and look for the 6.06 version.
- Chr

---

### Post by Bartender on 2006-11-22
I don't understand your choices as far as partitioning.  I'd suggest you delete that extended partition you built, download the alternate install CD and follow [Herman's]("http://users.bigpond.net.au/hermanzone/p3.htm") directions for dual-booting with NTFS.

---

### Post by christian_s on 2006-11-22
Hi Bartender,
>>I don't understand your choices as far as partitioning.
You are 100% correct. I do not know what I did wrong during the initial windows install. I tried to make a partion for windows, one for linux and one for common files. Somehow I ended up with a very small primary partion on 3Gb for windows instead of the intended 6 Gb. The 3Gb is too small after running windows update so I had a space issue. And Windows doesn't seem to allow me to change the partition size.

I ran the Ubunto 6.10 Live CD once more and found the partitioner. Very cool tool.

I deleted all the partitions except for the windows partition. 
I re-sized the windows NTFS partion from 3Gb to 6 GB. 
Then created a new primary partion of 6 Gb for Linux.
I set the remaining HD space as extended partion and created a 1 Gb linux swap partion and set the rest to FAT32.

Now I was able to install Ubuntu 6.10 as dual boot.
dha1: \windows
dha2: \
dha5: swap
dha6: \documents

So far I have only re-booted to Windows. At first windows did a disk check due to the partition re-size and then booted just fine. I'm still installing drivers and windows updates. After that I'll look more into tuning the Ubuntu.

My original problem was that I only had one primary partition and the rest were under the extended partition.

Thanks a lot for the help all!
- Chr

---

### Post by doobit on 2006-11-22
Linux really doesn't care if the partitions are primary or extended, only Windows cares. I usually make the Windows a Primary and then make three linux logical drives out of an extended partition, for / , /swap , and /home

---

