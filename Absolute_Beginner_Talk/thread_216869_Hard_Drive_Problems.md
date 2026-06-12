---
title: "Hard Drive Problems"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by oasis13 on 2006-07-16
Hi,
I installed Linux on a dual boot yesterday, and am having some problems.

I have 3 hard drives. My first hard drive is split into two partitions, Windows and Linux, my second hardive is all my documents, and my third harddrive is my media.

My media harddrive mounted fine, but when i try to open my documentss harddrive i get an error saying i do not have permission to open the folder!

I only have one account on my linux install and that has administrative priveleges!

Any help?

PS - i mounted the documents harddrive by going to system>administration>disks. The media harddrive mounted automatically when i turned the computer on.

---

### Post by Kurt` on 2006-07-16
> **oasis13 said:**
> I only have one account on my linux install and that has administrative priveleges!
Just for clarification, the account you created in the Ubuntu installer can run administrative commands (via sudo), but it is not technically an administrator account.

I am not too familiar with manipulating/mounting disks via the GUI, so I am afraid that I cannot help you. :(

---

### Post by oasis13 on 2006-07-16
im sorry, but i dont really know what you mean? :p

What would be an administrator account?

I tried mounting it through the terminal aslo and the same thing happened.

---

### Post by Denis on 2006-07-16
Take a look at the permissions of that directory you're trying to access. Right click on it, chose Properties and go to the Permissiosn tab. 

Who is the owner? What read, write and execute permissions are checked? 

I assume the hard drive with your documents has a Linux filesystem (like ext3) and not a Windows filesystem (like NTFS or FAT32). Is that right?

---

### Post by oasis13 on 2006-07-16
No, the documents HD is NTFS. Currently, i only need to be able to read them. If i use linux more, i will make it ext3.

---

### Post by Denis on 2006-07-16
In that case it is best to mount this hard drive using these instructions: 
[ How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

Instead of mounting at /media/windows, you can chose whatever location you want.

The device name of your documents partition will probably be /dev/hdb1 (you can also see this in the Disks utility.)

---

### Post by oasis13 on 2006-07-16
Ok, i tried that, and when i opened the folder there were no files in it ](*,) 

Also, when i then went to system>admin>disks it displayed the harddrive i want to make availabe twice!

---

### Post by Kurt` on 2006-07-16
> **oasis13 said:**
> im sorry, but i dont really know what you mean? :p

What would be an administrator account?
Typically on a Linux system, there is the 'root' account (the *only* adminstrator), and regular user accounts. Only root can make changes to the system (installing/removing programs, modifying certain files).

The 'sudo' command allows you to run a command as the root user (su = superuser, sudo = superdo *do*).

As for your problem:

The folder being empty indicates a permission problem, check again what Denis said in his first post.

---

### Post by moshuptrail on 2006-07-16
from one beginner to another:
1) I've read that very bad things can happen if you try to update files on NTFS filesystems from linux.  Perhaps NTFS is only partially supported - maybe someone more knowledgable can comment?
2) It may be easiest to re-install linux and simply assign your NTFS drive as /dev/hdxx in the install process.  it will be mounted as a readonly filesystem.  I've got something similar and linux will not give me write access.  It sounds like that's what happened to you at first and you couldn't understand why, so you tried to change it.  It might be lucky that you were unsuccessful!

If you really want a shared filesystem, you might try FAT32.  That would require backing up that entire partition first and then re-formatting it.

---

### Post by moshuptrail on 2006-07-16
go to the wiki and enter NTFS and search for titles
there is one on manually mounting NTFS filesystems (readonly) and another on the issues of mounting with write access and a possible (but not necessarily stable) solution.

---

