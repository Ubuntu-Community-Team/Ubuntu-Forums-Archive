---
title: "Recover windows HDD that wont boot."
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Badmagic on 2007-02-09
Hello,

Sorry to ask a strange question but I am running Ubuntu 6.10 from a CD at the moment and its taking along time to do anything.

A friend using her home PC for accounts just had a major problem with the local hard disc, it wont boot at all, on trying to remedy the situation I suggested using this  Ubuntu disc to at least try to find out if the disc could be accessed in any way.

Unfortunately I don't have a clue what I am doing in this O/S so any help someone could offer would be greatly appreciated, I have been browsing the "Places" area on the system but as I am unfamiliar with the terminology of Ubuntu I could really use some assistance with this.

As I say this is a fairly large problem and with it being Friday time is a factor.

Thanks for your time in reading.

---

### Post by indytim on 2007-02-09
The first question is, are you able to boot the friend's pc from the Ubuntu disc?  If so, this would pretty much rule out a H/W problem.

IndyTim

---

### Post by Badmagic on 2007-02-09
Yes sorry, I should have specified, I am running the Ubuntu disc from her system as I write this.

I dont have access to a secondary system at the moment, all her work accounts are on this system, she did keep backups on an extarnal USB drive but when the system crashed it was running a backup and the external disc is missing all the data from the start of this year.

Under Places/Computer the areas listed are Floppy, CD-RW & Filesystem but in browsing the Filesystem would appear to be the Ubuntu CD.

---

### Post by louieb on 2007-02-09
The Ubuntu live CD does not offer a point and click way to view the hard drives content.
But if thats all you have then see this   [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If you can get your hands on a Puppy or Knoppix live CD it is much easier to view the hard drives content.

When Puppy boots up you will see a icon labeled drives single click on it. A list of the partitions on the hard drive will come up. 
Click on "mount" and the file manager will open showing the content of the drive.
At least you will know if the drive is ok and you can  go from there to get  then copied off.  

In Knoppix the  hard drives partitions show up  as icons on the desktop.

---

### Post by MiCovran on 2007-02-09
Go to Applications -> Accessories -> Terminal and write:
```
sudo fdisk -l
```
Here you should see all hard drives and partitions on them. They aren't labeled C: or D: like in windows, you'll see something like hda1, hda2... or sda1, sda2... Now if you want to access hda1, you should do (replace NAME with how you want to call your partition in ubuntu):
```
mkdir /mnt/NAME
sudo mount /dev/hda1 /mnt/NAME
gksudo nautilus /mnt/NAME
```
'mkdir' makes a new directory called NAME
'mount' gives access to your partition and puts it in the /mnt/NAME directory
'nautilus' is a GUI file manager

If something is unclear, feel free to ask.

---

### Post by xpod on 2007-02-09
Always good to see a fellow jock....even if he is fae Glesga:lolflag: 
I`d settle for Glasgow myself right now mind you:) 

Anyway m8...the live cd will run a bit slower than an actual installation of Ubuntu as your running a complete OS from the ram so the less you have the slower it`s going to run i`m afraid(if at all).

IF you navigate to System>administration>gnome partition editor(gparted) you`ll  be able to see if the actual hardrive still at least contains the data ok if i remember correctly.The volume should also be visible under "Places>computer"  as "40g volume" or whatever size the disk in question is.

What type of install are you trying to access btw???
You will need to actually mount any volume you want to access but the above will at least show you if it exists ok.

These guy`s will keep you right soo much better than i can m8:)

---

### Post by Badmagic on 2007-02-09
Thanks for the responses everyone, to confirm I started following your post MiCorvan, here is where I have got too.

[INDENT]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS
ubuntu@ubuntu:~$ mkdir /mnt/HDD1
mkdir: cannot create directory `/mnt/HDD1': Permission denied
ubuntu@ubuntu:~$ [/INDENT]

:confused:

---

### Post by xpod on 2007-02-09
You need to put "sudo" before the "mkdir /mnt/HDD1"  command i think.

"sudo" will give you permission you need to do anything outside your home directory 

Then
```
sudo mount /dev/hda1 /mnt/HDD1
```
and then to navigate to your newly mounted Windows
```
gksudo nautilus /mnt/HDD1
```

Good luck

---

### Post by MiCovran on 2007-02-09
> You need to put "sudo" before the "mkdir /mnt/HDD1" command i think.
That's right, i forgot to put 'sudo' there. Sorry.

---

### Post by Badmagic on 2007-02-09
Thanks everyone for your help, sorry I did not respond sooner but I just got back, I ended up just bringing her HD home and installing it as a logical drive, I grabbed her data put it on a dvd then when I went back to her house did a fresh install, its working now but I still don&#8217;t like not knowing how it happened in the first place, I have talked her into using a secondary backup just in case it happens again.

On a side note, I have wanted to try out Ubuntu for quite some time but I never got it to install for me, with all the talk of Vista recently and looking at this latest burn it seems to be working fine so far, just past the partitioning stage and onto the installing system section (61%) with any luck I am now able to use the software from my own home PC.

No doubt I will be back with more odd questions in the near future, although I will try to refrain from asking how to get world of warcraft working.  ;)

***EDIT***

I was going to mark the thread as solved but I am not seeing a function like that, just thought I should mention it.

*END*EDIT*

---

