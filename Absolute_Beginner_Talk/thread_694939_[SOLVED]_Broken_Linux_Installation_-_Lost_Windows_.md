---
title: "[SOLVED] Broken Linux Installation - Lost Windows Partition"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by camellochapin on 2008-02-12
Hi,

during the weekend I was installing Xubuntu 7.10 on the Laptop from work, forgot to plug the AC adaptor and the inevitable happened... ran out of battery and the installation procedure was broken.  I know I know, there is no solution for human stupidity :mad:.  I followed all the steps to save my "Windus Vista" partition (with 60GB of HD space used), and using by that time just 10 GB of free space for my Xubuntu partition.

Ok, it crashed...

.... next day, I reinstalled it again using the LiveCD, this time proplerly plugged to the AC outlet.

I followed again all the steps, and after rebooting... voilá... my Windows partition was gone!  now I have "several" partitions... at least 4!  As you can see in the attached image file, there exists at least the following partitions:

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda6

from this four partitions, the active and running Xubuntu partition is located on "/dev/sda6", the others I can't access... ok, I can but the one located on "sda2" with 55.14GB (similar to my original Windows partition) has a "lost+found" folder, with wich I don't know what to do.

So, did I erase my Windows partition?  If not, can I recover it somehow?

Plesae, help me!  It's the laptop from the company, and I did all this without consultation :)

Any further information you might need, don't hesitate to request it!

---

### Post by Joeb454 on 2008-02-12
Erm...I hate to be the bearer of bad news, but looks like you've overwritten Windows...unless you've managed to get it - and it's contents into 1.46Gb

Sorry :(

---

### Post by camellochapin on 2008-02-13
> **Joeb454 said:**
> Erm...I hate to be the bearer of bad news, but looks like you've overwritten Windows...unless you've managed to get it - and it's contents into 1.46Gb

Sorry :(

I used testdsk it helped me to find that the biggest partition is still a NTFS partition.. but nothing could be done... so yeap, I erased Vista :popcorn: :guitar:  

Unfortunately the PC is from the company, and we "need" to have it back... unfortunately most software for the Automation Industry just runs under "Microsucks Windus"

Thanks anyway

---

### Post by seventhc on 2008-02-13
If you have your windows disk, just reinstall vista, then you can safely install xubuntu onto a second partition. While I am not familiar with the xubunutu installation menu, on ubuntu there is a choice. By default it is set to use the entire disk, which will wipe windows, or you can choose [COLOR=Blue]*use largest continuous free space*[/COLOR] which will give you a dual boot.
I am not sure of the options in xubuntu, but I would think there is something similar if not the same in choices.
Sorry about your lost windows.

---

### Post by kellemes on 2008-02-13
Yeah, it seems Windows is gone..:(

I think manual setting up your partitionscheme is the way to go, that way you see what you're doing.. The partition-editoer shows you all available partitions (including the NTFS partition).. as long as you simply don't let it format this partition (mounting you may do), you'll be fine..

---

