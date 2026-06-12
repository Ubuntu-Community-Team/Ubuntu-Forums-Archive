---
title: "Problem booting to Ubuntu"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-09-27
I tried to change my partitions so I could have the OS on it's own partition and /home on another. I used this tutorial:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

Now when I boot to Ubuntu I get a message that says:
"Your home directory is listed as:
'/home/larry'
But it does not appear to exist. Do you want to log in with the /(root) directory as your home directory?

It is unlikely anything will work unless you use a failsafe session.":( 
I chose yes and that just took me back to login and it still wouldn't login. I chose no the next time I booted up and it did the same thing.
I went back to the live cd and used the terminal to try to reset everything. This didn't change what happened when I booted up.
Now what do I do? I can reinstall the OS and lose everything. Most of which I have saved on cd's and dvd's. But there are some things I don't have saved that I would rather not lose.
This the main reason I wanted to do this in the first place ](*,) 
Larry

---

### Post by whizbaby on 2006-09-27
First, have you tried to switch to terminal (ctrl-alt-F1) when you see the graphical login screen and login from there (you will get the same error but perhaps be able to pass the login) so that you are able to change the settings on your system more easy than it is from a live system. Then type
mount
to see what's mounted. Is your /home mounted correctly? If not try manually (sudo mount -t ext3 /dev/*replace_by_name_of_home_partition* /home) 
and report the error message(s) (if any).

---

### Post by HareBall on 2006-09-27
> **whizbaby said:**
> First, have you tried to switch to terminal (ctrl-alt-F1) when you see the graphical login screen and login from there (you will get the same error but perhaps be able to pass the login) so that you are able to change the settings on your system more easy than it is from a live system. Then type
mount
to see what's mounted. Is your /home mounted correctly? If not try manually (sudo mount -t ext3 /dev/*replace_by_name_of_home_partition* /home) 
and report the error message(s) (if any).

I tried this and /home was not there. When I entered the sudo mount -t...
I got "mount: special device /dev/replace_by_name_home_partition does not exist"
Anything else to try? I would appreciate any and all help.
Larry

---

### Post by jorn on 2006-09-27
what is the output of:
> sudo fdisk -l

---

### Post by whizbaby on 2006-09-27
> **HareBall said:**
> 
I got "mount: special device /dev/**replace_by_name_home_partition** does not exist"

I don't want to make you look dumb, but
replace the string *replace_by_name_home_partition* with the name of the partition your /home will be mounted from (I thought it was clear that this thing doesn't exist), e.g. /dev/hda2 or /dev/hdb1 or /dev/sda2, don't know enough about your partitioning.
(I'll try to compose a little more comprehensive posts in the future and you promise to start reading between the lines -deal?)

---

### Post by HareBall on 2006-09-27
> **whizbaby said:**
> I don't want to make you look dumb, but
replace the string *replace_by_name_home_partition* with the name of the partition your /home will be mounted from (I thought it was clear that this thing doesn't exist), e.g. /dev/hda2 or /dev/hdb1 or /dev/sda2, don't know enough about your partitioning.
(I'll try to compose a little more comprehensive posts in the future and you promise to start reading between the lines -deal?)
Deal. I thought that looked a little odd, but what do I know. I have only been at this for about 6 days:confused: 
When you say the Partition it will be mounted from, do you mean the one I moved it to or the one I moved it from?
Larry

---

### Post by Predius on 2006-09-27
You need to have the partition where your homedirs are mounted in /home. You can mount it using mount /dev/partitionwherehomediris, replacing that with the device where the homedir is located. 

After that, try logging in and automounting it using fstab. See "man fstab" for more information.

---

### Post by whizbaby on 2006-09-27
R,L being partitions (of the form hdxy, e.g. hda4) let's say R is your root file system and H where you moved the /home to. Then you have an empty /home folder (I hope, if not, create!) on R where you want to mount H on (after it's mounted the folder is called *mount point* for H).

so

sudo mount -t ext3 /dev/H /home

where you have to find hdxy = H (you should know which one it is. If not, post your /etc/fstab please)

---

### Post by HareBall on 2006-09-27
> **whizbaby said:**
> I don't want to make you look dumb, but
replace the string *replace_by_name_home_partition* with the name of the partition your /home will be mounted from (I thought it was clear that this thing doesn't exist), e.g. /dev/hda2 or /dev/hdb1 or /dev/sda2, don't know enough about your partitioning.
(I'll try to compose a little more comprehensive posts in the future and you promise to start reading between the lines -deal?)
I hit send before I thought to tell you I have 3 partitions on this drive.(Not my windows drive) They are(this is from memory):
sdb1, sdb2 and sdb3. 1 & 3 are ext3 and 2 is the swap file. I do know that all I was trying to change was moving my /home from sdb1 to sdb3.
Hope this helps you help me:) 
Larry

---

### Post by whizbaby on 2006-09-27
Then replace hdxy by sdxy in my last post. So you moved your /home to sdb3? Then H = sdb3 and R = sdb1.

---

### Post by HareBall on 2006-09-27
> **whizbaby said:**
> Then replace hdxy by sdxy in my last post. So you moved your /home to sdb3? Then H = sdb3 and R = sdb1.
OK, I went back and tried the sudo mount -t ext3 /dev/sdb3 /home
I didn't get any errors, so I rebooted and still can't get into Ubuntu. Still get the message:
"Your home directory is listed as:
'/home/larry'
But it does not appear to exist. And so on..."
I tried to run fstab, but couldn't figure out the command to get to run.I logged in to my desktop and then ran a list. This is what I found:
bin etc initrd.img lost+found proc sys vmlinuz
boot home initrd.img.old media root tmp vmlinuz.old
cdrom home_backup larry mnt sbin usr
dev initrd lib opt srv var
After this I changed the directory to /home and did a list. All I found in it was lost+found.
I tried to run fstab, but couldn't figure out how.
I will get back to this later. I have to go to work now:( 
Larry:confused:

---

### Post by petri on 2006-09-27
So here you are. You started a new thread and i'm been waiting you at [http://ubuntuforums.org/showpost.php?p=1551034&postcount=7](http://ubuntuforums.org/showpost.php?p=1551034&postcount=7)

Well, you are going to get help here too.




P.S. We still need your ```
gedit /etc/fstab
``` and ```
sudo fdisk -l
``` paste them here. I think you followed the guide too literally. And don't worry about your files, you can always back them up with LiveCD but there is not going to be need to do that.

---

### Post by HareBall on 2006-09-27
> **petri said:**
> So here you are. You started a new thread and i'm been waiting you at [http://ubuntuforums.org/showpost.php?p=1551034&postcount=7](http://ubuntuforums.org/showpost.php?p=1551034&postcount=7)

Well, you are going to get help here too.




P.S. We still need your ```
gedit /etc/fstab
``` and ```
sudo fdisk -l
``` paste them here. I think you followed the guide too literally. And don't worry about your files, you can always back them up with LiveCD but there is not going to be need to do that.

Here are the results for fstabs:
union / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid nodev 0 0
/dev/sdb5 swap swap defaults 0 0
And fdisk:
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
Now I really do need to go. I'll be back in about 9 hours.
Larry:confused:

---

### Post by petri on 2006-09-27
EDIT: Read post #15 instead.

```
sudo fdisk -l
```

Use your left mousebutton to highlight te code above and paste it in terminal with clicking down your scrollwheel. In that way no typos get in :)

---

### Post by petri on 2006-09-27
I'm terribly sorry because I forget that you are in a Live session, you can't see fstab like I wrote above. You have to mount the hd first.

But first, when you tried the recovery did you use your "device names" (like sda1) or did you use [the guides]("http://www.psychocats.net/ubuntu/separatehome.html") "device names" (like hda1)? (I'm using "device names" because I don't know anything better, sorry about my english.) In that case you might try the recovery part again here it comes (remember to press **Enter** after each line): 

> What if it doesn't work?
You know, it really should work, but if you somehow messed up your /etc/fstab and didn't configure it correctly... well, that's why we have a live CD, so we can fix things.

Boot up the live CD, go to a terminal, and type:
```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab
```

Then, reboot. 

Your home backup is named home_backup and you have it still on your harddisk. The thing is that you have to mount the right partition to this /recovery in your case it might be sda1? But if you used that guide without changing the device names, well then it should have protested and said it can't find hda1 or something.

It might be easier do the mounting with GUI? Then you can browse your files also and see they are still there :)
- Go to **System** menu and choose **Administration** > **Disks**. 
- On the left you see all your harddisks but they are not mounted. Click the tab called **Partitions** and you should see three partitions if you have only Ubuntu, four if you have windows too.
- Choose the first partition if you have only Ubuntu, the second if you have windows too. Click the button **Change** > doubleclick **Desktop** > click **Create Folder** > name it **harddisk** > click **Open** and you get back to Disk Manager and there you click **Enable**. Then click OK to close Disk manager (or **Browse** to see your files). By the way the folder **harddisk** is now on your Live-Desktop and you can browse your files when you want as long as you are on the same session.
- Paste in terminal ```
nano Desktop/harddisk/etc/fstab
``` (Remember last time you used **sudo nano /old/etc/fstab** with the guide?) There in terminal you can see which partitions are or should be mounted at boot (you probably have to make the window wider) and if you can see the line > /dev/hda7 /home ext3 nodev,nosuid 0 2 and there isn't **hda7** in your pc then I think that is the problem. Just highlight the text in nano (terminal) with left mousebutton and paste with clicking scrollwheel to us. Mine looks like this

  > GNU nano 1.3.10                    File: Desktop/160/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde1       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc1       /media/hdc1     ext3    defaults        0       2
/dev/hdc3       /media/hdc3     ext3    defaults        0       2
/dev/hdc4       /media/hdc4     ext3    defaults        0       2
/dev/hdd1       /media/hdd1     ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
192.168.123.195:/home  /mnt/home   nfs      rw,hard,intr  0     0


We still need your ```
sudo fdisk -l
``` to see which partitions you really have, which you have created with the guide  and what is it called. Paste it here too. The reason why you can't boot ubuntu should be that something is wrong with your **/etc/fstab**. Someone will help you if I'm at sleep :) I'll be back in about 9 hours.

---

### Post by Metacarpal on 2006-09-27
> **HareBall said:**
> I hit send before I thought to tell you I have 3 partitions on this drive.(Not my windows drive) They are(this is from memory):
sdb1, sdb2 and sdb3. 1 & 3 are ext3 and 2 is the swap file. I do know that all I was trying to change was moving my /home from sdb1 to sdb3.
Hope this helps you help me:) 
Larry

```
sudo mount -t ext3 /dev/sdb3 /home
```

Also, did you:
> ```
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab
```

You'll then be taken to the nano text editor. Add in this line:
```
/dev/sdb3 /home ext3 nodev,nosuid 0 2
``` 
As shown in the tutorial you were following?

---

### Post by HareBall on 2006-09-28
But first, when you tried the recovery did you use your "device names" (like sda1) or did you use the guides "device names" (like hda1)? (I'm using "device names" because I don't know anything better, sorry about my english.) In that case you might try the recovery part again here it comes (remember to press Enter after each line):

Quote:
What if it doesn't work?
You know, it really should work, but if you somehow messed up your /etc/fstab and didn't configure it correctly... well, that's why we have a live CD, so we can fix things.

Boot up the live CD, go to a terminal, and type:
Code:

sudo mkdir /recovery 
sudo mount -t ext3 /dev/hda1 /recovery 
sudo cp -R /recovery/home_backup /recovery/home 
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab

Then, reboot.

OK, everything seemed to go good until I got to the last line of code. Here is what happened each time I tried this:
ubuntu@ubuntu:~$ sudo mkdir /recovery
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 /recovery
ubuntu@ubuntu:~$ sudo cp -R /recovery/home_backup /recovery/home

When I entered the line above I had to wait about 15 minutes for it to gewt finished doing it's thing.
Then I entered the line below.

ubuntu@ubuntu:~$ sudo cp /recover/etc/fstab_backup /recovery/etc/fstab
cp: cannot stat `/recover/etc/fstab_backup': No such file or directory
ubuntu@ubuntu:~$ dir
Desktop
ubuntu@ubuntu:~$ cd desktop
bash: cd: desktop: No such file or directory
ubuntu@ubuntu:~$

And here is what I got when I ran sudo fdisk -l:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       18846   151340332+   7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686   83  Linux
/dev/sdb2           19274       19457     1477980    5  Extended
/dev/sdb3            5100       19273   113852655   83  Linux
/dev/sdb5           19274       19457     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       18846   151340332+   7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686   83  Linux
/dev/sdb2           19274       19457     1477980    5  Extended
/dev/sdb3            5100       19273   113852655   83  Linux
/dev/sdb5           19274       19457     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order.

I am about to try another reboot and see what happens.

---

### Post by HareBall on 2006-09-28
- Paste in terminal ```
nano Desktop/harddisk/etc/fstab
``` (Remember last time you used **sudo nano /old/etc/fstab** with the guide?) There in terminal you can see which partitions are or should be mounted at boot (you probably have to make the window wider) and if you can see the line  and there isn't **hda7** in your pc then I think that is the problem. Just highlight the text in nano (terminal) with left mousebutton and paste with clicking scrollwheel to us. Mine looks like this

  


We still need your ```
sudo fdisk -l
``` to see which partitions you really have, which you have created with the guide  and what is it called. Paste it here too. The reason why you can't boot ubuntu should be that something is wrong with your **/etc/fstab**. Someone will help you if I'm at sleep :) I'll be back in about 9 hours.[/QUOTE]

I opened both  Desktop/harddisk/etc/fstab and /old/etc/fstab. What I found is that old/etc.fstab is empty and the other looks like this:
  GNU nano 1.3.10       File: Desktop/harddisk/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0




^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

I also found when I browsed harddisk that all my files are still there.
If I were to reinstall the OS on another partition, would this help recover my stuff or would it be even harder to access?
I'm not in a big hurry, but I really want to get this running so I can learn what else I can do with this OS. Maybe not break it for awhile;) 
Larry, still:confused:

---

### Post by petri on 2006-09-28
> OK, everything seemed to go good until I got to the last line of code. Here is what happened each time I tried this:
ubuntu@ubuntu:~$ sudo mkdir /recovery
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 /recovery
ubuntu@ubuntu:~$ sudo cp -R /recovery/home_backup /recovery/home

When I entered the line above I had to wait about 15 minutes for it to gewt finished doing it's thing.
Then I entered the line below.

ubuntu@ubuntu:~$ sudo cp /**recover**/etc/fstab_backup /recovery/etc/fstab
cp: cannot stat `/recover/etc/fstab_backup': No such file or directory
ubuntu@ubuntu:~$ dir
Desktop
ubuntu@ubuntu:~$ cd desktop
bash: cd: desktop: No such file or directory
ubuntu@ubuntu:~$

The bold **recover** above instead of **recovery**? Seems like typo and therefore ubuntu does not found your fstab_backup

---

### Post by petri on 2006-09-28
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 * 6 18846 151340332+ 7 HPFS/NTFS
/dev/sda3 18847 19452 4867695 db CP/M / CTOS / ...

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 5099 40957686 83 Linux
/dev/sdb2 19274 19457 1477980 5 Extended
/dev/sdb3 5100 19273 113852655 83 Linux
/dev/sdb5 19274 19457 1477948+ 82 Linux swap / Solaris

Partition table entries are not in disk order.

You have two harddisks about 160GB. The first on **sda** has tre partitions, **sda1** is probably Dells "Recovery CD" **sda2** is your windows and **sda3** I don't know.

Your second harddisk **sdb** is for Ubuntu. **sdb1** is for root, your ubuntu systemfiles. **sdb2** shame on me I don't know I have it too but can't see it in Disk Manager. **sdb3** is your new home partition! and **sdb5** is your swap partition which is used by the LiveCD, that is the reason you can see it if you paste  **gedit /etc/fstab** (or **nano /etc/fstab** which ever you prefer) in live-session without mounting any harddisks.

If the recovery doesn't work then your can add a line to fstab like in the guide (and Metacarpal writes above):

guide:
> Next, we're going to specify to use the new home partition as /home:
```
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab
```

You'll then be taken to the nano text editor. Add in this line:
```
/dev/hda7 /home ext3 nodev,nosuid 0 2
``` Then save (Control-X), confirm (Y), and exit (Enter)

After you reboot, you should be now using your new /home partition.  though you have to add line ```
/dev/sdb3 /home ext3 nodev,nosuid 0 2
``` with your "Device Name" which is **sdb3** for your new home partition and not the **hda7** as in the guide.

This is the cause to your problem, there wasn't no entry in fstab to your home partition, no **/dev/sdb3** line was there.> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/sdb5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by petri on 2006-09-28
> ...If I were to reinstall the OS on another partition, would this help recover my stuff or would it be even harder to access?...

Yes you could do that too. Create first a partition with LiveCD gparted and then install the new Ubuntu 8)  There, in partitioning do a mount för **sdb3** as **/home** and **do not format** that partition! How to do that you will find at [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

But I think you fix this with above instructions. One thing that might still stop you is that you have tried to recover your **/home** but your files should be intact at **sdb3**. You can check it with Disk Manager.

---

### Post by HareBall on 2006-09-28
> **petri said:**
> Yes you could do that too. Create first a partition with LiveCD gparted and then install the new Ubuntu 8)  There, in partitioning do a mount för **sdb3** as **/home** and **do not format** that partition! How to do that you will find at [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

But I think you fix this with above instructions. One thing that might still stop you is that you have tried to recover your **/home** but your files should be intact at **sdb3**. You can check it with Disk Manager.

Actually my files are intact at sdb1. I just went and checked. I can't access sdb3. There is only one file that shows up and it is called lost+found and it will not let me open it. It pops up a message saying I don't have permissions.
I have decided that I am going to reformat sdb3 and install the OS there. Then I will move my files over to there and start over with the moving of my /home partition. I believe I can do it right this time;) 
Larry,:confused:  still confused, but not as much.

---

### Post by HareBall on 2006-09-28
[QUOTE=petri;1554171]Yes you could do that too. Create first a partition with LiveCD gparted and then install the new Ubuntu 8)  There, in partitioning do a mount för **sdb3** as **/home** and **do not format** that partition! How to do that you will find at [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
I tried all of these instructions. I couldn't get it to work. I re-installed from the Live disk. I have access to the files I wanted to move. After I move them I will try to move my /home partition again.
Hopefully I will not be asking about this again. I think I learned a good lesson about this.
I am sure you will be seeing posts from me in the near future.
Thank you for all the time trying to help me,
Larry

---

### Post by petri on 2006-09-28
Or try again with this partition you already have? This time using your **sdb*** :)



EDIT: So you installed Ubuntu already and it is working? Great. And you can access all your files? That is great too. :-D

---

### Post by HareBall on 2006-09-28
> **petri said:**
> Or try again with this partition you already have? This time using your **sdb*** :)



EDIT: So you installed Ubuntu already and it is working? Great. And you can access all your files? That is great too. :-D

Yes, it is all up and running. At least untill I do something else to it;)
I am going to try to move /home tonight when I get home from work. Might be back in this thread asking again:0
I am trying to get a friend to try his hand at using Ubuntu. He says he isn't ready yet. I wish he lived closer so I could show him mine.
Later,
Larry

---

### Post by petri on 2006-09-28
Just use your **sdb*** when moving **/home**. That operation is not possible in windows at all and (when it works) on linux it shows you how much more you can do with linux :D  Just read carefully and make notes about partitions. And now you should have an partition for **/home** ready and waiting? :rolleyes: 

I'm just wondering how did you manage to install a new Ubuntu and keep your files in your old **/home** in same partition? :confused:  If it was because of the help on this forum that is an argument for linux and your friend ;)

---

### Post by HareBall on 2006-09-28
> **petri said:**
> Just use your **sdb*** when moving **/home**. That operation is not possible in windows at all and (when it works) on linux it shows you how much more you can do with linux :D  Just read carefully and make notes about partitions. And now you should have an partition for **/home** ready and waiting? :rolleyes: 

I'm just wondering how did you manage to install a new Ubuntu and keep your files in your old **/home** in same partition? :confused:  If it was because of the help on this forum that is an argument for linux and your friend ;)

I didn't keep them on the same Partition. They were moved to sdb1. I can't figure out why they would show up in sdb3. I installed the OS on sdb3 to keep from deleting them from sdb1. Later, I am going to delete everything from sdb1 and then move /home there.
Got to go now,
I owe I owe
It's off to work I go:biggrin:

---

