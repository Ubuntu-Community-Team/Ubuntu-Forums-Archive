---
title: "How do I get rid of some folders in my home folder while apps can still use them?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Redrazor39 on 2008-03-16
I attached a pic of my home folder. There are some folders like the google earth one and the google earth file and the nautilus thing that I don't want to see, but I still want google earth to be able to use it. I also have that VMware Fusion or w/e folder but access is denied to move it to the trash. I think I tried installing that once but I wanted to completely get rid of it (full uninstall). How do I do this?

---

### Post by Diabolis on 2008-03-16
You can hide folders/files by adding a "." to the beginning of their names.  If you press ctrl+h all your hidden files will show up. By doing this your applications won't be able to see the files/folders unless they have an option to set the route to those files.

---

### Post by Redrazor39 on 2008-03-16
I want to hide the google earth stuff but I want Google Earth to be able to use them so it still works. Also, whenever I try to delete the VMware_Fusion folder it says I do not have permissions to do that.

---

### Post by Diabolis on 2008-03-16
You can hide it by renaming it from "gogle earth" to ".google earth", notice the point at the beginning, but as I said you'll have to open google earth and look for a option where you can modify the directory that will be used for file storage/reading IF it has it.

The vmware folder was created whenyou installed vmware, so it was created by root not by you. If you want to remove it, you have to do it as root.

```
sudo rm vmware/
```
if it has files inside:
```
sudo rm -r vmware/
```

I'm telling you what you would have to do in order to accomplish your first objective, which is hide or delete files. 

Probably if you do this **you'll wreck vmware**, unless you can specify where it can save or look up for files.

---

### Post by Redrazor39 on 2008-03-16
What does vmware even do? And why is it bad to remove? Also, I've decided to just uninstall Google Earth. I'll use Google Maps onlinux and Earth on Vista. 

Note: I just clicked uninstall and all of google earth was gone.

Now about vmware...

---

### Post by Diabolis on 2008-03-16
Since you didn't know what vmware is, probably you should remove it. vmware is software used to make virtual machines so you can run other operating systems inside a running operating system. 

I wonder why is installed in your system. After uninstalling it the folder might be deleted, if not, do it yourself with the commands that I posted before.

You should not delete files if you didn't make them. Applications depends on different kinds of files in order to run properly, if you delete them they won't be able to run or if they do they'll crash at some point. Also, if you start deleting stuff by hand without really knowing what are you doing, chances are that you'll delete files needed to uninstall applications.

Actually this have happened to me only with vmware, every other application that I have used does not stores any files, besides configuration files, into my home folder.

---

### Post by Redrazor39 on 2008-03-16
Ok, also there's a thing called nautilus-debug-log.txt. Should I keep that? How can I hide it so it's still usable by the system, but I don't see it, or am I supposed to use it?

ALso, I think I installed VMware Fusion once, but then I decided I didn't need it because i just went dual-boot.

---

### Post by Redrazor39 on 2008-03-16
I meant vmware player lol

---

### Post by Redrazor39 on 2008-03-16
And the folder is called VMwarePlayer-2.0.2, so will that change the command to remove it?

And again, what about nautilus-debug-log.txt?

---

### Post by Diabolis on 2008-03-16
I suggest you to make a documents folder or a storage partition in you hard drive so you don't have to deal with application files. I have a documents folder, so I know that whatever is outside that folder I didn't make it.

If you are so curious, back up all your files and start deleting stuff to learn what happens.

---

### Post by Diabolis on 2008-03-16
yes, the command works using the name of the folder that you want to remove.

---

