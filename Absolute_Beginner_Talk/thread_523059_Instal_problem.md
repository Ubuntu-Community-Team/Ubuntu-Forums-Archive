---
title: "Instal problem"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by andyjl on 2007-08-11
I am trying to install xubuntu-7.04-desktop-i386 and am having loads of probs. i keep getting "the ext3 file system creation in partition 1 of IDE1 master (hda) failed"  i have tried doing this manual and guided and it still comes up with same error.I have also switched hard drive in case it was bad. i'm just about to give up linux, if i cant even get through a bloody install

---

### Post by SOULRiDER on 2007-08-11
If youre goint to take your whole hard drive i suggets you manually edit the aprtition table, delete all partitions and then create one, but remember youre gonna need a swap partition too!

Could you give us some mor einformation on the partitions in your hard drive and how you want the new partitions to be?

---

### Post by overdrank on 2007-08-11
> **andyjl said:**
> I am trying to install xubuntu-7.04-desktop-i386 and am having loads of probs. i keep getting "the ext3 file system creation in partition 1 of IDE1 master (hda) failed"  i have tried doing this manual and guided and it still comes up with same error.I have also switched hard drive in case it was bad. i'm just about to give up linux, if i cant even get through a bloody install

Hi you might check and see i the the drive you are installing on is mounted. I the live cd has that drive mounted you will receive that error. If the drive is mounted it will be on your desktop and you can right click on it and unmount it also in places, home you can unmount there with the same. Hope this helps, :)

---

### Post by Pragmatist on 2007-08-11
Is this a dual-boot (i.e. do you also have windows on this hard drive)?

I see you are frustrated.  Please realize that Linux is not for everybody, and perhaps giving up is the right decision for you.  If you do not want to give up, however, and you are willing to have patience and spend some time to get things working, then I am happy to volunteer and help you.

---

### Post by andyjl on 2007-08-11
as far as the partitions i just tried use entire disk and have also unmounted the drive on the desktop as it said it was being used by some other source  i am using a seagate 80gb ide can u give me an idea how i can set this up manually because another error i got was u havnt defined the root

---

### Post by andyjl on 2007-08-11
> **Pragmatist said:**
> Is this a dual-boot (i.e. do you also have windows on this hard drive)?

I see you are frustrated.  Please realize that Linux is not for everybody, and perhaps giving up is the right decision for you.  If you do not want to give up, however, and you are willing to have patience and spend some time to get things working, then I am happy to volunteer and help you.

no it not dual boot i am just trying to have a dedicated box right now

---

### Post by Pragmatist on 2007-08-11
> **andyjl said:**
> no it not dual boot i am just trying to have a dedicated box right now
Is it a second drive on the system, or are you using a LiveCD.  In other words, how are you presently working on the system?

---

### Post by andyjl on 2007-08-11
> **Pragmatist said:**
> Is it a second drive on the system, or are you using a LiveCD.  In other words, how are you presently working on the system?

no its the only drive and yes i am using a liveCD

---

### Post by Pragmatist on 2007-08-11
Do you remember your partitioning decisions?  
(edit: Nevermind this question: [COLOR=Silver][COLOR=Gray]Have you tried just doing a new install?[/COLOR])[/COLOR]

---

### Post by Pragmatist on 2007-08-11
> **andyjl said:**
> ....i keep getting "the ext3 file system creation in partition 1 of **IDE1** master (hda) failed"....
Why are you using IDE1 and not IDE0?  What is the output of this:
```
sudo fdisk /dev/hda
```
Then type 'p' (lowercase P)
cut-and-paste the output to your next post
Then type 'q' (lowercase Q)

---

### Post by ajgreeny on 2007-08-11
I recall reading about problems with the gparted version on the live CD so suggest you  make partitions before starting to install.  Try making an ext3 partition with gparted from the live CD first using the whole disk size less 2 x your ram size, ie if you have 512 MB ram make provision form 1GB of swap.  If that doesn't work get a copy of gparted liveCD, which is more up to date than the one on ubuntu liveCD, I think. It's worth having around in any case, and is only a 30 MB download.

So now you will have an ext3 partition of 79 GB and an unallocated 1GB, and it's here that you make a swap partition.

Now go to installation, and when you get to partitioning, use manual and put root (/) on the 79 GB and swap on the 1 GB.  The figures I show here will not be exact as ubuntu will show your disks to be smaller than they are shown on their labels.

Good luck, and if it doesn't work , get back again.

---

### Post by andyjl on 2007-08-11
> **ajgreeny said:**
> I recall reading about problems with the gparted version on the live CD so suggest you  make partitions before starting to install.  Try making an ext3 partition with gparted from the live CD first using the whole disk size less 2 x your ram size, ie if you have 512 MB ram make provision form 1GB of swap.  If that doesn't work get a copy of gparted liveCD, which is more up to date than the one on ubuntu liveCD, I think. It's worth having around in any case, and is only a 30 MB download.

So now you will have an ext3 partition of 79 GB and an unallocated 1GB, and it's here that you make a swap partition.

Now go to installation, and when you get to partitioning, use manual and put root (/) on the 79 GB and swap on the 1 GB.  The figures I show here will not be exact as ubuntu will show your disks to be smaller than they are shown on their labels.

Good luck, and if it doesn't work , get back again.

ok i did it manually as u suggested and it still came up as an error cant mount root its busy  (or something of that nature) but i noticed in the backround that the install was still proceeding so i left it and it completed. whooohooo!!!!  must be a flaw somewhere. thanks for all ur help

---

### Post by ajgreeny on 2007-08-11
Glad to be of help.  Did you use the **ubuntu gparted** in the end or get a copy of **gparted liveCD**?  If you used the ubuntu version, now is a good time to download and burn the dedicated version.

---

