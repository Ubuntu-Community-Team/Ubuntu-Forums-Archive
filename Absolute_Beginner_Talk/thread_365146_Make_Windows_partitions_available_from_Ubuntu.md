---
title: "Make Windows partitions available from Ubuntu"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by david walsh on 2007-02-19
I've been checking out some linux live cd's over the last week, and have eventually settled with ubuntu. Until the day comes that I can run adobe premiere 2 and after effects 7 pro I'm stuck with dual boot and windows xp has to sadly remain on my computer.

It seems from reading around forums I'm far from the only one in this position.

I am yet another who is brand new to linux, and am going to spend time learning all the harder stuff while waiting for the inevitable day that I can change over completely.

There is one thing that I need to get straight away, I have restricted axcess to the partition of the drive that xp is installed on and my other hard drive.

I found at [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html) this:

Windows partitions should be automatically available from any Ubuntu system. If they are not, you can make them available using the Disks Manager.

   1.Open System->Administration->Disks .
   2.Select the correct hard disk, and click Partitions.
   3. Select the relevant partition, and click Enable.
   4. To unmount the partition, click Disable.

When I go to System->Administration there is then no option for disks. Am I looking in the right place for what I want to do? If so how do I get this option?

Hopefully,

David.

---

### Post by aberry5555 on 2007-02-19
In order for you to see your windows hard-drive you have to "mount" it in a folder, ie it will be shown as a folder somewhere in /. In order to mount first post back the result of 

```
fdisk -l
```

and also tell me which part of the output is your windows drive. Basically the command works like this:

```
sudo mount /dev/hda1 /media/windows
```

Firstly "sudo" allows you to run something as an administrator, which is needed for mounting disks, secondly you run the command "mount" which is a program that mounts a partition in to a specified folder. the next two parts describe **(a** which partition to mount and **(b** which folder to open the partition in.

One last thing, though, unless you install special software called ntfs-3g you will be able to read the disk but not write to it.

---

### Post by Sef on 2007-02-19
> One last thing, though, unless you install special software called ntfs-3g you will be able to read the disk but not write to it.

NTFS-3G is beta software, so make sure you have everything backed up if you are going to use it.   It may work fine, but there are no 100% guarantees.

---

### Post by MicheleZ on 2007-02-19
Hello David,

first of all I would like to make clear that I am also a newbie, so you'd better wait for some pros for a proper answer (I am sure I broke several rules with my "solution" :) ). Having said that, I just did what you want to do on my dual boot machine.

The access to ntfs formatted drives is by default read only. To gain write access you have to use an experimental package called ntfs-3g ([www.ntfs-3g.org)](www.ntfs-3g.org)). Remember that you will use it at your own risk then. 

Once you have your have it, you can unmount the windows partition
[PHP]sudo umount /dev/???[/PHP]
replace ??? with the ID of the windows partition (the name that appears on your desktop now (for me it was sda1 since I have a SATA HD).


and then mount it specifying as type ntfs-3g.
I have created a new directory under /mnt called driveC
[PHP]cd /mnt
sudo mkdir driveC[/PHP]
then
[PHP]sudo mount -t ntfs-3g /dev/??? /mnt/driveC[/PHP]

I have just learnt that you can also add these commands in a file called /etc/rc.local so that the instructions may be executed at time of bootup.


Cheers,

Michele

---

### Post by Michaelt74 on 2007-02-19
David

I'm faced with a similar scenario. Currently Ubuntu as default allows read only access to the ntfs (windows partition). There is an option to install write access software, as per this post:

[https://help.ubuntu.com/community/MountingWindowsPartitions#head-fb8716b5d667b443f5dda66c63dd39375260a9d9](https://help.ubuntu.com/community/MountingWindowsPartitions#head-fb8716b5d667b443f5dda66c63dd39375260a9d9)

I'm new to this too, but I couldn't make head or tail of the instructions.

Also try [www.psychocats.net](www.psychocats.net), there is some useful information about mounting Windows partitions.

There are software Windows emulators which allow some Windows software to run in Ubuntu, such as wine, cedega, crossover.

Michael

---

### Post by david walsh on 2007-02-19
Thanks for your quick help, and sorry, I should have been clearer. 

I can see the drives, I can access the files, I can even copy them to the Ubuntu desktop. I just can't delete files from them or add files from the Ubuntu desktop to them.

Does this sound normal, unusual or anything?

David.

---

### Post by david walsh on 2007-02-19
Wow, that last posts relates to the first reply, it was the only one there when I strated to post, I'll read through the others.

David.

---

### Post by aberry5555 on 2007-02-19
> **Sef said:**
> NTFS-3G is beta software, so make sure you have everything backed up if you are going to use it.   It may work fine, but there are no 100% guarantees.

True, it is Beta, I have had no problems though but, as Sef says, there are no guarantees. The best Idea would be for you to mount it in read-only mode and, if you have enough space somewhere on your disk, copy across the relevant items on to your linux disk or, alternatively, create a FAT32 partition to share files between windows and linux (although FAT32 is a bit of a dodgy file system, it still works). That way there are no third party programs that need to be installed either on windows or on Ubuntu.

---

### Post by Jussi01 on 2007-02-19
> **Sef said:**
> NTFS-3G is beta software, so make sure you have everything backed up if you are going to use it.   It may work fine, but there are no 100% guarantees.

Has Ntfs-3g not gone int to RC status??

---

### Post by dannyboy79 on 2007-02-19
> **Sef said:**
> NTFS-3G is beta software, so make sure you have everything backed up if you are going to use it.   It may work fine, but there are no 100% guarantees.'

NOT TRUE. It is out of Beta status and is in Release Canidate 1 as of 02/07/2007. See here [http://www.ntfs-3g.org/releases.html](http://www.ntfs-3g.org/releases.html).

---

### Post by hyper_ch on 2007-02-19
On the other way you could perfectly safe access the data on your ubuntu partitions in winodws :)
As ext2 is open source stable modules for Windows are developped :)

---

### Post by david walsh on 2007-02-19
Thanks everyone, I got it working, I'm not really sure how or why though.

I downloaded NTFS-3G, no problems. I then followed your instructions "MicheleZ" (it was the one I could follow easiest). I replaced the ??? with "New Volume" as it was the drive with no OS installations on it and seemed like less work to clean up if I went wrong.

Nothing would happen so I  replaced it with the partitioned drive with both installations "hda1" and it all went through fine. Then I could delete from the partition but not write to it.

I had stuff to do, left, came back and opened up again. Something you posted "MicheleZ"...

*I have just learnt that you can also add these commands in a file called /etc/rc.local so that the instructions may be executed at time of bootup.*

...made me think that perhaps I would have to repeat the actions again after rebooting, I must have got this wrong.

When I got back the first thing I done, before checking to see if the drive was in the same state, was to look at the NTFS 3G Configuration tool, I noticed the option "Enable write support for internal device" I ticked the box, then had a look. The partition with windows installed on it is almost fully accessible, I can't delete from the partition itself but I can from folders within.

The drive titled New Volume on the desktop is now fully accessible, this I never done anything to a tall.

Does anyone know what happened here, it all works fine, but I'm damned if I know how.

David.

---

### Post by MicheleZ on 2007-02-20
Hello David,

Clearly you have been much more clever than me. I did not even know there was a ntfs-3g configuration tool and this is why I used the terminal.

if you were to use the command line, then you would have had to re-do the umount and mount every time you logged in unless you placed these commands in this file called rc.local which (as I understand it) can be used to give additional instructions at boot up time.

Cheers,

MicheleZ

---

### Post by 999.michael on 2007-02-20
> **david walsh said:**
> Thanks for your quick help, and sorry, I should have been clearer. 

I can see the drives, I can access the files, I can even copy them to the Ubuntu desktop. I just can't delete files from them or add files from the Ubuntu desktop to them.

Does this sound normal, unusual or anything?

David.

I can't do this either as a normal user, but if I open Nautilus as root...

```
sudo nautilus
```

...then I can edit/add/delete files as well. The only problem is that I can't change permissions so I *have* to do this as root every time. I recommend creating a launcher on your desktop to mount the drive and open it as root in nautilus. I would go to my Ubuntu pc and give you the command I use now, but I'm installing xubuntu on it aswell and so can't at the moment.

Hope this helps :)

---

### Post by david walsh on 2007-02-20
I'm certainly not sure about being more clever, I just follwed the steps, then noticed the configuration tool in the system tools menu.

I'm just glad I can get it to do what i want it to now,

Thanks again,

David.

---

### Post by david walsh on 2007-02-25
This is weird, after messing around a lot and starting to get the hang of linux a bit more, I decided to reinstall to clean up all the mess I made in the progress.

This ntfs thing all works different now, the first time I searched the net for ntfs-3g and found a .deb that installed instantly and opened an ntfs configuration tool in the applications/system tools menu.

This time I couldn't find where i downloaded ntfs-3g from the first time, I searched synaptic and got it from there, there's no configuration tool this time. Does anyone know how i can get it back?

Could it be that the version I had first time was a more recent version, if so how can I update from the terminal?

David.

---

