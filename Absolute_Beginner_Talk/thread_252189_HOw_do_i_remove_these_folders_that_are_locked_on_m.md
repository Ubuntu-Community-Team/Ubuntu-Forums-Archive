---
title: "HOw do i remove these folders that are locked on my desktop?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Rizla on 2006-09-06
Hey GUys,

I have a couple folders on my desktop that have a lock icon hovering above them.  I want to remove them.  Even though I can open them to read the contents, thats about all i can do.  They're just taking up space.  These folders are also located in my /media folder.  I think yesterday i wanted to put these on my desktop for some reason and transfered them and thats how they showed up but now i cant get them off?  I cant delete it from there either..  ANy ideas? 

Here's my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/XP_Drive   ntfs    nls=utf8,umask=0222       0       0
/dev/sda5       /media/Data_Drv   ntfs    nls=utf8,umask=0222  0       0
/dev/hda7       /media/Share_Drv  vfat    auto,users,rw  0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

Any help would be greatly appreciated.  Thanks for all the help thus far.

PS- I took a screenshot and attached it so you can see.

---

### Post by Tomosaur on 2006-09-06
The lock means you are not the owner. Do not delete anything from /media until you've verified what they are exactly, but to delete from desktop:
```

sudo rm filename filename filename

```

Or, for the more 'correct' way, let's assume your username is 'me'
```

sudo chown me filename filename filename
rm filename filename filename

```

---

### Post by whizbaby on 2006-09-06
What would be pretty more interesting than your fstab is the output of (in terminal):

**ls -la Desktop**

Besides it's a very bad idea to move the contents of the /media directory, you should rather generate links to contents (done with the command **ln**(little 'L'). For the manual of a command type **man *command***)

For removing anything in *Desktop* type:

**sudo rm -r Desktop/***

that should annihilate all contents of this folder.

---

### Post by petri on 2006-09-06
Try one of these, chance to your Desktop folder which might be 
```
cd /home/YOURUSERNAME/Desktop
```

```
sudo rmdir foldername
```
or
```
sudo rm -r /foldername
```

---

### Post by Rizla on 2006-09-06
I dont want to delete any of the contents of those folders.  I jsut dont want them showing up on my desktop anymore.  I recieved alot of suggestions, which one should i use to not kill any data in those folders?

I know linux's power feature is how it compartmentalizes thigns so that a regular user cant mess up their systems but it makes it a little difficult for a seasoned windows user to get used to these changes.  I've been having so many issues with the dirves mounting as root and me not having access to them.  I had to edit my fstab to put them in my /media folder, but for some reason they were showing up with the locked icon too.

---

### Post by petri on 2006-09-06
Ooops, do not use mine 8) 

But. But if you have these folders at the original folder /media then you can delete the folders att the desktop. 
Icons you say, or are they just links? Then just delete them. You could make a copy of them in your home folder or something.

---

### Post by Rizla on 2006-09-06
> **Tomosaur said:**
> The lock means you are not the owner. Do not delete anything from /media until you've verified what they are exactly, but to delete from desktop:
```

sudo rm filename filename filename

```

Or, for the more 'correct' way, let's assume your username is 'me'
```

sudo chown me filename filename filename
rm filename filename filename

```

Can i do a chown on the folders so that I can have them instead of root?  I can do a screen shoot of my desktop directory right now cuz im at work and wont be back home for another 7+hrs. (i work 3-11 East coast time.)

---

### Post by Maddoguk2 on 2006-09-06
If these folders are not wanted, right click the folder and go to properties. Go to permissions and change the attributes by ticking all 9 boxes. Then you can delete it. Be warned that doing this my render the OS inoperable. I only say this because I do not want to be blamed for what might happen. YOU HAVE BEEN WARNED.

---

### Post by Tomosaur on 2006-09-06
Yes, you can chown the directory, but unless you specify that you want to recursively chown, then only the actual directory's owner will be changed. From the looks of it these folders are not files, but extra links to your mounted volumes. The two versions of Data_Drv have the same name, which could be problematic, but you should be able to rm XP_Drive easily enough:
```

sudo rm XP_Drive

```
For the Data_Drv file, I would personally:
```

sudo chown vic Data_Drv

```

then right click > delete from the desktop.

---

### Post by Rizla on 2006-09-06
> **Tomosaur said:**
> Yes, you can chown the directory, but unless you specify that you want to recursively chown, then only the actual directory's owner will be changed. From the looks of it these folders are not files, but extra links to your mounted volumes. The two versions of Data_Drv have the same name, which could be problematic, but you should be able to rm XP_Drive easily enough:
```

sudo rm XP_Drive

```
For the Data_Drv file, I would personally:
```

sudo chown vic Data_Drv

```

then right click > delete from the desktop.

if i sudo rm XP_Drive will that delete my data?  Thats my xp partition drive.  I DO NOT want to delete that.. well maybe.. :)

---

### Post by Tomosaur on 2006-09-06
No, because the thing you're seeing on your desktop is only a LINK to the data. Much like a shortcut in Windows. You don't have to worry about deleting  anything from your XP partition :)

---

### Post by Rizla on 2006-09-06
Quick followup.  Can someone please help me understand whats happening so that i'm more knowledgeable about how linux handls short cuts/links.  I was under the assumption that the icons on my desktop were shortcuts to the folders located in the /media/ folder.  Therefore a simple delete of the shortcut would be all i'd need.  But it seems a lot more complicated than that.

---

