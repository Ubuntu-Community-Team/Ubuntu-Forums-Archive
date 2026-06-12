---
title: "SOS Permission Emergency, HELP!!!"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-05-17
HI,

I have to take a CD of photos for my daughter's school project.

She does not have permission to write.

I wanted to copy her files to my desktop and then make a CD

she put them on a pendrive too..

I cannot into the pendrive... it says file owner ancsi. group ancsi?

1. so how the hell did she copy fiels to the pendrive adn in doing so lock the rest of us out of the pendrive?


2. how do I give her permission to make CDs?

3. How do I giv emyself permission to access everything, everywhere?

We a bit les sthan an hour to get this done or it will be too late.

Thanks

Robi

---

### Post by Thingymebob on 2007-05-17
this is not clever so take care:
in a terminal enter:
```
sudo nautilus
```
this will open the file manager as root user so you can copy the files to your profile and burn the cd

---

### Post by mbradlcu on 2007-05-17
Hi, 
I hate to answer a post with more questions but,
what file system is the pen drive using?
sudo fdisk -l
and how is it mounted:
mount
if it's ntfs you still should be albe to read from it.
can you change permissions on the files on the usb drive?
chmod 666 /media/usb{somthing}

if you can copy the files to her ~/ dir then you should be able to change the premissions so she can read and write to them with the chmod command.

hope this helps!

---

### Post by beanco on 2007-05-17
so i tried the first idea, the sudo nautilus

i was able to copy as root to the cd... but now i cannot access the CD

I could copy as root to my ~ but then i could not copy from there to the CD!!!!

the file system of the compute is ext or sg similar.

what is strange is we have all used pendrives with no problems. my son used this one in question now. then my daugheter, and now it says my daughter has permission only


the cd with teh pics on it... if we take it to a place to have prints made will they also not be able to read the disc?


this is all so confusing.. i know in the end I will be the better for it since I will learn sg but having a duaghter not be able to turn in her project because she cannot print the pictures because of stuff like this makes me want to go back to MS XP

robi

---

### Post by beanco on 2007-05-17
so, i thought i would try it again,

i entered sudo nautilus. copy file to my profile it went there just fine but it has a little lock icon on it and when I try to open it it says I do not have access...


robi

---

### Post by beanco on 2007-05-17
> **mbradlcu said:**
> ... 
sudo fdisk -l
and how is it mounted:
mount
hope this helps!


so i ran the above and got this

> Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14405   115708131   83  Linux
/dev/hda2           14406       14593     1510110    5  Extended
/dev/hda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 1028 MB, 1028653056 bytes
16 heads, 32 sectors/track, 3924 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3924     1004528    e  W95 FAT16 (LBA)
robi@robi:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/sda1 on /media/UDISK 2.0 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1002,gid=1002,umask=077,iocharset=utf8)

but  i guess i ran the wrong code because that is the info from my hard drive, not my pen drive, if I am not mistaken...

robi

---

### Post by kvonb on 2007-05-17
open a terminal, cd to the folder that the files are in and issue this command:

sudo chmod 777 *

BE CAREFUL!!!!!  MAKE SURE YOU ARE IN THE CORRECT FOLDER FIRST!!!!

That will make them read/write to everyone!

For cd-writer access, look on the menu under system->administration->users & groups.  Make sure that you have permission in there!

Your daughter might have used used a sudo nautilus to copy, or she is being a very bad Linux-ian and is logged on as root!

---

### Post by beanco on 2007-05-17
> **kvonb said:**
> open a terminal, cd to the folder that the files are in and issue this command:

like this?

 ```
cd ~ robi:/home/ancsi/desktop/eves munka
```

then i get this

```
robi@robi:~$
```

is that correct?

so now I can try this?

```

sudo chmod 777 *

```

```
BE CAREFUL!!!!!  MAKE SURE YOU ARE IN THE CORRECT FOLDER FIRST!!!!
```

being a neophyte and not sure of myself I have decided to ask for help with eachstep!

I assume if I were to do the above to the wrong folder everybody would have access to the folder that could be private/secret whatever.




```
For cd-writer access, look on the menu under system->administration->users & groups.  Make sure that you have permission in there!

```

well when I checked this all users had all permissions ACCEPT executing administrative....


```
Your daughter might have used used a sudo nautilus to copy, or she is being a very bad Linux-ian and is logged on as root!

```


she has not idea what root is, how to get there, what temrinal is, nothing

she just uses oo writer to write texts and firefox and epiphany to search the net and vlc to wathc dvds.


robi

---

### Post by beanco on 2007-05-17
not quite sure what happened.

i got the cd burned... form my desktop.. uh, i mean profile. but i noticed that I some how changed the ownershipof the pendrive to root and I cannot access it from other places..

what's up with that?

robi

---

### Post by mbradlcu on 2007-05-17
Hi,
when you copy 'cp' files the take ownership of the user that's copying them. my guess is when you were using 'sudo natulis' that's how the files became owned by root. Another command you'll like is the 'chown' command, eg:
chown {your_daughters_username} {file_to_change_ownership_of}

---

### Post by Delkster on 2007-05-17
The pendrive is, according to the mount output, formatted as vfat, which doesn't support file access control, so file ownership and permissions aren't preserved over unmounts and remounts. However, they're enforced as long as the drive is mounted even though they can't be stored onto the drive itself.

I assume what happened was this:
1. Your daughter is logged in and plugs in the pendrive. It's mounted with her user as the owner.
2. She copies the files over to the pendrive. Their ownership is assigned to her and will be enforced as long as the drive is mounted.
3. You log in under your account. The pendrive is still mounted. The files are still owned by your daughter.

If you unmount the drive between steps 2 and 3 and remount it after step 3 the file ownership and permissions aren't preserved (because the vfat filesystem can't store them), so when the pendrive is mounted again under your user account, you as the mounter become the "owner" of the files (and that, again, is only enforced until the drive is unmounted again).

Just trying to explain things a little. If you did things in a different way and I guessed it all wrong, please ignore.

---

### Post by beanco on 2007-05-18
hi there mbradlcu,

> **mbradlcu said:**
> Hi,
when you copy 'cp' files the take ownership of the user that's copying them. my guess is when you were using 'sudo natulis' that's how the files became owned by root. Another command you'll like is the 'chown' command, eg:
chown {your_daughters_username} {file_to_change_ownership_of}


so what is *cp*? copy? I copied the files in midnight commander because i sort of know how that works.

in terminal if I type 

```
cp ancsi/desktop/eves munka robi/desktop/eves munka  
```

will it be copied to my profile?


of if I type

```
chown ancsi/desktop/eves munka robi
```

the ownership will be changed to me?

now how then would i get the pendrive out of root?
I just want the pendrive to be used by everybody!

I do not want to worry about it at all.. and this is how we have been using the other pendrives... whoever needed to just saved their work on it and took it with them...

BTW, if i were to put the pendrive in a different comuter, say one with XP or KDE would the ownership iseus show up there too?

robi

---

### Post by beanco on 2007-05-18
> **Delkster said:**
> 
I assume what happened was this:
1. Your daughter is logged in and plugs in the pendrive. It's mounted with her user as the owner.
2. She copies the files over to the pendrive. Their ownership is assigned to her and will be enforced as long as the drive is mounted.
3. You log in under your account. The pendrive is still mounted. The files are still owned by your daughter.


that is most likely what happened... i was unaware of this mounting unmounting thing. so I have never told the kids.. Ancsi, my daughter most likely just pulled the pendrive out..

when messing round with the suggestions yesterday I somehow ended up messing things up agian..

now I cannot access the pen drive at all..
when I checked the permissions i see this

file user robi
file group root

how did i end up as root? how do i

1. get back to being robi@robi? I asusme robi@root is not very safe.. i guess i could end up doing amgae since I know nil about this computer stuff...

2.what should i now do with the pendrive? just pull it out? 

robi

---

### Post by steve.horsley on 2007-05-18
I think Delkster is exactly right. Look at this from the mount command:
> /dev/sda1 on /media/UDISK 2.0 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1002,gi d=1002,umask=077,iocharset=utf
The pendrive is mounted with uid=1002, telling you that user 1002 is the owner of the files (the whole drive). I bet this is your daughter's ID. Manage Users and Groups will confirm. It is also mounted umask=077 which means only the owner can read/write the drive. 

I have tested, and found that when you insert a pendrive, it always gets mounted as being owned by the user on the console. This makes sense to me - the user currently on the console os probably the person that plugged the stick in. When you logout and someone else logs in then, it helps to remove and re-plug the USB stick. This is all part of using a true multi-user OS. I wonder how Vista copes with this situation, now that MS is trying to make Windows a multi-user OS.

---

### Post by beanco on 2007-05-18
yes, 

I think 1002 is my daughter.

but now the pendrive is owned by root...


so how do i change that?

and, yeah, it makes great sense to me that the one using it is the owner, from what I can tell by testing with another pen drive is that if you mount/unmount it should be fine for everybody to use the pdrive... 


robi

---

### Post by Najand on 2007-05-18
Can you copy and paste your /etc/fstab file here?

---

### Post by beanco on 2007-05-18
> **Najand said:**
> Can you copy and paste your /etc/fstab file here?

here you go


```
robi@robi:~$ /etc/fstab
bash: /etc/fstab: Permission denied
```


so what to do now?

robi

---

### Post by steve.horsley on 2007-05-18
> but now the pendrive is owned by root...
I don't know how that could happen. Does the /media/USBwhatever directory still exist when the drive is unplugged? I don't think it should. Mine disappears when I eject the stick. If yours still exists, try renaming it (needs sudo) and then try plugging the stick in again.

---

### Post by Najand on 2007-05-18
```

$ cat /etc/fstab

```

---

### Post by beanco on 2007-05-18
steve, no the icon is not there if I remove the drive. but if I try to acces the drive from any of the other users i am denied access.


najand


```
robi@robi:~$  cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
robi@robi:~$
```

robi

---

### Post by Najand on 2007-05-18
OK, Let us go with the fast way:
First unmount it:
```

sudo umount /dev/sda1

```
Make a directory at media like pendrive.
Run this in the terminal:
```

sudo mkdir /media/pendrive

```
Then edit your fstab file:
```

sudo gedit /etc/fstab

```
And add the following to it:
```

/dev/sda1       /media/pendrive          vfat        defaults,users,rw     0     0

```
And then try to mount it by:
```

sudo mount /media/pendrive

```
and see if it works or not?

---

### Post by beanco on 2007-05-18
I ran this

> **Najand said:**
> OK, Let us go with the fast way:
First unmount it:
```

sudo umount /dev/sda1

```


and got this

> robi@robi:~$ sudo umount /dev/sda1
umount: /dev/sda1: not found
 
so i guess i cannot try the next steps.

robi

---

### Post by Najand on 2007-05-18
It is ok... Ignore that step and continue.

---

### Post by beanco on 2007-05-18
well i went ahead and trie dthe rest and go tthis


> mount: special device /dev/sda1 does not exist

where shoudl I have added the line to the fstab? I jus tstuck it in at the bottom, using copy and paste...

robi

---

### Post by Najand on 2007-05-18
Hmm.... Let me look at your fdisk -l and I will reply you in a second.

---

### Post by Najand on 2007-05-18
OK... When editing fstab add:
```

/dev/sda       /media/pendrive          vfat        defaults,users,rw     0     0

```
And save it and continue. See if this one works or not?

---

### Post by Najand on 2007-05-18
Any result?

---

### Post by beanco on 2007-05-18
Najand,

I tried the fstab again... i got it opened and added what you said to the end, hit save, closed the file and did this


```
robi@robi:~$ sudo gedit /etc/fstab
Password:
robi@robi:~$ sudo mount /media/pendrive
mount: special device /dev/sda1 does not exist
robi@robi:~$

```


robi

ps... could it matter that the pendrive had been removed and put back in earlier today or that there is another pendrive in at the moment, making that two pdrives now...
but the second, BTW works just fine.

robi

---

### Post by Najand on 2007-05-18
> **beanco said:**
> Najand,

I tried the fstab again... i got it opened and added what you said to the end, hit save, closed the file and did this


```
robi@robi:~$ sudo gedit /etc/fstab
Password:
robi@robi:~$ sudo mount /media/pendrive
mount: special device /dev/sda1 does not exist
robi@robi:~$

```


robi

ps... could it matter that the pendrive had been removed and put back in earlier today or that there is another pendrive in at the moment, making that two pdrives now...
but the second, BTW works just fine.

robi

Yeah, it might be the reason. So, give me the output of following commands now and please don't remove USB pendisks:
```

$ sudo fdisk -l 
$ mount
$ cat /etc/fstab

```

---

### Post by beanco on 2007-05-18
```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14405   115708131   83  Linux
/dev/hda2           14406       14593     1510110    5  Extended
/dev/hda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/sdc: 1015 MB, 1015021568 bytes
33 heads, 63 sectors/track, 953 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         954      991216    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(215, 32, 63) logical=(953, 18, 43)
```


then for

```
$ mount
```

i got

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)

```

followed by

```
robi@robi:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/pendrive          vfat        defaults,users,rw     0  0
dev/sda       /media/pendrive          vfat        defaults,users,rw     0     0robi@robi:~$
```

what does this tell you?
and again, thanks!!!

robi

---

### Post by Najand on 2007-05-18
OK... It seems you use different USB pendrives... So let us stop changing fstab...
First use:
```
sudo gedit /etc/fstab
```
and remove last two lines.
Then try the following command in the terminal:
```
sudo mount -t vfat -o users /dev/sdc1 /media/pendrive
```
and see if you have access to the files there or not?

---

### Post by beanco on 2007-05-18
the last two lines were the once i added..

removed them 

ran what you said

got this

```
robi@robi:~$ sudo mount -t vfat -o users /dev/sdc1 /media/pendrive
mount: special device /dev/sdc1 does not exist
```

and yes, i have two different pendrives .... would it help if i remove the one that works correctly?

robi

---

