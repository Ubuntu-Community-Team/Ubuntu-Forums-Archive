---
title: "help accessing ntfs partition plz"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by krajni on 2007-01-04
I am new to linux and have been directed here by a friend....anyway i have a ntfs partition (hda6) that contains nothing but music.....i would like to access that through ubuntu....my friend tells me that to do so i have to use the terminal to mount the logical drive before i can access it and unmount it when i'm done, but he doesnt know the commands to use because he is a slackware man (whatever idk much about the difference).......i understand what he is telling me so u dont have to go all kindergarten on me...i just wanna know the command line i need to enter to mount  said drive and the command to unmount it.......and do i have to run terminal as the root user to do so?

all help appreciated

ps     do i need an additional program to read .mp3  format files?

---

### Post by hyby on 2007-01-04
Usually, once you install ubuntu; it detects the logical drives on your computer and automounts them everytime you boot into ubuntu.

---

### Post by Phesto on 2007-01-04
you will need a directory created to mount the hd in
for example mkdir /media/musicHD
after that, the command would be
sudo mount /dev/hda6 media/musicHD

the sudo takes care of the root question

i would suggest using XMMS to play the mp3s

if you wanted to have the partition automount you can edit your /etc/fstab file

---

### Post by Cariboo1938 on 2007-01-04
> **krajni said:**
> I am new to linux and have been directed here by a friend....anyway i have a ntfs partition (hda6) that contains nothing but music.....i would like to access that through ubuntu....my friend tells me that to do so i have to use the terminal to mount the logical drive before i can access it and unmount it when i'm done, but he doesnt know the commands to use because he is a slackware man (whatever idk much about the difference).......i understand what he is telling me so u dont have to go all kindergarten on me...i just wanna know the command line i need to enter to mount  said drive and the command to unmount it.......and do i have to run terminal as the root user to do so?
all help appreciated
ps     do i need an additional program to read .mp3  format files?Welcome to the Forum, welcome to the Ubuntu family:
Try this, [HERE ]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=NTFS") you should find all information needed! 
Good Luck

---

### Post by CroEragon on 2007-01-05
> **hyby said:**
> Usually, once you install ubuntu; it detects the logical drives on your computer and automounts them everytime you boot into ubuntu.

In my experience Ubuntu NEVER automount NTFS drives. That what scared me in Ubuntu when i first booted it from LiveCD. In Knoppix it works great, in Ubuntu doesn't at all.
Anyway, you can use thread linked above but it looks scary from point of newbie. If you want easier tutorial you can use [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#windows") (just read access, not write) or [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")(read and write, uses beta sowtware maybe won't work)
If you can't mount it with any of this two links than use thread.

---

### Post by Zzl1xndd on 2007-01-05
from my install it is automounting both of my NTFS drives no issue at all.

---

### Post by krajni on 2007-01-05
OK so i figured out my friend is an idiot and really knows nothing about linux......they did automount, i just dont have access to them (which explains why they are on my desktop :-?  ) , but thanks for all the resources i am finding them useful for other things.......real quick though....how do i access my ntfs partions without logging in under root....can i set it up so my basic user name always has access to all hard drive partitions?

---

### Post by bodhi.zazen on 2007-01-05
> **krajni said:**
> OK so i figured out my friend is an idiot and really knows nothing about linux......

What took you so long ? I'm sure your friend is knowledgeable in some ways ;)

> they did automount, i just dont have access to them (which explains why they are on my desktop :-?  ) , but thanks for all the resources i am finding them useful for other things.......real quick though....how do i access my ntfs partions without logging in under root....can i set it up so my basic user name always has access to all hard drive partitions?

You have to edit fstab

In a terminal type```
gksudo gedit /etc/fstab
```

Enter your password.

Change the line with your ntfs partition to something like:> /dev/hda1  /media/windows  ntfs  auto,users,umask=222  0  0

This will give you ro access. For rw access see Cariboo1938's link above.

---

### Post by krajni on 2007-01-05
yeah ok u lost me a little.....and here is my terminal session

justin@ubuntu:~$ gksudo gedit /etc/fstab
(gedit:9333): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by bodhi.zazen on 2007-01-05
Did gedit open ? If so you can ignore the warning message ...

Otherwise try:

```
sudo nano -B /etc/fstab
```

nano is fairly user friendly .....

Go ahead and edit ....

Ctrl-X to exit, type Y to save your changes ....

The -B "flag" creates a backup of your original fstab /etc/fstab~

If you do not understand what to do, post the line from fstab with your ntfs partition ....

---

### Post by krajni on 2007-01-05
ok so i replaced 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda6       /media/hda6     ntfs    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


with....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda6       /media/hda6     ntfs    auto,users,umask=222        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



and it still tells me i do not have permission necessary to view contents...and root user still can not change the permissions because it is read only....

well no one said learning linux would be easy

---

### Post by bodhi.zazen on 2007-01-05
unmount and then re mount the partition:

```
sudo umount /media/hda6
mount /media/hda6
```

---

### Post by krajni on 2007-01-05
ok so  i replaced this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda6       /media/hda6     ntfs    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


with this.....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda6       /media/hda6     ntfs    auto,users,umask=222        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


and i still cant access the drive...it changed access for others (owned by root) to execute, but i still cant open it, how do change it to read ( owner and group permissions are already read)

---

### Post by krajni on 2007-01-05
oops...well anyway i not only unmounted remounted, i also rebooted....no still no read access for other than owner

---

### Post by bodhi.zazen on 2007-01-05
According to the man page you should be fine:

[http://www.die.net/doc/linux/man/man8/mount.8.html](http://www.die.net/doc/linux/man/man8/mount.8.html)

At any rate, can you post the output of:```
ls -l /media | grep hda6
```
(with the partition mounted)

Perhaps chmod:```
sudo chmod 555 /media/hda6
```
(with the partition mounted).

---

### Post by krajni on 2007-01-05
i agree according to that page it should work...unles he umask value should have been other than 222, i dont know and couldnt find a list of values for the permissions


output for first not gonna be of any help but here it is

bash: syntax error near unexpected token `|'

tried it twice typed exactly as u did

output of second

chmod: changing permissions of `/media/hda6': Read-only file system

---

### Post by jvc26 on 2007-01-05
Krajni: Just noticed you're a 5.10 user - any reason that you're using such an old distro? It may not help the whole drives issue?
Il

---

### Post by krajni on 2007-01-05
because i just got my hands on 5.10 disk from the pc repair shop where i work, and replaced the distro which i put on my machine over a year ago ( 5.0 or 5.02 sumthin like that) and never learned how to use

---

### Post by bodhi.zazen on 2007-01-05
> **krajni said:**
> i agree according to that page it should work...unles he umask value should have been other than 222, i dont know and couldnt find a list of values for the permissions


output for first not gonna be of any help but here it is

bash: syntax error near unexpected token `|'

tried it twice typed exactly as u did

output of second

chmod: changing permissions of `/media/hda6': Read-only file system

Try cutting and pasting the command (to eliminate typo')s

---

### Post by krajni on 2007-01-05
thxs but after reading bout it for hours  i added uid=100, gid=1000 to fstab and can access the hda6 now,.....but had to start a new thread cuz that opened another can o worms

---

