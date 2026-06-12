---
title: "new hard drive setup"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-28
i have added a new IDE hard drive to my computer running Ubuntu 7.10.  i have installed GParted and created 2 new ext3 partitions on this hard drive.  when i mount these volumes, their mount points are set to '/media/disk' and '/media/disk-1', and under the Computer location, they are showing as '39.2 GB Volume disk' and '38.3 GB Volume disk-1' when mounted.  i am not able to add files or folders to either of these volumes- when i right-click inside either volume to do so, the options for creating a file or folder are greyed out.  i also want to change the labels for each of these volumes- so that when i go to the Computer location, the '39.2 GB Volume disk' icon will show up as 'My files' as an example.

i have read many posts and tutorials that explain long and drawn-out ways of achieving these goals, but what i am looking for is a way to perform each of these tasks graphically from the desktop environment (GNOME i believe it is called)- in other words, i don't want to go through the Terminal/command prompt to do this... i am new to Ubuntu and i am still learning most of the commands that i am reading about, so i'm not interested in using a number of commands that i don't understand when i have little knowledge of what any of them do- even after reading up on them.  plus, i believe that there should be a much simpler way of doing these tasks than what many of the posts i have read are suggesting- like the way Windows allows you to make these types of changes in My Computer.  can anyone explain to me how to do this without having to reformat my hard drive and change things like user permissions and mount points and editing different files via the command prompt?  i just want to be able to make these changes with this hard drive as it is.

thanks in advance for any and all suggestions.

---

### Post by Nepherte on 2008-01-28
You will have to change the ownership of that disk:
```
sudo chown user:group /media/disk
```
with user being your user name and group the group you belong to.

---

### Post by Matt26 on 2008-01-28
will this allow me to then change the volume labels by going to the Computer location, right-clicking the volume icon and using the Rename option?  i have read that this option is only intended for use with files and folders.  thanks.

---

### Post by ajgreeny on 2008-01-28
Should do, /media.disk and /media/disk-1 are just that, folders.  Try opening the /media folder so that the contents are on the right pane of nautilus and you should be able to rename the folders as you want.  The only possible problem is if you want them mounted at boot up from the /etc/fstab file.  If so I think you will need to edit their mount points in fstab as root ```
gksudo gedit /etc/fstab
```If anyone knows different to this, no doubt they will let us both know that I'm wrong!

---

### Post by Matt26 on 2008-01-28
so to make the volume label changes- should i go directly to the folders under /media and change the names of these folders from 'disk' and 'disk-1' to whatever i want?  or can i make the changes directly from the Computer location by right-clicking the icon for the volume and choosing the Rename option?

also, does the volume need to be unmounted to make these changes (in which case the folders under /media are no longer present), or can i make these changes while the volumes are mounted?

---

### Post by logos34 on 2008-01-28
> **Matt26 said:**
> so to make the volume label changes- should i go directly to the folders under /media and change the names of these folders from 'disk' and 'disk-1' to whatever i want?  or can i make the changes directly from the Computer location by right-clicking the icon for the volume and choosing the Rename option?

[http://www.linux.com/base/ldp/howto/Partition/labels.html](http://www.linux.com/base/ldp/howto/Partition/labels.html)

---

### Post by Matt26 on 2008-01-28
i have tried e2label but it didn't work for me- it kept repeating a line stating the syntax and usage of the command like i wasn't using it right- my volumes get mounted to /media instead of /dev as i noticed 32label uses in it's syntax- could that be why it's not working for me?  thanks.

---

### Post by logos34 on 2008-01-28
try tune2fs

---

### Post by Matt26 on 2008-01-28
i got the volumes labelled the way i want them using e2label, and i have added them to my /etc/fstab to be auto-mounted- i rebooted to see if this worked and now i can't see the volumes under Computer- they should up in GParted as mounted (and i don't have the option to unmount them).  any ideas?

---

### Post by logos34 on 2008-01-28
Can you post your fstab?

also,

ls -l /dev/disk/by-label

---

### Post by Matt26 on 2008-01-29
i will post my fstab file as soon as i am able to- one thing i thought of after looking at an example fstab is that i didn't include the UUID of each volume... could this be causing the issue?  i have no idea how to find this UUID either if that is the case, if someone could tell me where to find it that would be great.  thanks.

---

### Post by ajgreeny on 2008-01-29
```
 ls -l /dev/disk/by-label
```as logos34 suggested.  In fact the fstab file will work fine using the dev/hda1 style, without the UUIDs of the partitions so it shouldn't be that causing your problem.

---

### Post by Matt26 on 2008-01-29
here are the results from ls -l /dev/disk/by-label:

total 0
lrwxrwxrwx 1 root root 10 2008-01-28 23:41 Downloads -> ../../sdc5
lrwxrwxrwx 1 root root 10 2008-01-28 23:46 Stuff -> ../../sdc6
lrwxrwxrwx 1 root root 10 2008-01-28 23:41 VMware_Vista -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-01-28 23:41 VMware_XP -> ../../sdb1


and here is what i have entered into /etc/fstab for the volumes i want automounted:

#auo-mount new VMware volumes
/dev/sdb1 /media/VMware_XP ext3 defaults 0 0
/dev/sdb2 /media/VMware_Vista ext3 defaults 0 0

the VMware_XP and VMware_Vista volumes are the ones i am trying to automount.

---

### Post by logos34 on 2008-01-29
well, this is the standard fstab format for labels:

> **LABEL=**VMware_XP /media/VMware_XP ext3 defaults 0 0

Personally, e2label has always given me trouble, so I use tune2fs.

---

