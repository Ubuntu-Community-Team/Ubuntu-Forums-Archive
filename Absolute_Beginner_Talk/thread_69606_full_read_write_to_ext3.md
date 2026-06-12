---
title: "full read write to ext3"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by c2483 on 2005-09-27
i know how to edit te fstab file somewhat and give myself full read/write access to a vfat file system but how can I do that with ext3?

---

### Post by Valder on 2005-09-27
Isn't ext3 the native filesystem for Linux? Is there indeed any need for editing something?:confused:

---

### Post by Wolki on 2005-09-27
[QUOTE=c2483]i know how to edit te fstab file somewhat and give myself full read/write access to a vfat file system but how can I do that with ext3?[/QUOTE]


You mean, you've mounted it and only root can read/write to it?

Try chmodding the directory you mount it into both before and after mounting... so if it's /mnt/data/, do

sudo umount /mnt/data
sudo chmod a+rw /mnt/data
sudo mount /mnt/data
sudo chmod -R a+rw /mnt/data

this should give read/write access to everyone. If you want it only for yourself, chown them to yourself and replace a+rw above with u+rw.

---

### Post by c2483 on 2005-09-27
i have several hard drives in my computer besides the one where linux is installed.
i converted one of these to ext3 but now cannot write to it unless i'm root.

---

### Post by mlomker on 2005-09-27
> i converted one of these to ext3 but now cannot write to it unless i'm root.

You just need to add a proper fstab entry.  [Look here.]("http://ubuntuforums.org/showpost.php?p=355988&postcount=8")

---

### Post by c2483 on 2005-09-27
i made those changes but write still does not work

my drive is hdb1 and is ext3 
my fstab line is /dev/hdb1       /media/hdb1     ext3    defaults,users   0   2
i went to the terminal and typed
sudo umount /media/hdb1
sudo mount /media/hdb1

then i double click the icon on my desktop but i cannot even create a folder

---

### Post by c2483 on 2005-09-27
is there any way?

---

### Post by mlomker on 2005-09-27
What is the output of **mount** after it is mounted?

---

### Post by c2483 on 2005-09-27
ok, i solved it
thanks

---

