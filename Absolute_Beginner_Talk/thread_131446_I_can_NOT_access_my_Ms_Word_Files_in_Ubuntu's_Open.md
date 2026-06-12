---
title: "I can NOT access my Ms Word Files in Ubuntu's Open Office Writer"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-16
Hello all !!!

I copied a Folder with Files & Subfolders from a Windows NTFS Partition to Ubuntu.

I changed the File Permissions from: "555" to "644", with the command (from root):

             chmod 644 *

Then I changed Ownership Rights from: "dimitris:dimitris" to  "dimitris:dimitris", just in case this created the problem, with the command:

            chown dimitris:dimitris *

When I try to open an MS Word File (coming from NTFS) to Ubuntu's Open Office Writer, I get the following Message:

                  Access to /blah/blah/blah/filename.doc was denied.

The only thing that Ubuntu's Open Office lets me press is the "OK" button.

Any ideas, what have I done wrong?

---

### Post by rsmereka on 2006-02-16
There is nothing special open OpenOffice's access to your files so I think firstly, we should take OpenOffice out of the picture. The issue you are having is one of permissions.

Can you tell me what userid you are using to access the files and also, in your reply, please supply an:
```
ls -l
```
of the directory where your former MS Office files are stored. Also, could I please see the output from:
```
df
```

---

### Post by aysiu on 2006-02-16
You can't change file permissions when it's mounted. You have to mount it with the proper permissions. See the fourth link of my signature for more details.

Keep in mind that even after you mount the NTFS partition properly, NTFS is read-only in Linux.

---

### Post by dvarsam on 2006-02-16
I do no NOT understand what you mean with: "what User Id you are using to access the files"

Sorry, I am a beginner - and it is the first time I've heard about a User Id.

Do you mean my User Name when I enter Ubuntu - User Name is: dimitris

The "ls -l" is the following:

root@ubuntu:/home/dimitris/Desktop/z_Forum_Questions# ls -l
total 560
-rw-r--r--  1 dimitris dimitris  83456 Jan 27 01:14 All Linux Programs.doc
-rw-r--r--  1 dimitris dimitris   4708 Feb  2 19:07 Canon i550 Printer - Drivers for Linux - E-mail to Canon.txt
-rw-r--r--  1 dimitris dimitris  24064 Jan 24 23:35 Difference Between Bin Folders.doc
-rw-r--r--  1 dimitris dimitris    301 Feb  2 23:04 Install DVD Shrink in Ubuntu.url
-rw-r--r--  1 dimitris dimitris  20992 Jan 24 23:14 Linux - Preferred Text Editors.doc
-rw-r--r--  1 dimitris dimitris  43008 Jan 24 23:03 Linux Pros & Cons.doc
-rw-r--r--  1 dimitris dimitris  52736 Feb  4 13:21 Ubuntu - Creating Partitions.doc
-rw-r--r--  1 dimitris dimitris  63488 Feb  4 15:07 Ubuntu - Installing Drivers.doc
-rw-r--r--  1 dimitris dimitris  29696 Feb  8 11:21 Ubuntu - Setup Internet Connection.doc
-rw-r--r--  1 dimitris dimitris  26112 Feb  4 03:38 Ubuntu - Will Windows Programs Work.doc
-rw-r--r--  1 dimitris dimitris 129536 Feb  4 05:00 Ubuntu Questions & Answers .doc
-rw-r--r--  1 dimitris dimitris  22016 Jan 24 23:27 Windows & Linux Together.doc
drw-r--r--  2 dimitris dimitris   4096 Feb 15 13:49 Windows .TTF Greek Fonts
-rw-r--r--  1 dimitris dimitris  24576 Feb  7 23:20 ?????????????? ???????????? ???????? Antivirus ?????? Linux.doc
root@ubuntu:/home/dimitris/Desktop/z_Forum_Questions#

The "df" is the following:

root@ubuntu:/home/dimitris/Desktop/z_Forum_Questions# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             19228276   2470304  15781224  14% /
tmpfs                   517436         0    517436   0% /dev/shm
tmpfs                   517436     12588    504848   3% /lib/modules/2.6.12-9-386/volatile
/dev/hdc1             39078080  14443004  24635076  37% /ntfs_files
/dev/sda5             31568320       128  31568192   1% /fat32_files
root@ubuntu:/home/dimitris/Desktop/z_Forum_Questions#

Thanks for your help.

---

### Post by aysiu on 2006-02-16
Forget the user id.
See the fourth link of my signature.

---

### Post by wrtrdood on 2006-02-16
You did good but you must also change the permissions on the directory (folder) you copied.

*e.g.*

drw-r--r-- 2 dimitris dimitris 4096 Feb 15 13:49 Windows .TTF Greek Fonts

*must be *

drwxr-xr-x 2 dimitris dimitris 4096 Feb 15 13:49 Windows .TTF Greek Fonts


Same thing for the parent folder for the files shown.  For example, the command for this directory would be:

chmod 755 "Windows .TTF Greek Fonts"

Directories must have the Execute bit set to be accessible.

---

### Post by dvarsam on 2006-02-16
I do Not know if you understood what I said.

I have ALREADY accessed the NTFS (Windows) Hard Drive, _copied_ the Files into the Ubuntu Partition & I can NOT open them from inside the Ubuntu Partition.

So, it is as if I am saying to Ubuntu, this:

"open the file which is lying inside the Ubuntu Partition"

What I do NOT understand is: why do I need to "mount" & "unmount" the Windows Partition, if I have already managed to copy the files into my Ubuntu Partition?

And right after the copy, I then performed the "chmod" & "chown" commands...

So, I do NOT see anything else I should do.

However, my "fstab" for the Windows Partition, is like this:

root@ubuntu:/home/dimitris/Desktop/z_Forum_Questions# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


# To see my FAT32 Partition (on the same SATA Hard Drive), type:

/dev/sda5       /fat32_files    vfat    iocharset=utf8,umask=000  0  0

# To see my NTFS Partition (on a diff IDE Hard Drive), type:

/dev/hdc1       /ntfs_files     ntfs    nls=utf8,umask=0222  0  0

root@ubuntu:/home/dimitris/Desktop/z_Forum_Questions# sudo mount -a
root@ubuntu:/home/dimitris/Desktop/z_Forum_Questions# 


I do NOT think that this matters, but between the "umask=0222" & the following two "0" there are two spaces in between.

Thanks for your help.

---

### Post by aysiu on 2006-02-16
[QUOTE=dvarsam]
I have ALREADY accessed the NTFS (Windows) Hard Drive, _copied_ the Files into the Ubuntu Partition & I can NOT open them from inside the Ubuntu Partition.

So, it is as if I am saying to Ubuntu, this:

"open the file which is lying inside the Ubuntu Partition"

And right after the copy, I then performed the "chmod" & "chown" commands...

So, I do NOT see anything else I should do.[/QUOTE] Sorry. I missed that. You're right. Careless reading on my part.

I still don't see why you need to know what your user id is, though.

What *chmod* and *chown* commands did you use? You need to stick an **-R** in there for it to work on all the folders' contents as well.

For example, if the files live in /home/dvarsam/windows_docs, then you'd need to ```
sudo chown -R dvarsam:dvarsam /home/dvarsam/windows_docs
``` to make you the owner of the files and then ```
sudo chmod -R 755 /home/dvarsam/windows_docs
``` to give you read/write/execute.

---

### Post by dvarsam on 2006-02-16
Hi, "aysiu", I did NOT notice that it was you who answered my Question.

It is nice to see you back!


It seems that AFTER I replaced "chmod -R 644" to "chmod -R 755". I was able to open the Ms Word Files in Open Office's Writer.


                        Before I had                           You said

Author:          Read & Write               Read, Write & Execute
Group:               Read                              Read & Execute
Others:              Read                              Read & Execute



But at the same time, I have some Questions to You:

1. Does the "chown" command **MUST** be given before the "chmod" command in the 
     "Terminal"?

2. At the same time I do NOT understand the following:
    Before deciding to use "644" I went, inside a Folder & checked (verified) a File's Permissions,
    (I am talking about a file created in Ubuntu - whick had it's Permissions set to "644"), and 
    therefore I know what Permissions to give (apply) to My Window coming files... (e.g. the 
    "644")....
    
    However, to be able to OPEN a Windows created File, the File Permissions MUST be set to
    "755". Why is there such a Difference?

    IT IS as if we are "discriminating" Window's coming Files.....

    .... of course, I know WE ARE SUPERIOR to Windows, but I really wonder why does this 
         happen....

   Is there something wrong to my System?

---

### Post by polpak on 2006-02-16
This should help you greatly.

[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

---

### Post by dvarsam on 2006-02-16
[QUOTE=polpak]This should help you greatly.

[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)[/QUOTE]

Dear "polpak",

                          thank you for your Help.

I went to the place you specified, but I did NOT find the ANSWERS to my questions.

My questions were specific & the page you suggested DID not even talk about them...

Does anybody know the answers to my questions?

Thanks.

---

