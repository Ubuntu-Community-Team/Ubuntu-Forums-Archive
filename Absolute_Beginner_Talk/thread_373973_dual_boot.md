---
title: "dual boot"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by wwjoeyd on 2007-03-01
ok..
i booted with the Live CD

and i clicked install
but i do NOT want to erase Windows XP

their is an option that allows you to have both OS's correct?
which one do i pick?

thanks people

---

### Post by confused57 on 2007-03-01
> **wwjoeyd said:**
> ok..
i booted with the Live CD

and i clicked install
but i do NOT want to erase Windows XP

their is an option that allows you to have both OS's correct?
which one do i pick?

thanks people

See this guide:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Defrag your Windows partition a couple of times, back up any important data before resizing...there's always an outside chance of problems, not likely, but possible.

Added: Just in case you need to restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

I also recommend that you download & burn a copy of the Super Grub Disk(500 kb download), before installing:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD can restore Windows mbr or Linux grub & can boot Windows or Linux

---

### Post by wwjoeyd on 2007-03-01
thank you alot man

cheers

---

### Post by manojvekaria on 2007-03-01
Oh yes definitely!! 

1) Select your conuntry keyboard username etc etc
2) Then its going to ask you, where you want to install Ubuntu - Select edit partition manually
3)You are going to have a drive named  hda1 or something like that, if you only have one partition. (C Drive for windows)

Note: Its always good to have three partitions. 
            1) Fat32- Where windows is installed
            2) Fat32- Where you will keep personal documents, incase windows crashes,and you  
                 need to re-install it. You won't lose your documents.
            3) Unpartitioned Space - Where you install the new OS (Operating System like linux)

4) on the hda1 - rightclick and select new partition. about 2GB. Repeat same process for     
    another partition of about 1GB. (This might take time)

5)After the two have been made. select the 2GB one and create it as ext3 ( I don't know what
   that means)
6) Select the 1GB one and make it linux-swap. (try Rightclicking)

Now Click Forward)

now match it in the selector 
hda1-hda1
/root (or /)-ext3(new partition created- whatever its called e.g hda3)
swap-linuxswap-(the linux swap partition)

Then click forward-Its gonna comeup with summary. Click next and the installation is complete. After restarting its gonna ask where you want to boot into.



I hope this helps you.

---

