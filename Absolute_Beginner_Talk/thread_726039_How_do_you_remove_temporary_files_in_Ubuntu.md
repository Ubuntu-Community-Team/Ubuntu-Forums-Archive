---
title: "How do you remove temporary files in Ubuntu"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2008-03-16
In Microsoft XP to removed temporary files, I did something like this:

Go to:
All programs 
Search
All files and folders
Then I typed in *.tmp and a list of all the computers temporary files would appear which could be deleted as required. 

How do I find and delete temporary files and folders in Ubuntu please?

---

### Post by ghost_ryder35 on 2008-03-16
apte-get clean
and there is a /tmp directory which can be cleaned as well :)

---

### Post by banewman on 2008-03-16
The /tmp folder is cleared at each boot as far as I know.
:)

---

### Post by ghost_ryder35 on 2008-03-16
> **banewman said:**
> The /tmp folder is cleared at each boot as far as I know.
:)

idk

---

### Post by VraiChevalier on 2008-03-16
I am wondering the same thing.
Recently I tried to make a backup copy of a DVD movie and it appeared that the copy was placed in a /tmp directory. The file was quite large (6.7G) and I got to wondering if Ubuntu or the ripping app would automatically clear the /tmp directory when the ripping and backing up was complete.

Does anyone know? Do I need to reboot to reclaim this disk space?

---

### Post by Ub1476 on 2008-03-16
As posted already, 

```
sudo apt-get clean

#and to remove unused dependencies:

sudo apt-get autoremove
```

Also, almost all configs files is stored in /home/user (ctrl+h to show hidden files). You might want to remove folders which store configs for apps you no longer have installed (not really necessary though).

---

### Post by handydan918 on 2008-03-16
> **VraiChevalier said:**
> I am wondering the same thing.
Recently I tried to make a backup copy of a DVD movie and it appeared that the copy was placed in a /tmp directory. The file was quite large (6.7G) and I got to wondering if Ubuntu or the ripping app would automatically clear the /tmp directory when the ripping and backing up was complete.

Does anyone know? Do I need to reboot to reclaim this disk space?

Rebooting will do it, but you can do it manually as well, without the reboot.

---

### Post by a.v.l on 2008-03-16
Thanks very much. Can I view there temporary folders before deleting them?

---

### Post by handydan918 on 2008-03-18
Sure, just like any other file...

---

