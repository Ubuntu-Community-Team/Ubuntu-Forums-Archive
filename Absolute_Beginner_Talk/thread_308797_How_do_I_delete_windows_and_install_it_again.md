---
title: "How do I delete windows and install it again?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by britt-stinker on 2006-11-28
Hi everyone!
I have had Ubuntu for a few days now and I'm really liking it so far. I have a few problems with it, I will not dive into all of them here. 
The problem I need help with is how to delete windows and back install it again without it using very much space. I need it to run to programs(ableton live and adobe audition). 
So until they are supported in linux I need windows for those two. 
But I'm a little unshure if it would be better just to defract(?) windows or delete and install it again. 

Please help, thanks!

---

### Post by John.Michael.Kane on 2006-11-28
Sounds like you want to dual boot windows,and ubuntu.

These should get you going.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by turbojugend_gr on 2006-11-28
Note grub might be erased after windwos reinstallation, you can restoreit using on of these how to's:

1. [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)
2. [www.ubuntuguide.org](www.ubuntuguide.org), press CTRL+F, and search for "restore grub"

---

### Post by nickburns on 2006-11-28
If you have a good system, you may want to go the vmware option.  Then you don't have to dual boot anymore!!!

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by britt-stinker on 2006-11-29
Hi! And thanks for the posts.
I think I will go with the vmware option. But I still need some help removing windows. Can anyone help me with that?

Thanks

---

### Post by smoker on 2006-11-29
quickest way to get rid of windows is to re-format your windows partition, to ext3, preferably if only using ubuntu. use qtparted or gparted partitioner within ubuntu for this.

you will also have to edit out the windows option from the grub boot list.

---

### Post by seshomaru samma on 2006-11-29
You can use Ubuntu's live Cd to format your whole drive using an application called gparted
I don't remember if it is installed by default on the live Cd
If not you can easily install it by writing this in the terminal:
```
sudo apt-get install gparted
```

---

### Post by britt-stinker on 2006-11-29
I used gparted. I unmounted the windowshdd but now it says unallocated and now  I can't do anything with it. Any help?

---

### Post by gn2 on 2006-11-29
Do you have two hard drives? If so this may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

If you have one hard drive, insert Windows install CD and re-boot with CD first in BIOS boot order. 

You will then get the option to install Windows to the unallocated space, and create a partition first. 

You can tell the Windows installer what size you want the new partition to be. This will allow you to create a smaller partition and leave some unallocated space. 

Gparted*should* be able to merge this unallocated space into another partition.
(Partition Magic can, but I've never used gparted so can't swear to it)

After you've re-installed Windows you will need to re-install Grub. This can be done with the Super-Grub disc.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Good Luck

---

### Post by britt-stinker on 2006-11-29
I can't rezize the ubuntu partion to get the extra GB, it says the partion is busy.

---

### Post by gn2 on 2006-11-29
If you've got Windows installed in a reduced partition, the size you want it, and gparted won't absorb back the unallocated space, one solution, albeit very drastic and not at all technically elegant, would be to completely delete the Linux partitions and re-install Ubuntu.

Hammer to crack a nut...

Another way would be to use a different partitioning tool.
Know anyone nearby with a copy of Partition Magic?

---

### Post by nickburns on 2006-11-29
I was once in the same situation, and let me tell you I tried all kinds of ways to repartition and was successful.  But I was never happy until I totally reinstalled Ubuntu and during the install choose to use my entire hard drive as ext3 and gave up on the old windows partition all together.

Just a thought, I know it will be some work to save everything, but it might be the best option.

---

### Post by britt-stinker on 2006-12-03
Thanks all. I choosed just to reinstall linux again, so I could run windows in vmware. But I have a slight problem with vmware, I cant get it to connect to the shared folders in linux. Can anyone help me with this?

Thanks

---

### Post by nickburns on 2006-12-04
you will have to set up the shared folder as a network share, even though it is on the same machine.  Or you can use a thumb drive to share or some other means.  But you cannot just point to some directory on the HD and share through vmware.

---

