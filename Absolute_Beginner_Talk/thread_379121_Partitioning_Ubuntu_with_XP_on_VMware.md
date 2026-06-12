---
title: "Partitioning Ubuntu with XP on VMware"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-03-08
Hi guys,

I'm currently using Ubuntu AMD64, I'm thinking of formatting and installing Ubuntu i386 sometime soon, and I was hoping for some advice on partitioning my new hard disk :)

I currently have a partition for Ubuntu(It was automatic, so I'm not too familiar of the details), a 5gb fat32(for shifting files between windows and Linux), and another 30gb or so as NTFS(for windows system files). (its an 80gb hard disk)

And on a separate physical hard disk, 200gb of NTFS for pure data.

The scenario:
I was thinking of using Ubuntu as a main system, and running XP from VMware, then I wouldn't have to reboot into XP when I need to do something there(cause I haven't 100% moved to Ubuntu yet...its in the process ;) ). I want to be able to share files between the 2 systems as well.

As far as I've been told, I should try putting /home on a separate partition(so its easier when I format).

I was thinking of partitioning the 80gb hard disk to (swap/root/ext3 and whatever linux needs)
putting /home on the 200gb, and putting the xp VMware thingy as a file(its like a file right?) in my home folder(probably somewhere like /home/virtualmachines).

Is this advisible? If not, would there be a better solution?

Aside from that, how would I share files between the 2 operating systems? I know there's something I can install to give XP read/write to ext3 file system, so I could install that, and let the xp virtual machine have read/write access to my /home folder?

Any suggestions/comments would be welcome :)

Cheers,
Kinson.

PS: I'll probably install 6.06 cause its "LTS", and I bought a book([SAMS Ubuntu Unleashed]("http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093")) based on 6.06. But I might give Feisty a test when it comes out(it seems really interesting :) ).

---

### Post by ziggykg on 2007-03-08
If you simply want to share files between Ubuntu and an XP vmware install, simple use Samba! :) 

Ok, here's what to do:

Share one of you're folders in Ubuntu.  In the Administration section, select "Share folders" and follow the prompts.  Select a workgroup name (for your domain).  BTW, this is the Samba bit.

Then create and install XP in vmware.  During the XP installation (or even after), set the workgroup name to the same one you set in Ubuntu when sharing folders.

You should then be able to mount your Ubuntu shared folder in XP!

Some notes: to make file transfer faster have a look at [this]("http://www.ubuntuforums.org/showthread.php?t=342320&highlight=slow+samba")  post here on configuring your Samba config file.

Also using NAT in your VMWare network options seems to help too.

---

### Post by Bachstelze on 2007-03-08
About your partitons setup, I assume your 200 GiB drive is formatted as FAT32. If so, it's a very bad idea to use it as /home. If you want to use it as /home, you'll need to format it in a more performant filesystem (ext3, reiserfs, XFS, whatever) or if you want to keep it as it is, your best bet is to create the /home partition on your primary drive and use the second one as you currently do.

---

### Post by kinson on 2007-03-08
> **HymnToLife said:**
> About your partitons setup, I assume your 200 GiB drive is formatted as FAT32. If so, it's a very bad idea to use it as /home. If you want to use it as /home, you'll need to format it in a more performant filesystem (ext3, reiserfs, XFS, whatever) or if you want to keep it as it is, your best bet is to create the /home partition on your primary drive and use the second one as you currently do.

I was actually planning to format the 200GB as a ext3 partition, since Windows XP can be setup to read/write to ext3 file systems.

Thanks :)

---

### Post by haelters on 2007-03-08
In my opinion, it is possible to have the 200GB partition mounted in Linux as /home and have VMWare use that physical disk as a virtual drive for Windows XP. However, you should NEVER do this: this means that you would open the EXT3 file system twice.

I think the best way to go is using samba shares.

---

### Post by Bachstelze on 2007-03-08
Yep, if you use a physical partition in VMware, you should know *exactly* what you are doing. Otherwise, it's asking for major trouble.

---

### Post by kinson on 2007-03-08
I'm a little confused here. I'm not too familiar with the whole process to be honest.

In windows, I tried microsoft's virtual pc before. It had a config type file, and a hard disk like file(I'm assuming this would be the virtual machine's disk). So in this case, if I use VMware, it would be more or less the same scenario? But from Ubuntu I wouldn't be able to access the files that are on the "XP Disk"?

but what I should NOT do is, install XP(on VMware), and then access one of the mounted disks in Ubuntu?

So the suggested way would be to setup Ubuntu(as normal), I can setup the XP virtual machine in my 200gb hard disk. But they will have to communicate through SAMBA? So I kinda have to setup networking?(though it shouldn't be hard)

Btw, on a side note, how would I access files on the windows pc? I remember I tried it before last time in nautilus, I typed something like "smb://<workgroup>" into the location bar...I forgot what, and when I search for it, I find some really complicated steps :P

Cheers,
Kinson

---

### Post by haelters on 2007-03-08
> **kinson said:**
>  But from Ubuntu I wouldn't be able to access the files that are on the "XP Disk"?

Yes, this is why you need Samba access to the XP virtual machine

> **kinson said:**
> 
Btw, on a side note, how would I access files on the windows pc? I remember I tried it before last time in nautilus, I typed something like "smb://<workgroup>" into the location bar...I forgot what, and when I search for it, I find some really complicated steps :P


This is the general format:
smb://[[[authdomain;]user@]host[:port][/share[/path][/name]]][?context]

so smb://mycomputer/share should be good...

Hope it helps !

---

### Post by kinson on 2007-03-08
> **haelters said:**
> Yes, this is why you need Samba access to the XP virtual machine

K, I understand this. But the downside would be that in order to access my XP stuff, I'll need to boot up the virtual machine. Not that its a big issue, I'm just running through the use cases in my mind :) On the other hand, my plan was to just use the xp as a system, and let it access files on my ext3 hard disk.



> 

This is the general format:
smb://[[[authdomain;]user@]host[:port][/share[/path][/name]]][?context]

so smb://mycomputer/share should be good...

Hope it helps !

Thanks a billion  :) I'll give this a try tonight :) (The samba. I'll only format my pc near the end of the month :( )

---

