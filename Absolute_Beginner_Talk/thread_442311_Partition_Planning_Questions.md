---
title: "Partition Planning Questions"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Marsonis on 2007-05-13
Hello everyone, 

I am going to install Ubuntu for the first time and I am planning my partitions.  I am considering using a this plan:

[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]

I'll use the /home partition to share files between Windows XP and Linux instead of having a Fat32 partition.

My first concern deals using the /home partition as the shared space by installing Ext2 IFS in Windows.  The FAQ page for IFS said that it does not protect access rights, so usernames and passwords, such as those contained in /etc/passwd and /etc/shadow, can be read and written to in Windows if the particular partition is mounted.  So, where would the /etc/ directory be located on the partition scheme above?  

Also, I read that my personal settings are stored in the /home area, so should I have a smaller /home (which would only store setting and not be mounted in Windows) and make an additional partition for shared space?  If so, what would it be called?

Where are Linux applications be installed?  Are they in /home or Ubuntu/ (which I assume is the same as /root).  Also, where would additional desktop flavors be stored?  I would like to be able to switch between Ubuntu, Kubuntu, and Xubuntu until I decide which one works best for me, so I need to make sure that I allocate plenty of space for them in advance.

Thank you for your help.

Marsonis

---

### Post by finer recliner on 2007-05-13
/etc/passwd and /etc/shadow would both be located in a subfolder in your / partition. 

despite the name, the passwd file has no passwords in it, only usernames and some properites about each user. the shadow file has all the users' passwords. and yes both files are in plain text, but the shadow file stores passwords encrypted. so they are not immediatly useful to a stranger viewing the file.

i personally dont think you need a "shared space" since ntfs-3g is out of beta you can read/write to an ntfs partition from ubuntu with almost no problems. windows has had support to read/write to ext3 for a while now. on my dual boot, i have just: [windows,ntfs][linux,ext3][linux,swap]

applications do not have a single folder like the "program files" folder in windows. they all go somewhere different depending on what they do and their use. they are not stored in /home though, those are just user preferences and personal files.

hope this helps

---

