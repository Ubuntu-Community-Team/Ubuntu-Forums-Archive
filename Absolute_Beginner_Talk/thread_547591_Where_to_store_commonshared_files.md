---
title: "Where to store common/shared files?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-09-10
Hi Folks,

I'm in the process of migrating much of my personal data from XP to Ubuntu.  I've got a fairly high level grasp of the Linux file system, but am conceptually stumped at where to put some things.  In particular, my wife and I both have seperate Ubuntu accounts.  We also have a store of photos which we both want access to.  Where should these go?

Yes, I could put them in one or other's home directory and change the permissions, but it strikes me that this isn't really what I want since they would reside under a particular user, when what I want is for these files to be user/account independant.  I'm looking for something like /home/commonFiles or something, but would setting up such a directory confuse anyone or anything, since 'commonFiles' is not a user/account?

Any ideas most appreciated!

---

### Post by BrendanM on 2007-09-10
I have a fairly low-level grasp of the Linux file system, but it seems to be like you could just create a folder like /home/shared_files and set the permissions so you and your spouse could both read/write to it. You could even create a symlink from your own home directories to the shared ones.

Does anyone know if manually creating a directory under /home that isn't associated with a user would cause any problems?

---

### Post by tszanon on 2007-09-10
> **cknight said:**
> Hi Folks,

I'm in the process of migrating much of my personal data from XP to Ubuntu.  I've got a fairly high level grasp of the Linux file system, but am conceptually stumped at where to put some things.  In particular, my wife and I both have seperate Ubuntu accounts.  We also have a store of photos which we both want access to.  Where should these go?

Yes, I could put them in one or other's home directory and change the permissions, but it strikes me that this isn't really what I want since they would reside under a particular user, when what I want is for these files to be user/account independant.  I'm looking for something like /home/commonFiles or something, but would setting up such a directory confuse anyone or anything, since 'commonFiles' is not a user/account?

Any ideas most appreciated!
Unless you're willing to create an user called commonFiles, I don't think that anything would be harmed.
I'd go further and create a symbolic link under each user's home folder to /home/commonFiles. It will look like they have a folder inside their home folder that contains all common files.
If /home has it's own partition, then I'm against placing commonFiles outside it. If anything breaks, you can easily format the system partition, not worrying about your files.

---

### Post by matthewrdamon on 2007-09-10
when I need to share files, I create a dir under the root dir called /mnt.  Then I mount all my partitions there.  Then I link the folders that I use all the time into my home directory.  Also, I create a group, usally called "files", that I gives the users I want write read and execute privilages on these folders.  Even if you are only mounting one partition, I still think its the best to put the dirs in the /mnt dir and then link them into your home folder.  
If you make it in /home, I don't know of any specific problems that would cause, but it isn't organized like the linux file system should be.

---

### Post by tszanon on 2007-09-10
> **matthewrdamon said:**
> when I need to share files, I create a dir under the root dir called /mnt.  Then I mount all my partitions there.  Then I link the folders that I use all the time into my home directory.  Also, I create a group, usally called "files", that I gives the users I want write read and execute privilages on these folders.  Even if you are only mounting one partition, I still think its the best to put the dirs in the /mnt dir and then link them into your home folder.  
If you make it in /home, I don't know of any specific problems that would cause, but it isn't organized like the linux file system should be.
I agree when you say that placing it in /home isn't organized as it should be. You gave a better solution, thanks!

---

### Post by cknight on 2007-09-10
> **matthewrdamon said:**
> when I need to share files, I create a dir under the root dir called /mnt.  Then I mount all my partitions there.  Then I link the folders that I use all the time into my home directory.  Also, I create a group, usally called "files", that I gives the users I want write read and execute privilages on these folders.  Even if you are only mounting one partition, I still think its the best to put the dirs in the /mnt dir and then link them into your home folder.  
If you make it in /home, I don't know of any specific problems that would cause, but it isn't organized like the linux file system should be.

So what you're suggesting is to put the photos on their own partition which is then mounted to /mnt and subsequently symbolicly linked from /home/*username*?  Hmm, I think I like the design of having a seperate partition for these files.  Thanks for that.

---

### Post by hyper_ch on 2007-09-10
you could create a new group and add both yourself and your wife to it and then give the folder with the pic rwx group-accesss to it and the files in it.

---

### Post by AndyCooll on 2007-09-10
> **cknight said:**
> So what you're suggesting is to put the photos on their own partition which is then mounted to /mnt and subsequently symbolicly linked from /home/*username*?  Hmm, I think I like the design of having a seperate partition for these files.  Thanks for that.

This is roughly what I do except all our shares are actually stored on a separate server. 

However the theory still applies in that they are on a separate partition which is then mounted to the /mnt folder with symbolic links in the home folder. And a new group which we are both members of with read/write access. 

:cool:

---

### Post by cknight on 2007-09-10
> **hyper_ch said:**
> you could create a new group and add both yourself and your wife to it and then give the folder with the pic rwx group-accesss to it and the files in it.

Yep, I get the whole group/permissions thing.  The crux for me is where logically the folder should be located.  Home doesn't feel quite right since this folder seems user/account oriented and the other folders  (off of root '/') are all system oriented.

---

### Post by hyper_ch on 2007-09-10
I consider the /home folder as place to store personal files... so I'd create something like /home/share or /home/exchange where both users can rw-access it.

---

### Post by daveshields on 2007-09-10
While many folks suggest putting /home on a separate partition, I have found it more convenient to have a partition called /share. I use it to store all my original work. If I need to update Ubuntu or try another distro, than I can do a standard install and then mount /share. I can also do a backup by just
$ sudo tar cfz share.tgz /share
and ftp'ing  that file to another machine. 

I use ext3 for /share. If you want to share files with Windows you could create /wshare partition with FAT32 format.

---

### Post by hyper_ch on 2007-09-10
well, if you put /home on a seperate partition you will not only have your docs but also your config files for the various applications.

---

