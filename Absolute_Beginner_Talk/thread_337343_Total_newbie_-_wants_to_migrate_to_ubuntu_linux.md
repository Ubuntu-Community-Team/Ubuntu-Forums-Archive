---
title: "Total newbie - wants to migrate to ubuntu linux"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by richie82 on 2007-01-12
Forgive my ignorance as i do not know how simple a question this is, as it probably will be to most experienced users.

scenario:
-windows user wanting to free themselves of the evil that is microsoft.
-120gb hdd, partition into roughly 4x 40gb ext3 partitions using gparted.
-newly installed ubuntu 6.10, cant save anything to the 3 extended logical partitions [all ext3].

Can someone please explain as clearly as possible, why it is, that i am not able to save any files to, or move any files to my ext3 partitions that i created with gparted after installing ubuntu 6.10?

it just says access denied. all that is in them is a folder called lost+found which also does not let me access.

please help set me free.

i want to be a linux user fully.

thanks

---

### Post by richie82 on 2007-01-12
[QUOTE=richie82;2005447]Forgive my ignorance as i do not know how simple a question this is, as it probably will be to most experienced users.

scenario:
-windows user wanting to free themselves of the evil that is microsoft.
-120gb hdd, partition into roughly 4x 40gb ext3 partitions using gparted.
-newly installed ubuntu 6.10, cant save anything to the 3 extended logical partitions [all ext3].

Can someone please explain as clearly as possible, why it is, that i am not able to save any files to, or move any files to my ext3 partitions that i created with gparted after installing ubuntu 6.10?

it just says access denied. all that is in them is a folder called lost+found which also does not let me access.

please help set me free.

i want to be a linux user fully.

thanks

Windows had detected you do not have a keyboard. Press ‘F9&#8243; to continue.

---

### Post by statictonic on 2007-01-12
Did you already mount the NTFS directory while in ubuntu?  That'd be the first step, I'm assuming ubuntu is installed and working at this point, although correct me if im wrong on that.

---

### Post by richie82 on 2007-01-12
I no longer have any ntfs drives. this is concerning ext3. I have formatted my new hard drive completely and all 4 partitions are ext3. I cant do anything to my partitions.

---

### Post by halitech on 2007-01-12
if they are outside your home partition (/home/username) then you will not have rights to save, delete, rename, create or anything. you will need to change ownership on the partitions in order to use them, otherwise it will only be root that can use them

---

### Post by richie82 on 2007-01-12
can you tell me or refer me to where i can find out how to do this? i have found some things concerning unmasking and others about chmod, but i am not to sure of what to do.

---

### Post by halitech on 2007-01-12
I think it would actually be a chown that you would need to do on them but not totally sure at the moment. I have 2 seperate drives and it works differently but I know you don't have permission to write if outside your home.

---

### Post by richie82 on 2007-01-12
cool. i hope someone will see this and know exactly how to do it. ill try and look for chown and permissions. as it can get really confusing.

thanks for your help, you have made it clearer about what is actually going wrong "ownerships" concerning my ext3 partitions. i seem to be ok with everything else, thanks to automatix haha.

i just not to clever with thes terminal stuff at the moment.

[as a seperate question, why is it different if you have two hdd's? do u create 2 home directories then?]

---

### Post by halitech on 2007-01-12
with the 2 drives I created a mount point called /storage and then edited fstab so it loads the partition everytime I reboot and then modified the ownership to my account so I don;'t have to sudo to do anything in it. You can make the mount point anywhere, I just happened to make it there. Other people have made it mount in /home/username/music , etc.

---

### Post by misha680 on 2007-01-13
For changing permissions there is an easier way than the terminal too, if you are really new to ubuntu you might just try using Alt-F2 to run a command and then typing:

```
gksu nautilus
```

This will ask you for your password and then will open nautilus which is the GNOME desktop environment file manager but this one will run as root. Now, if you want to change the permissions of a file or folder you can just right click on it, click on Properties..., go to the Permissions tab, and there you can just the owner and the permission of the file or folder.

If you want to go the terminal route, to change the owner you can just use the command:

```
sudo chown newuser pathtofileorfolder
```

Misha

---

### Post by tonyr1988 on 2007-01-13
IIRC, you'll need to change your /etc/fstab file, too.

> sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

There will be a line for each partition (/dev/hda1, /dev/hda2, /dev/hda3, and /dev/hda4). a = first hard drive, 1/2/3/4 = partitions. For each line, there are 6 columns. The first three (partition, mount point, and file system) as well as the last two (two numbers, probably 0 and 0) should be fine. You may need to change the fourth one ("options") to allow you access. For ext3, this should do the trick:

> /dev/hda2       /shared         ext3    **users,rw,exec,suid,dev**  0       0

(first two columns will be different on yours, bold is the stuff you'll want to add).

---

### Post by richie82 on 2007-01-13
thanks tonyr1988. it seems to have worked spot on!

i think i understand some of that line ie, **user**, **rw**[read+write access], **exec**[excute? maybe], **suid**[is this that new long number formart of hdd detection ive read a little about?] and **dev** i and not too sure of?

as i am the only user for my pc, this will be fine to do.

thanks again

---

### Post by steve.horsley on 2007-01-13
You may want to link these from your desktop. If so, open the nautilus file browser and drag the directory you want to link to your desktop using the middle mouse button (or using both buttons if you have no middle button) and choose the link option.

---

### Post by richie82 on 2007-01-13
thanks, they are nicely on my desktop now haha.

bit torrent is my next conquest, does anyone have recommendations for firewalls? im using firestarter but its a bit basic for my liking. ie, program control and intrusions blocked counters would be a nice thing.

---

### Post by Buck2348 on 2007-01-13
> **richie82 said:**
> i think i understand some of that line ie, **user**, **rw**[read+write access], **exec**[excute? maybe], **suid**[is this that new long number formart of hdd detection ive read a little about?] and **dev** i and not too sure of?
thanks again
User means any user can mount the filesystem, and only that user can unmount it.  User**s** means any user can mount or unmount it.  Exec allows for executing binaries in the filesystem.  suid stands for something like set user id and allows set-user-identifier or set-group-identifier bits to take effect.  (You might have to read up on permissions to get that--I'm still a little hazy.)  The long number you refer to is the UUID of the device being mounted.  Here is a line from my fstab:
```
UUID=918a24d8-4e50-4946-a5bb-9714c9fdb149 /home           ext3    defaults        0       2
```  The code identifies a device uniquely (I don't have any idea how the system gets the code) so that if it is physically moved to, say, a new ide cable position or usb slot its mount point and therefore its system path will remain the same.  I've read about the meaning of dev but don't understand it.

Some good reading on these topics:  man fstab (just enter that in a terminal), man mount, [this page on permissions]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html"), and [this thread on fstab.]("http://www.ubuntuforums.org/showthread.php?t=283131")
Welcome to Ubuntu--I think you're going to like it.

Buck

---

