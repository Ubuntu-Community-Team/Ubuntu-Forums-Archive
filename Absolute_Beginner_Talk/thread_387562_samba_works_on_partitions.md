---
title: "samba works on partitions?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Morkhaar on 2007-03-18
ok, so i decided to switch to ubuntu but I still need  a windows partition for certain applications until I set up a virtual platform, possibly on a new release of ubuntu or a new laptop, or until I find sufficient alternatives  (common situation)

I've installed the ubuntu 6.06  and mounted the drives from the windows partition so that I can browse my files and folders. I am able to copy files from the directories, but     I cannot paste anything, not even to my external hdd (naturally since it is a windows formatted volume)    
I'm looking for a way to access and copy paste files from one partition to the other, both from ubuntu and windows.
I've searched the forums and done some googleing, but I can't seem to be able to find what i'm looking for. (common problem)
I suppose the answer is **samba** but up to now all I've seen posted has to do with a network of both linux/ windows PC's. Does it work also with partitions? 

I'm sorry if this is a 'more than absolute beginner' issue, if the answer already exists in these forums (..of which I have no doubt!), please give me the link!

---

### Post by Bachstelze on 2007-03-18
Short answer : No

Long answer : Samba is a network protocol,meaning that it needs a server and a client machine. Using Samba on a partition makes no sense.


Is your partition formatted in FAT32 ? If sou, Linux can very well write to it, you just need to set your permissions correctly.

---

### Post by benerivo on 2007-03-18
The answer is not samba, but is instead making changes to your fstab file (/etc/fstab). This is where permissions are set for mounting, read-write access, and some other controls regarding drives and file permissions. Search for fstab in the forums. There is not a single universal fstab setting that works on all machines, as the changes you will need to make depend on how you have your machine set up, but you will find your answer as the question is very common. Linux will be able to write to your windows partition even if it is in ntfs format, but you may need to install the ntfs-3g package.

---

### Post by Morkhaar on 2007-03-18
thanks a lot, i'll look it up! Common problems have simple solutions if you know what to look for! :)

---

