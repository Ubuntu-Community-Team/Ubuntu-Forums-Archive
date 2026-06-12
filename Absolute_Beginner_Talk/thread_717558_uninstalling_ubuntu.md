---
title: "uninstalling ubuntu"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by asakurax on 2008-03-07
So here is the thing:
I've got 3 partitions:
C: windows
D: my stuff
X:Ubuntu

Is there a way to uninstall Ubuntu without losing the data on the D partition?
Cause all the ways I've seen are like to install windows on the whole partition, and by doing that ill also delete my D partition...

Thanks

---

### Post by corney91 on 2008-03-07
You can't uninstall ubuntu, as such, but you can format the partition using gparted. You could then merge X: with another partition, again with gparted:
```
gksudo gparted
```

I'm not on Ubuntu atm so i couldn't tell you, from memory, which options to choose, but IIRC it's pretty self-explanatory - Of course, just ask if you have any queries:)

Just out of interest, any reason you want to get rid of it?:)

---

### Post by kpkeerthi on 2008-03-07
Use gparted live cd to erase ubuntu partition. This will produce unallocated free space. Format the free space (using the gparted) to ntfs or move D to the end and resize C to occupy rest of the free space. Finally use windows recovery CD to fix mbr and overwrite grub.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

EDIT: Oh.. btw.. be sure to backup before playing with your partitions.

---

### Post by criskat777 on 2008-03-07
If you are more comfortable in Windows use Partition Magic and do what he seed. delete X then use the space for what ever Partition you like. :)

---

### Post by HereInOz on 2008-03-07
If you use a partition editor and delete the Ubuntu partition, then combine it with the D: partition, that will get rid of Ubuntu. but it will leave you with Grub as a boot loader.

I am no Grub guru, so to speak, so I can't advise you how to get rid of it guaranteed, but what I would have a go at would be, when you have deleted the Ubuntu partition, insert your Windows CD and boot from it, and select the option to repair an installation using the Recovery Console,

Once in the recovery Console, run the utilities of Fixboot and Fixmbr.  I reckon that ought to overwrite the boot sector and the master boot record with the appropriate information to boot straight into Windows.  I have run those 2 utilities many times, for various reasons, but never to get rid of Grub, so I don't know if it actually will rid you of Grub, but it is worth a shot.

Hopefully a Grub guru will post on here a much easier and simpler way of getting rid of Grub and getting back to the Windows boot loader, but until then, this is all I can offer.

---

### Post by marckie on 2008-03-07
I am so wondering why on Earth would you uninstall Ubuntu? :confused: 	:confused:

---

### Post by asakurax on 2008-03-07
Umm, come to think of it, the more easy solution to my problem would be to make my two Ubuntus systems "shareable"(lol)
Umm, I'm a bit confused on how to do it
is there a "Howto" for sharing folders between two ubuntu systems?

---

### Post by asakurax on 2008-03-08
Bump :)

---

### Post by thisiam on 2008-03-08
> **asakurax said:**
> Umm, come to think of it, the more easy solution to my problem would be to make my two Ubuntus systems "shareable"(lol)
Umm, I'm a bit confused on how to do it
is there a "Howto" for sharing folders between two ubuntu systems?

Samba i would think.
well samba is so you can see windows but you should be able to go to places and network and see your other ubuntu computer.

---

### Post by ugm6hr on 2008-03-08
I agree, SMB (Samba) is probably the easiest way to do it (in System-> Administration-> Shared Folders).

NFS should also achieve what you are asking: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) [http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

### Post by PeterJS on 2008-03-08
Depends how you want to go about setting up the sharing, if you just want to get your data from machine A to B, right now, with minimal hassle you probably want to use sftp/ssh. If you want to set up a more permanent share that is Ubuntu only you could use NFS. If you want to set up a more permanent share that is accessible from Windows, you'll want to use SMB.

I've never used SMB or NFS and personally advocate using sftp because there's pretty much no setup involved beyond installing sshd, and if you want a more permanent share you can add sshfs on top of that, but the gnome vfs tools and bookmarks cover all you'd need for moving data around.

On the machine you expect to by physically sitting in front of less often, you'll want to install openssh-server, and it's all good to go. On the other machine go to Places > Connect to Server, select ssh as your service type, the default port is 22, and the rest should be self explanatory. After you connect the share will show up on your desktop, and off you go.

---

### Post by asakurax on 2008-03-08
Thanks every1
I've managed to make a shared folder using 
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

Too bad though that i didn't managed to share an NTFS folder...
So I'm doing some partitions changes now using gparted Live CD

Thanks again :)

---

### Post by quinnten83 on 2008-03-08
> **asakurax said:**
> Thanks every1
I've managed to make a shared folder using 
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

Too bad though that i didn't managed to share an NTFS folder...
So I'm doing some partitions changes now using gparted Live CD

Thanks again :)


[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)
[http://www.youtube.com/watch?v=AwBhkL5jRsw](http://www.youtube.com/watch?v=AwBhkL5jRsw)

youtube videos explaining how to share folders between windows & ubuntu.
no need really to partition, me thinks.

---

