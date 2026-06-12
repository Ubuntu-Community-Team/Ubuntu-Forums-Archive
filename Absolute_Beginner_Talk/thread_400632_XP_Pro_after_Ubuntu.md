---
title: "XP Pro after Ubuntu"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by elcapy on 2007-04-03
Hello all, any help is better than none, so please post whatever you think can help!!!

Well this is the problem: I want to install XP on a diff Partition, same harddrive. I would like some links to instructions on how to do it since installing ubuntu after XP did not work. I formatted the HD and need to put XP back on. I have no Idea how this would work but I know Grub will be wiped out so I think I can use the XP loader to do this. well, Thanks all in advance...


Here is some details
partition 1 is reserved for XP 195.3 gigs
partition 2 Ubuntu LTS 6.06    38 gigs
partition 3 Linux Swap

---

### Post by freebird54 on 2007-04-03
I am not too sure about why you want to move it.  I am not aware of anything more tricky than trying to get XP to live anywhere else than the first partition!  Ubuntu can boot off Exiended partitions, different drives, CD's etc- but up till Vista WIn wants to be first.

If it is a matter of more space for other things, resizing the XP should do the job.  If not - what final result are you hoping/planning for?

---

### Post by mikewhatever on 2007-04-03
You can easily reinstall grub after having finished with Windows installation, and then manually add an entry for Windows to the end of GRUB menu.lst. Hopefully that was the question you wanted answered, because I wasn't sure.
Here is an exelent grub page for general info [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Here is how to reinstall grub using Ubuntu live cd 
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by raja on 2007-04-03
You can reinstall XP and as you said, it will overwrite the MBR. Windows' boot loader will not recognize the linux partition. So you will have to reinstall grub for that. An alternative is to use SuperGrubdisk. Have a look at [this link]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no").

---

