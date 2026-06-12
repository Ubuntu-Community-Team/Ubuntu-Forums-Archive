---
title: "Having troubles getting a new partition to work."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by astrogiblet on 2007-01-18
Backstory -

Originally, I was going to dual boot this laptop, but since I got Ubuntu working so nicely, I decided over it. Which meant that my 60 gig partition that I was going to use for Windows needed to be turned into a storage drive for my Ubuntu installation. 

So I apt-get gparted, it installed just fine. I used it to make the 60 gig partition into an ext3 partition, and realize its not going to be automatically mounted. So I go through the trouble of getting it to recognize (a friend walks me through this) adding it to my fstab file, and everything is fine.. 

But now I dont have permission to use it. I can't read/write, or even open any folders in it.. How do I gain permissions over this drive? 

I can sudo umount and sudo mount it, but I cannot access anything no matter what I do. 


Thanks for the help,


-Brandon

---

### Post by riven0 on 2007-01-18
Not sure if it'll work, but it doesn't hurt to try:

> sudo chmod a+x /dev/hdXY

Replace the XY with your drive's letter and number. Maybe that'll work.

---

### Post by astrogiblet on 2007-01-18
Hmm.. that didnt work. :(

Thanks for the try though. 


-Brandon

---

### Post by riven0 on 2007-01-18
One more thing to try: wherever you drive is mounted, (like /media/drive for example), do:

> sudo chmod 777 /path/drive

---

### Post by oracle5 on 2007-01-18
I had the same problem before and what I did was create a group in system>administration>Users and groups. Say the group is named disktwo and then I added my user name to the group.  Then I went in the terminal and typed "sudo nautilus --no-desktop" without the quotes, and then navigated the mount point which was in /media for me and changed the permissions on the folder that represented the disk so that group disktwo had read write access.

I tried to do it by just giving my user name rights but that didn't work and that's when I came up with this solution.

oracle5

---

### Post by bodhi.zazen on 2007-01-18
> **riven0 said:**
> One more thing to try: wherever you drive is mounted, (like /media/drive for example), do:

This will work, make sure the partition is mounted first though.

You can also, again with the partition mounted, chown

chown user:group <mount_point>

For example, againusting the mount point of /media/drive:
```
sudo mount /media/drive
sudo chown root:users /media/drive
sudo chmod 770 /media/drive
```

The first command was to mount the partition and can be skipped if you have already mounted it :p

HTH

---

### Post by astrogiblet on 2007-01-18
I've tried everything stated above, and yet it still doesnt work. 

Why does this even happen? I'm a new-to-linux user, and I can't see any reason why when I make a new partition its not accessible from the start. 

I was just beginning to think Linux was easier then what everybody says.. 


-Brandon

---

### Post by oracle5 on 2007-01-18
Even with this its still easier than what people say. I've met people that think linux is all command line and that you have to be a genius to run it. That's when I hand them a livecd.

oracle5

---

### Post by bodhi.zazen on 2007-01-18
> **astrogiblet said:**
> I've tried everything stated above, and yet it still doesnt work. 

Why does this even happen? I'm a new-to-linux user, and I can't see any reason why when I make a new partition its not accessible from the start. 

I was just beginning to think Linux was easier then what everybody says.. 


-Brandon

Well, perhaps if you gave some more information.

What partition are you trying to work with ? /dev/hd??

What is the mount point? /media/???

What are the current ownership and permissions ?

```
la -l /media
```

Is the partition mounted ?

And last, what is your fstab entry ?

---

### Post by astrogiblet on 2007-01-18
> **bodhi.zazen said:**
> Well, perhaps if you gave some more information.

What partition are you trying to work with ? /dev/hd??

What is the mount point? /media/???

What are the current ownership and permissions ?

```
la -l /media
```

Is the partition mounted ?

And last, what is your fstab entry ?



/dev/sda2

/mnt/Storage

Current ownership is set to my name and my group, with read, write, etc. permissions. 

The partition is mounted, as it shows up when I do "df -h". la gives me an error, saying its not a command. 

My fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2       /mnt/Storage    ext3    defaults        0     1




-Brandon

---

### Post by bodhi.zazen on 2007-01-18
> **astrogiblet said:**
> /dev/sda2

/mnt/Storage

Current ownership is set to my name and my group, with read, write, etc. permissions. 

The partition is mounted, as it shows up when I do "df -h". la gives me an error, saying its not a command. 


-Brandon

oops, typo there :redface:

Did you know the a key is next to the s ?

Could you post the output of:

```
**ls** -l /mnt
```

and:

```
touch /mnt/Storage/test
ls -l /mnt/Storage
```

Those are small "L's" and not the number 1 ;)

8)

---

### Post by astrogiblet on 2007-01-18
Heres a direct copy of it: 

> astrogiblet@astrogiblet-laptop:~$ ls -l /mnt
total 4
drwxrwxrwx 3 astrogiblet disktwo 4096 2007-01-17 22:09 Storage
astrogiblet@astrogiblet-laptop:~$ touch /mnt/Storage/test
astrogiblet@astrogiblet-laptop:~$ ls -l /mnt/Storage
total 16
drwx------ 2 root        root        16384 2007-01-17 22:09 lost+found
-rw-r--r-- 1 astrogiblet astrogiblet     0 2007-01-18 14:51 test


So it appears as thought it made a test file just fine? Now its allowing me to create files if I right click, but I still can't access the lost + found folder.. is that normal? 


Thanks for the help!


-Brandon

---

### Post by bodhi.zazen on 2007-01-18
Yep, all seems well with your partition :p

Lost & Found is owned by root.

you can access it if you ```
gksudo nautilus
```

Or from a terminal if you change to root:

```
sudo -i
```

HTH and happy partitioning :p

Oh, and if you like you can:```
rm /mnt/Storage/test
```

---

### Post by astrogiblet on 2007-01-18
Hey thanks a lot for the help. 


-Brandon

---

