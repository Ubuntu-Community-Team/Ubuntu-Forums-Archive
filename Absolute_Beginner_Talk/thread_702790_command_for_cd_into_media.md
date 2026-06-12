---
title: "command for cd into media??"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2008-02-20
in terminal

am never sure of the difference between Media & "mnt"

am trying to "cd" into the directory of an external drive... (so I can change permissions)

it shows up on the desktop (it's mounted) as

Matrix 2_20 1

how do I cd into it ?

nothing seems to work :

will@will-linux:~$ cd /media/Matrix 2_20 1
bash: cd: /media/Matrix: No such file or directory

will@will-linux:~$ cd /mnt/Matrix 2_20 1
bash: cd: /mnt/Matrix: No such file or directory

the drive is formatted in Mac OS X, but I can't imagine that is the problem...

thanks

willfriedwald

PS: oh wait, am I NOT allowed to have a volume name with a space?  does the volume have to have underscores and no spaces in the name? could that be it?  should I change the volume name accordingly?

---

### Post by TheBoat on 2008-02-20
I could be wrong, but it looks like you have spaces in the filename.  Therefore, spaces need to be escaped(\) when referring to the file in the terminal.```
Matrix\ 2_20\ 1
```. cd into both directories and see what is in them. When you find Matrix, type Matrix and then hit [tab] to autocomplete.

EDIT: Sorry, I didn't notice that you already realized the spaces were the problem.

---

### Post by S15_88 on 2008-02-20
you can try using quotes around "Matrix 2_20 1"

---

### Post by spiderbatdad on 2008-02-20
I believe that is a mount point. You can't actually cd into a mount point. You can edit /etc/fstab and set the umask=000 for that device. I think you can also sudo chown - R username : group /media/Matrix 2_20 1/*

---

### Post by spiderbatdad on 2008-02-20
if it is a directoy, and on your desktop you need to add Desktop...so...cd Desktop/media/matrix...

---

### Post by willfriedwald on 2008-02-20
that seems to have worked !

however, then the commands which I thought would change the permissions for me did NOT work - 

here is what I tried

will@will-linux:~$ cd /media/Matrix\ 2_20\ 1
will@will-linux:/media/Matrix 2_20 1$ sudo find . -type d -exec chmod 777 {} \;
[sudo] password for will:
chmod: changing permissions of `.': Read-only file system
chmod: changing permissions of `./.Spotlight-V100': Read-only file system
chmod: changing permissions of `./.Trashes': Read-only file system
chmod: changing permissions of `./.Trashes/501': Read-only file system
will@will-linux:/media/Matrix 2_20 1$ sudo find . -type d -exec chmod 777 {} \;
chmod: changing permissions of `.': Read-only file system
chmod: changing permissions of `./.Spotlight-V100': Read-only file system
chmod: changing permissions of `./.Trashes': Read-only file system
chmod: changing permissions of `./.Trashes/501': Read-only file system
will@will-linux:/media/Matrix 2_20 1$ sudo find . -type f -exec chmod 666 {} \;
chmod: changing permissions of `./.DS_Store': Read-only file system
chmod: changing permissions of `./.journal': Read-only file system
chmod: changing permissions of `./.journal_info_block': Read-only file system
chmod: changing permissions of `./.Spotlight-V100/.journalHistoryLog': Read-only file system
chmod: changing permissions of `./.Spotlight-V100/.store.db': Read-only file system
chmod: changing permissions of `./.Spotlight-V100/_rules.plist': Read-only file system
chmod: changing permissions of `./.Spotlight-V100/ContentIndex.db': Read-only file system
chmod: changing permissions of `./.Spotlight-V100/store.db': Read-only file system
chmod: changing permissions of `./Desktop DB': Read-only file system
chmod: changing permissions of `./Desktop DF': Read-only file system
chmod: changing permissions of `./fsck.jfs :dev:matrix:main_matrix.txt': Read-only file system
will@will-linux:/media/Matrix 2_20 1$ 

what's the easiest command to change the permissions on a drive so I can write to it?

thanks!

w

---

### Post by S15_88 on 2008-02-20
you can do:
sudo chown -R username:username directory

---

### Post by willfriedwald on 2008-02-20
sudo chown -R username:username directory

what would that be in this case (sorry to be so dense?)

also : what would that be if I am already in the directory?

w

---

### Post by S15_88 on 2008-02-20
what i've always done is navigate to the directory i want to be in then: ls -al    to check the permissions.  then i do: sudo chown -R alain:alain /home/alain    
that would change the permissions of everything in that directory.  don't think it matters if you're in the directory because you still have to specify what directory to change the permissions of.

Thanks, Alain

---

### Post by willfriedwald on 2008-02-20
this seems to be the same - 

possibly I have to re-format the drive in gParted?  I want to re-format it in Mac OS X format so that my Mac can read it.  would that be HTFS+?  or what?


thanks!

w

will@will-linux:/media/Matrix 2_20 1$ sudo chown -R will:will /media/Matrix\ 2_20\ 1
chown: changing ownership of `/media/Matrix 2_20 1/.DS_Store': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.journal': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.journal_info_block': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.Spotlight-V100/.journalHistoryLog': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.Spotlight-V100/.store.db': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.Spotlight-V100/_rules.plist': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.Spotlight-V100/ContentIndex.db': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.Spotlight-V100/store.db': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.Spotlight-V100': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.Trashes/501': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/.Trashes': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/Desktop DB': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/Desktop DF': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1/fsck.jfs :dev:matrix:main_matrix.txt': Read-only file system
chown: changing ownership of `/media/Matrix 2_20 1': Read-only file system
will@will-linux:/media/Matrix 2_20 1$

---

### Post by spiderbatdad on 2008-02-20
the permissions are set when the device is mounted. so you want to change the umask in /etc/fstab to umask=000.

Maybe post your /etc/fstab

---

### Post by S15_88 on 2008-02-20
humm interesting not sure what the deal is perhaps  try chown --help and read into it.

---

### Post by willfriedwald on 2008-02-20
gParted doesn't seem to want to format it!'

what would be a way to format it in the terminal?

would like to format it as HTFS+ so a Mac can read it, and make it universally read & writable?

help!

thanks!

w

---

### Post by willfriedwald on 2008-02-21
quick question - what is the command to get terminal to display the contents of /etc/fstab ?

also: can someone think of a way to format a drive so that it can be read & written to in both linux-ubuntu AND mac os X?

for some reason, I can't re-format this drive(currently in Mac HTFS+) in gParted - gP doesn't give me the option of reformatting it...

thanks!

w

---

