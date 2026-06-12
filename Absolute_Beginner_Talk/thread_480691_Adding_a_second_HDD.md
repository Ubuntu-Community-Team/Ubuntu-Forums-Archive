---
title: "Adding a second HDD"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Hranj on 2007-06-21
ive got a bunch of computers lying around the house all of which have ubuntu installed and running on them. ive been meaning to make a music server out of the one for quite a while and i finally am but i ran into a roadblock.

they are old computers and dont have a lot of space on them, about 15 gigs, and i wanted to add a second hdd so that i could have more storage for my music files.

so what i did was take a hdd out of one of the old computers that i dont use and popped it into the music server.

my question is, how can i format the second hdd so that the ubuntu OS is wiped off of it to make room for music?

---

### Post by rich.bradshaw on 2007-06-21
gparted.

sudo apt-get install gparted

---

### Post by Hranj on 2007-06-21
ok so i installed gparted but im lost. what do i do from here. the two hdds both come up and i found that one that i want to format but how do i do it. i think the problem is right now it sees it as a removable drive because all i did was set it to slave and plug it in but im not sure, dont really know what im doing.

there is a lock icon by the part that i want to format so i guess thats the problem but idk how to fix it

---

### Post by EagleRock on 2007-06-21
The lock means that it probably was automounted.  If you unmount it (right click on the row in gparted, select unmount), you should be able to format it.  If I were you, though, I would double-check that are you are indeed looking at the right drive.  Check the GB size and partition layout to see if it matches.

---

### Post by Hranj on 2007-06-21
thanks eagle rock. that worked and now its formated. but there is a partition on that drive one that i found on the master drive as well so i guess its something that is installed with ubuntu.

its a file tree with one subfolder. the main one is /dev/sdb2 and its formated as an extended

the one under that is /dev/sdb5 and its formated as a linux-swap.

can i get rid of these or are they essential to the hdd

---

### Post by Hranj on 2007-06-21
o and i wasnt sure what i should format it as so i formated it to an ext3, im not sure if that was right or not or what it should be formated as.

also my computer isnt picking up the second hdd anymore. its not recognizing it in the computer screen and only gparted is finding it. how can i make it so that the system "sees" it again.

---

### Post by bren on 2007-06-21
maybe you need to mount it again?

mount /dev/hdb1 /media/anamelikemusicdisk

(assumes disk is b and partion is 1 but you can check yours in gparted)
if this works you can add to your fstab file to make auto for future

bren

---

### Post by Hranj on 2007-06-21
ok all i had to do was reset the computer and it sees it again. but its still coming up as a type of removable disk and not as a second hdd. there is an icon on the desktop and it is a second storage device in the places menu. how do i make it so that it is seen as a second hdd?

also when i open it there is this folder called "lost and found" that i cant open because i dont have the right permissions. how can i make it so im the super user on this disk too. 

i know this is a lot but i cant figure this out so i need to come and bother the forums. thanks everyone that has helped and will help.

---

### Post by paparucino on 2007-06-21
> **Hranj said:**
> ok all i had to do was reset the computer and it sees it again. but its still coming up as a type of removable disk and not as a second hdd. there is an icon on the desktop and it is a second storage device in the places menu. how do i make it so that it is seen as a second hdd?

Did you removed the logical partition?
Try to resize the second hdd so to have only a partition. You can do it via gparted.
if this doesn't work, you should check the jumpers and the BIOS.

> 
also when i open it there is this folder called "lost and found" that i cant open because i dont have the right permissions. how can i make it so im the super user on this disk too. 

You must live with "lost+found" :-) unless you remove the hdd from the fsck check which happens every 30 mount.
I don't remeber how to do it, but you'll find a lot of docs in the ubuntuforums.

---

### Post by Hranj on 2007-06-21
sorry but whats a logical partition?

---

### Post by Hranj on 2007-06-21
ok so i deleted the logical partition but now there is this thing in gparted under the partitions list that says "unallocated" what does this mean and is there any way to get rid of it because it is taking up 431 mb. not alot on know but these drives are small and i want every kb i can get out of them.

---

### Post by bren on 2007-06-21
hranj

unallocated = spare space on the disk

click a partition on the same disk and increase the size of this partition it to use up the spare space (rightclick/resize)

bren

---

### Post by Hranj on 2007-06-21
unallocated space is gone and now there is just one entry under the partitions list. 

/dev/sdb1 formatted as a ext3

but its not mounted. how do i now mount the drive?

---

### Post by Hranj on 2007-06-21
ok so i popped the drive into one on my other ubuntu computers to see what came up and its still unmountable. this is the exact error message i get

> Unable to mount the selected volume
error: device /dev/hdb1 is not removable

error: could not execute pmount

---

### Post by EagleRock on 2007-06-22
"Extended Partition" is merely a placeholder for other special partitions inside of it like Linux swap.  It's not an actual partition that you do anything with...it's just there to hold other partitions.

"Swap Partitions" are vital to Linux, as they are used to support the RAM in your machine.  When you run out of space, loaded applications that aren't currently active and moved to swap and purged from RAM.  Without it, your system will lose a lot of performance.  However, if this is for a secondary drive, it can be deleted as you did.  Also, I would've recommended extending your other partition, but you seem to have done that as well.

The ext3 filesystem is a good default to use, as it is Linux native.  There are other types that have different pros and cons, but ext3 is a solid choice.

A "Logical Partition" is a kind of "virtual" partition.  A normal partition is just what it is...a regular, normal, physical partition on the drive.  Certain types of filesystems, notably the swap partition, live under another partition (the extended partition).  It's just getting technical for saying that a partition is inside of another partition.

Also, if you're having mount issues, try mounting it manually in a terminal window:

```

sudo mkdir <MOUNTPOINT>
sudo mount /dev/<DRIVE>

```

Where <MOUNTPOINT> is equal to where you want the drive to be mounted (e.g. /drive or /home/drive) and where <DRIVE> is equal to the drive name (e.g., sda1, hdb2, etc.)

---

### Post by Hranj on 2007-06-22
ok, i tried doing the mkdir so i could choose a mount point before but my problem is that when i do the mkdir command it makes a directory in my master drive not the slave.

i cant figure out how to cd to the slave drive because, well idk why i just dont know what im doing.

also whenever i open up that second drive the only thing i can do is look at it. when i open the browser on it it asks me for my password because access is restricted for security reasons and once i open it all i get to do is look at that lost and found folder i cant make any folders move any files there, nothing. is this normal?

---

### Post by EagleRock on 2007-06-22
Everything you do in *nix (UNIX, Linux, BSD, etc.) is under the umbrella of one huge directory, root (/).  When you mount a new drive, you are simply mounting it to a directory under root.  In the case of your primary drive, your mount-point is root itself, which is why it seems your primary drive is that particular drive.  However, when you make a directory (e.g. /drive) and mount the other hard drive to it, that folder is now the root of your secondary drive.  It can be confusing, as it's a completely different mindset than Windows.  Even CD-ROMs and removable media when automounted are simply under root (usually in a place like /mount/cdrom, /mnt/cdrom, or just /cdrom).

---

### Post by Hranj on 2007-06-22
ok so i make a directory to mount to now how do i find out the name of the second drive and how does it know to mount to that folder that i just made

---

### Post by Hranj on 2007-06-22
ok so i tried what you told me the whole mkdir and mount commands and this is what i got

```

dhranj@dhranj-desktop:/$ sudo mount /dev/sdb1
[mntent]: warning: no final newline at the end of /etc/fstab
mount: /dev/sdb1 already mounted or /media/disk busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/disk

```

---

### Post by EagleRock on 2007-06-22
A simple way to find out the device name of your partition is to use gparted.  Once you find out the name (it will be something like  /dev/hda1 or /dev/sda1), you make a directory you want the drive to fall under.  I recommend keeping to convention and using the mnt folder:

```
sudo mkdir /mnt/drive
```

Now you need to mount the partition to that folder you just created (I'm going to assume it's called /dev/hdb1):

```
sudo mount /dev/hdb1 /mnt/drive
```

Now, if you run "df -k", you should see an entry for your newly mounted drive, as well as the mount point.

If you go into /mnt/drive through the terminal or through a file browser, you will see those files under that folder.

There is a way to get it to automount upon startup, but it involves editing /etc/fstab.  I'm not sure if ubuntu has a GUI utility to make it easier, as I'm used to doing it manually through the command line in Debian.

---

### Post by EagleRock on 2007-06-22
> **Hranj said:**
> ok so i tried what you told me the whole mkdir and mount commands and this is what i got

```

dhranj@dhranj-desktop:/$ sudo mount /dev/sdb1
[mntent]: warning: no final newline at the end of /etc/fstab
mount: /dev/sdb1 already mounted or /media/disk busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/disk

```

Sorry, I didn't see your post.

That means your drive is already mounted.  Use the file browser to go to /media/disk, and you should see the disk already mounted.

---

### Post by mgmiller on 2007-06-22
> There is a way to get it to automount upon startup, but it involves editing /etc/fstab. I'm not sure if ubuntu has a GUI utility to make it easier, as I'm used to doing it manually through the command line in Debian.


This may be a little late in this thread as it seems his drive is now mounted and accessible, but there is a nice GUI for setting mount points for drives.  It does all the changes to fstab.  It's called pysdm.   You can just apt-get it or use synaptic.  It will show up in System > Administration > Storage device manager.  Between gparted and pysdm you can handle this sort of stuff without having to drop to CLI.  (I know CLI is faster if you know what you're doing, but the GUI is easier for noobies).

---

### Post by Hranj on 2007-06-22
ok so i just did all of that and now it shows up under df -k but for some reason im still not allowed to write to the drive, i dont have any rights or anything. this is a big problem cause its the reason i put in a second hdd as is the reason why anyone would

also, i dont know if this is how its supposed to be, but when i go into my places menu at the top it comes up as /mnt/drive and in the computer window it still comes up as 9.5 gb volume: /mnt/drive and i have the option to unmount it. is it right like this?

---

### Post by EagleRock on 2007-06-22
Thanks mgmiller!

I don't really know the GUI side of disk managment, as Ubuntu is only a recent addition to my Linux experience.  I learned most of what I know from pure CLI managment of a Solaris UNIX enterprise server and my personal Debian server.   I'm sure that tool will help Hranj a lot more than the CLI, especially when he wants to start editing /etc/fstab...

---

### Post by EagleRock on 2007-06-22
> **Hranj said:**
> ok so i just did all of that and now it shows up under df -k but for some reason im still not allowed to write to the drive, i dont have any rights or anything. this is a big problem cause its the reason i put in a second hdd as is the reason why anyone would

also, i dont know if this is how its supposed to be, but when i go into my places menu at the top it comes up as /mnt/drive and in the computer window it still comes up as 9.5 gb volume: /mnt/drive and i have the option to unmount it. is it right like this?

Hmm...that's strange...I think you might not have rights because this was from a different Ubuntu install and the files are owned by a different user.

Was this the previous primary drive of another Linux install?  If you're not going to use it for that capacity anymore, you might want to just chown all the files on the drive to your user account on your current install.

Give me the results of this:

```

cd /mnt/drive
ls -l

```

I can tell from there what you need to do.  Chances are you're going to need to do:

```

sudo chown -R username /mnt/drive

```

DON'T do that until you paste the results of that ls, tho...

---

### Post by purdticker on 2007-06-22
I just installed Linux and my second hard drive is already mounted.  Where is it mounted by default in Ubuntu.  I can click on it through GUI I just don't know where it is in terminal.  Is there a command that will show it?  I don't see it listed in fstab.

---

### Post by Hranj on 2007-06-22
```
dhranj@dhranj-desktop:/mnt/drive$ ls -l
total 16
drwx------ 2 root root 16384 2007-06-21 19:13 lost+found
```

---

### Post by purdticker on 2007-06-22
Ok, cool, so how do I change that?  What if I want to name it /mnt/hdb1?

---

### Post by Hranj on 2007-06-22
o sorry i didnt see that post i was replying to eagle rock about his chown post. im not sure what the commmand in the terminal would be it might be best to get a response from eagle rock on that one

---

### Post by EagleRock on 2007-06-22
> **purdticker said:**
> I just installed Linux and my second hard drive is already mounted.  Where is it mounted by default in Ubuntu.  I can click on it through GUI I just don't know where it is in terminal.  Is there a command that will show it?  I don't see it listed in fstab.

/etc/fstab is only a list of filesystems that are configured to be set up at boottime.  If you want to see what is currently set up, use "df -k" or check /etc/mtab.

> **Hranj said:**
> ```
dhranj@dhranj-desktop:/mnt/drive$ ls -l
total 16
drwx------ 2 root root 16384 2007-06-21 19:13 lost+found
```

Okay, the problem is a permissions issue.  I'm not sure what you're using this Linux install for, but you may want to do one of two things:

1) Make a folder in the drive that your user can write to and give it permissions for your account
2) Make the entire drive usable for specifically your user.

Option 1 can be done like this:

```

cd /mnt/drive
sudo mkdir /myfolder
sudo chown user:group myfolder
sudo chmod 755 myfolder

```

You can name /myfolder whatever you want.  user is your username, your group is probably the same.

Option 2 is done like this:

```

sudo chown user:group /mnt/drive
sudo chmod 755 /mnt/drive

```

Again, user:group is your username twice.  For example, "sudo chown eaglerock:eaglerock /mnt/drive" would do it for my username.

---

### Post by Hranj on 2007-06-22
on the slave drive there used to be an ubuntu 6.06 install. i wiped that out when i formatted it or at least i thought i did.

on the current computer there is only one user name, mine, so im gonna go ahead and do option two and ill let you know how that turned out a little later. thanks a lot for your help eaglerock

---

### Post by Hranj on 2007-06-22
> **EagleRock said:**
> /etc/fstab is only a list of filesystems that are configured to be set up at boottime.  If you want to see what is currently set up, use "df -k" or check /etc/mtab.



Okay, the problem is a permissions issue.  I'm not sure what you're using this Linux install for, but you may want to do one of two things:

1) Make a folder in the drive that your user can write to and give it permissions for your account
2) Make the entire drive usable for specifically your user.

Option 1 can be done like this:

```

cd /mnt/drive
sudo mkdir /myfolder
sudo chown user:group myfolder
sudo chmod 755 myfolder

```

You can name /myfolder whatever you want.  user is your username, your group is probably the same.

Option 2 is done like this:

```

sudo chown user:group /mnt/drive
sudo chmod 755 /mnt/drive

```

Again, user:group is your username twice.  For example, "sudo chown eaglerock:eaglerock /mnt/drive" would do it for my username.

ok i performed option two and everything is good. since its a hdd basically just for music i made a multimedia folder and i have sudo rights inside of that folder i guess. thanks everyone

---

