---
title: "Removed vmware stole 20GB from my HDD"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by airfoil6205 on 2008-03-04
Hi All,
I removed vmware with Synaptic but the 20GB virtual HDD didn't turn up. I read in Hungarian Ubuntu Forum "I have to delete /var/lib/vmware-server/ library" I deleted it but 20GB still missing. What is to be done?

---

### Post by taurus on 2008-03-04
Have you looked at your own $HOME directory, ~/.vmware?

```
du -h ~/.vmware
```

---

### Post by {BzF}~JOKesTER on 2008-03-04
Ok First Things First: Assuming You Created The Virtual Partition In The Default Directory:

In The Taskbar Goto: Places>>Home Folder, In The Top Bar Click The "View" Menu, And Tick The Box 
"Show Hidden Files" -Now You Can See Hidden Files!!

Next In The Same Directory Scroll Down Until You Find The Folder .Vmware And Delete It!!!

That Should Be It!!!

---

### Post by teamkiller87 on 2008-03-04
You probably still have the virtual HDD on your normal HDD. For VMWare it's in a vmware folder in your home directory. With VirtualBox the directory is hidden, I dunno how it is for VMWare. If you can't find it try enabling View Hidden Files from the View tab on your File Browser menu.

---

### Post by airfoil6205 on 2008-03-04
Thank you very much Everybody!
I never use  /.Trash I only delete everything  but Synaptic use it. I only had to empty  /.Trash as a root and I found 20GB disk space. :)

---

