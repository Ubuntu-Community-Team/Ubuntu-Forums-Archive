---
title: "Permission denied even with root access/password"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by dunomous on 2006-03-22
Hello, first timer *timid pose* to Ubuntu, just installed today. 

Anywho, enough of the n00b disclaimer. 

On install, I selected my 10 gig partition for root, as well as apparantly /home for my user account, along with making a seperate one gig swap. 

That being said, I tried accessing my files (sda6), and my windows files (sda1), even after I gained root. My processed attempt:

```

user@computername:~$ sudo su -
Password:
root@computername:~# cd /mnt
root@computername:/mnt# /dev/sda6 
-su: /dev/sda6: Permission denied

```

I don't have my Window's files mounted yet. But I imagine that will go the same. Thanks so much for the help Freunde!

---

### Post by Sef on 2006-03-22
> accessing ... my windows files (sda1)

To access your window files, you need an ext2 partition.  Both Linux and Windows can read that.

> user@computername:~$ sudo su -

Why do you need to access root to do this?   Root is very dangerous to be in.  It is best just to use sudo.

---

### Post by dunomous on 2006-03-22
[QUOTE=Sef]Why do you need to access root to do this?   Root is very dangerous to be in.  It is best just to use sudo.[/QUOTE]

When I accessed the drive from my desktop, it said I did not have permission to do so. I know no other way, or other logic, than to do so from root.

---

### Post by Ian Maxwell on 2006-03-22
Mounting a filesystem (such as /dev/sda6) is done with the mount command. Try the following:

```
mkdir /dosfiles
sudo mount /dev/sda6 /dosfiles
```

Then look in the directory /dosfiles, and you should see all your stuff. When you're done in there, type

```
sudo umount /dev/sda6
```

to unmount the fileystem.

---

### Post by dunomous on 2006-03-22
alright, so I've now accessed my windows files where it was mounted (media/sda1) giving me

```

root@computername:/media/sda1#

```

do I now browse for my things like dos?

---

### Post by towsonu2003 on 2006-03-22
ok, a couple of things... 
1. Instead of su, use sudo (unless you know about the sudo thing in ubuntu). See here: wiki.ubuntu.com/RootSudo

2. You have to mount the partition before accessing it. 

3. To automatically mount a fat32 / ntfs partition on reboot, use the below examples to add lines to your /etc/fstab
```

/dev/hda7       /**fat32**          vfat    defaults        0       0
/dev/hda1       /**ntfs**       ntfs    auto,user,ro,nls=utf8,umask=0222        0       0

```
You can use /media/blabla or /mnt/blabla instead of bolded text above, but make sure you create those directories (sudo mkdir /mnt/blabla or similar). Use /dev/sda6 (or /dev/sda1, depends on file system etc) instead of /dev/hda1|7

4. Once you add those lines to /etc/fstab (sudo gedit /etc/fstab); mount the partitions with sudo mount /bla/blabla (text in bold above).

5. ntfs filesystem is not writable in ubuntu. you can only see/copy stuff from it, nothing more... write access to ntfs is currently in testing and thus dangerous (regardless of linux distro you use)

---

### Post by dunomous on 2006-03-22
[QUOTE=towsonu2003]5. ntfs filesystem is not writable in ubuntu. you can only see/copy stuff from it, nothing more... write access to ntfs is currently in testing and thus dangerous (regardless of linux distro you use)[/QUOTE]

Quite understood. All I desire to do is read/copy my files only. Thus only desiring to be able to browse around my files and nab them for here.

---

### Post by Ian Maxwell on 2006-03-22
In answering your question, dunomous, I'll also throw in a bit of terminology.

The hard disk partition containing your windows files is represented in linux as (in your case) /dev/sda1. This "file" is called a *device node* or *device file*. In order to access the data stored thereon, we must *mount* it somewhere.

First, create a folder where you want to mount it. This folder is called a *mount point.*

```
mkdir /windows
```

Then, use the mount command:

```
sudo mount /dev/sda1 /windows
```

Now go tell someone, "I've just mounted the device /dev/sda1 at /windows," because you have. Then go look in that directory for your stuff.

towsonu2003 offers good advice: by adding a few lines to the file /etc/fstab, you can get the computer to automagically mount these two devices every time you start the computer.

---

### Post by dunomous on 2006-03-22
alright, thanks so much fellas

Again, I know my /dev/sda1 is mounted in /media/sda1.

So how to access them?

---

### Post by Ian Maxwell on 2006-03-22
Just go to the directory like any other directory. Within Gnome, click on "Places -> Computer", then open "Filesystem", then "media", then "sda1". Or, within the terminal window, type

```
cd /media/sda1
```

---

### Post by dunomous on 2006-03-22
Which is where we meet my problem. It says You do not have the permissions necessary to view the contents of "sda1". Perhaps I need make it so from windows?

---

### Post by Ian Maxwell on 2006-03-22
Does "sudo cd /media/sda1" work?

---

### Post by dunomous on 2006-03-22
says command not found

---

### Post by towsonu2003 on 2006-03-22
[QUOTE=dunomous]Which is where we meet my problem. It says You do not have the permissions necessary to view the contents of "sda1". Perhaps I need make it so from windows?[/QUOTE]
I'm a little lost (too many replies from too many people:PpPp). 

Totally edited:

Please attache /etc/fstab as a file here and cop/paste the output of ```
mount | sort
```

PS. There is nothing to do from windows. It's all about mounting it right in linux...

---

### Post by markiss on 2006-03-25
dunomous, on my ubuntu system after i've mounted my disks I found I can access them by: System--->adminstration---->disks

here I am able to pick the disk i want to enable or disable, then browse.

markiss

---

### Post by dunomous on 2006-03-25
Ah! Very excellent. My new problem is my access to my windows drive is only accessible through root. I've been told that accessing files like this is bad practice. I attempted to give access to my windows files using chown. However, when checking the values, basically seeing if my user had access, instead of saying 'user' it had root. I'll try to check exactly what I'm talking about. But the fact remains the same, that I have problems such as viewing video files and all since all this accessing is via root, instead of user. 

In addition, all of your help has been quite helpful.

---

### Post by towsonu2003 on 2006-03-25
[QUOTE=dunomous]Ah! Very excellent. My new problem is my access to my windows drive is only accessible through root. I've been told that accessing files like this is bad practice. I attempted to give access to my windows files using chown. However, when checking the values, basically seeing if my user had access, instead of saying 'user' it had root. I'll try to check exactly what I'm talking about. But the fact remains the same, that I have problems such as viewing video files and all since all this accessing is via root, instead of user. 
[/QUOTE]
Change your /etc/fstab file to make it look like the following (which is MY fstab, so you'll need to change it to your needs):
```

*/dev/hda2       /mnt/ntfs*       ntfs    **user,ro,nls=utf8,umask=0222**   0       0
```I bolded the useful stuff and italicised the stuff you need to change to your needs.  
to edit the file, do:```

sudo cp /etc/fstab /etc/fstab.backup01
sudo gedit /etc/fstab

```
first one does the backup, second one opens the file in gedit (gnome's notepad).

---

