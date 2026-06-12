---
title: "How do I log in as root to change the permissions on /media/disk?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by krazejpo on 2007-05-08
How do i log in as root so that i can change the permissions on /media/disk.  its also NTFS. PLEASE HELP!

---

### Post by justleen on 2007-05-08
you should read the answers in your first post..

If its an NTFS drive, you will need the NTFS-3g drivers installed. Default, you cannot write to NTFS partitions, even if the permissions are set correctly

---

### Post by mcduck on 2007-05-08
Short answer: you don't.

The long one is that writing to NTFS is not natively supported in Linux, as it's Microsoft's proprietary file system. There is software available that allows write support for NTFS, but even then you could not just change the permissions as NTFS doesn't support unix-style permissions.. Editing permissions of mounted drives is done by editing their settings in /etc/fstab.

And in any case, you never need to log in as root in Ubuntu. Read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If you still feel like enabling write support for your NTFS drive, somebody else (who is actually using it) will most likely help you soon :)

---

### Post by Tomosaur on 2007-05-08
You use the 'sudo' and/or 'gksudo' commands to temporarily gain root privileges, for example, if you want to edit the /etc/apt/sources.list file:

```

sudo nano /etc/apt/sources.list

```

You should use 'sudo' for command line apps, and 'gksudo' for GUI apps.

As for NTFS write support - I think Feisty has the NTFS-3g drivers installed by default, which means you should be able to write to NTFS (but you WILL need to use sudo or gksudo to do it).

The best option by far is to set up a new partition, formatted as a filesystem which both Linux and Windows can read/write to natively.

---

### Post by hyperair on 2007-05-08
The best is as Tomosaur said, which is to set up a FAT partition which both Linux and WIndows can write to effectively. At one point of time, NTFS writing support for Linux using the default NTFS drivers was very unstable. It still is. But now there's a new driver around, called ntfs-3g. It provides stable read and write support (so it claims) and so on. I have been using it for quite a while already, but while my Vist a partition seems to stay intact, there's no knowing if there are any bugs or not. After all, the ntfs-3g and ntfs drivers are manufactured from tons and tons of reverse engineering. NTFS is a proprietary file system created by Micrsooft, and they may, and most probably will update the way the file system is handled someday without prior notice. When this happens it can really throw the ntfs and ntfs-3g drivers off track (I reckon) and knowing Microsoft, they would most probably do it to spite Linux. For now however, ntfs-3g seems to work, and you can install and use them by the following instructions

1. Enable your universe repository if you haven't already done so (System->Administration->Software Sources and check the "Community maintained packages (universe)") 
2. Close the dialog box and allow it to refresh your repository.
3. Run this command in the terminal: ```
sudo apt-get install ntfs-3g ntfs-config && sudo ntfs-config
```
4. Check the "enable write support for internal device" and click Ok.
5. run ```
sudo mount -a
```

---

### Post by mcduck on 2007-05-08
> **Tomosaur said:**
> You use the 'sudo' and/or 'gksudo' commands to temporarily gain root privileges, for example, if you want to edit the /etc/apt/sources.list file:

```

sudo nano /etc/apt/sources.list

```

You should use 'sudo' for command line apps, and 'gksudo' for GUI apps.

As for NTFS write support - I think Feisty has the NTFS-3g drivers installed by default, which means you should be able to write to NTFS (but you WILL need to use sudo or gksudo to do it).

The best option by far is to set up a new partition, formatted as a filesystem which both Linux and Windows can read/write to natively.

No, it's not installed by default, as NTFS is proprietary file system. It's the same thing as with most media formats. But the driver is in Universe repository if you want to install it.

---

### Post by silent1643 on 2007-05-08
> **krazejpo said:**
> How do i log in as root so that i can change the permissions on /media/disk.  its also NTFS. PLEASE HELP!

this will make your file browser "root" capable - please read all the info first
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by krazejpo on 2007-05-08
I fixed the problem thanks to my friend Machinevirus, all I had to do is go to synaptic package manager, search for ntfs-config and install it. After that you look for it in Applications- System Tools- NTFS Configuration Tool and then enable write support for internal device. click ok. And now you can write and delete files on it! TRUST ME IT WORKS!!!! Create a folder in it and see for yourself!!!

---

### Post by hyperair on 2007-05-09
Yeah my post did explain how to install ntfs-3g and ntfs-config via the command line. Don't forget that you must enable your universe repository, or ntfs-config won't show up.

---

