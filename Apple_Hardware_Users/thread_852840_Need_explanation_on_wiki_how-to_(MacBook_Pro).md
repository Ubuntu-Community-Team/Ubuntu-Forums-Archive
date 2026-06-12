---
title: "Need explanation on wiki how-to (MacBook Pro)"
date: 2008-07-08
forum: Apple Hardware Users
---

### Post by iPodAddict181 on 2008-07-08
Alright, I just read the wiki how-to on dual booting Ubuntu and Mac OS X on a MacBook Pro (Penryn, gen 4). I need just a little bit of further explanation on the sizing of the partitions. Number six says, > Select the 'free space' and click 'New Partition'. Set the size of the partition in wich Ubuntu will be installed leaving the free space for the swap partition if needed plus the free space that you wrote down before. Set the formatting to occur at the end. Format it as an 'ext3' type partition and set the 'Mount Point' to '/'. Click OK. (Note: After finishing partitioning, the free space left by BootCamp should be the same) The wording is a little confusing, especially when it says "...leaving the free space for the swap partition if needed plus the free space that you wrote down before." Could someone make this a little easier to understand because again, the wording is a little confusing, thank you.

---

### Post by i_ll_be on 2008-07-08
For your dual boot you will need the following partitions :
1. OSX formatted as HFS+
2. Ubuntu formatted as ext3
3. Swap to be used by Ubuntu

I Think the most simple way is to resize your OSX partition from the OSX terminal.
Open the terminal an type :
> diskutil list
The command will reply something like that :
> /dev/disk0
#: type name size identifier
0: GUID_partition_scheme *233.8 GB disk0
1: EFI 200.0 MB disk0s1
2: Apple_HFS Macintosh HD 233.4 GB disk0s2

**Here my OSX partition is disk0s2**.

Then type the following command (backup of your data is advised since it is not reversible !!!). The command will give here 200 Go for OSX, 30Go for Ubuntu and 2Go for Swap :
> sudo diskutil resizeVolume **disk0s2** 200G "HFS+" Ubuntu 30G "HFS+" SWAP 2G 
Here I formatted everything in HFS+, it doesn't matter : you can reformat later during ubuntu install.

During Ubuntu install select manual partitionning, then select :
1. The 30Go partition to be formatted in ext3 and mounted as "/"
2. The 2Go partition to be used as Swap.

**At the last step of the install wizard, select Advanced and then select your 30Go partition for Grub install.**

Last thing : installing ReFit (bootloader for EFI) would be a good idea before you do anything.

Hope this help !

---

### Post by iPodAddict181 on 2008-07-08
yes, it actually did clear a lot up, thanks :D  unfortunately for me, my installation failed and i had to revert back to the live cd in order to clean up my partitions, as for now i am left without my precious ubuntu :( ill have to look deeper into the problem tomorrow, because it's 2:00am and i'm really, really tired :p ill fix it and post what was wrong and my solution

---

### Post by iPodAddict181 on 2008-07-08
I have tried to get the Mac/Ubuntu dual boot to work about three times now, and it still doesn't work. I followed the instructions very carefully and I still cannot manage to get it to work. I am not using rEIFIt. I am using a MacBook Pro 4th gen (Penryn), does anyone else have this problem? It installs fully but I cannot see it when I start up and hold 'Option'. It has messed up my Mac's partition table once, but I fixed it by going back to the live CD and deleting the partitions there. Anyone else have this problem? If you do or did, do you have a solution? It's not important to put Ubuntu on my Mac but it would be nice to. Thank you.

---

### Post by cyberdork33 on 2008-07-08
> **iPodAddict181 said:**
> I have tried to get the Mac/Ubuntu dual boot to work about three times now, and it still doesn't work. I followed the instructions very carefully and I still cannot manage to get it to work. I am not using rEIFIt. I am using a MacBook Pro 4th gen (Penryn), does anyone else have this problem? It installs fully but I cannot see it when I start up and hold 'Option'. It has messed up my Mac's partition table once, but I fixed it by going back to the live CD and deleting the partitions there. Anyone else have this problem? If you do or did, do you have a solution? It's not important to put Ubuntu on my Mac but it would be nice to. Thank you.
Please reply to your posts instead of creating a new thread so that others know what you have tried.

There is a bug in the Ubuntu installer which creates problems. You need to install rEFIt temporarily in order to fix the problem. Then you can uninstall it and use the default Option-key method.

---

### Post by bapoumba on 2008-07-08
Threads merged.

---

