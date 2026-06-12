---
title: "Hard Drive Troubles"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by jtccjt on 2006-12-01
Hello!

I am new Linux.  I can solve windows problems, but I haven't felt my way around Linux enough to know much of anything.  

Here is some info on my setup:
- Ubuntu 6.10
- 3 hard drives: Windows(80G), Data (250G), Ubuntu (80G) All SATA drives.

I want to have the data HD (250g) to be accessible to both OS's.  I am willing to have it in NTFS or an EXT format.  I've scanned all kinds of threads here but none of them helped me.  Right now I have it formatted with NTFS.  I've seen several mention GParted but I do not have that program nor can I find it with the add/remove under applications.  

After hours of searching I got the drive mounted, but when I tried to access it told me that I did not have permissions.  

Thank you so much for your help!

Josh

---

### Post by milton1 on 2006-12-01
You can mount and read ntfs from linux, but not write. (at least, not without much fiddling and instability) If you format the drive to fat32, both systems can have full access to it.

---

### Post by jtccjt on 2006-12-01
I believe that with FAT you can't have a file over 4GBs.  I do some multimedia stuff from time to time.  

Also, in Windows the only option it gave me was NTFS when I wanted to format it and I don't know how to format a disk in Ubuntu yet.

---

### Post by Hankers on 2006-12-01
This may or may not help you with your issue. Using the instructions there I had no problems with accessing info on an NTFS     drive.
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

---

### Post by jtccjt on 2006-12-01
I got lost on that site when I get to this command

```
sudo cp /ect/fstab ect/fstab_backup
```

I then get

```
 cp: cannot stat `/ect/fstab': No such file or directory

```

If I just skip that step and go to ```
 sudo nano /ect/fstab 
```

I get a text program that comes up where the whole screen is blank except the top and bottoms on the window- not what is on the site.

---

### Post by jtccjt on 2006-12-01
I do have a fstab file.  When I go to /ect and open fstab in the file browser this is what the file looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=77923007-dede-4df8-892f-479b947a0acd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=c6a50049-cad5-4f54-a959-ce1a51bdf9d0 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by scc4fun on 2006-12-01
I believe it should be **/etc**/fstab instead of **/ect**/fstab

---

### Post by jtccjt on 2006-12-01
> **scc4fun said:**
> I believe it should be **/etc**/fstab instead of **/ect**/fstab

I feel kind of silly asking this, but what is the difference?

---

### Post by Hankers on 2006-12-01
You left out a '/' before the second etc - sudo cp /ect/fstab ect/fstab_backup should have been sudo cp /ect/fstab /ect/fstab_backup in order to make a backup file of fstab

You need to find out how your NTFS drive is listed by using the sudo fdisk -l in terminal. That will allow you to put in the correct hda? line in the fstab file such as /dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0

---

### Post by jtccjt on 2006-12-01
Ok,

```
josh@josh:~$ sudo cp /ect/fstab /ect/fstab_backup
cp: cannot stat `/ect/fstab': No such file or directory

``` 

As you can see it gave the same thing.  :(

I did sudo fdisk -l 
```
Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706    7  HPFS/NTFS

```
is the HD I want.

---

### Post by Hankers on 2006-12-01
Then you should be able to add the line (on it's own line )in the fstab file - /dev/sdb1 /windows ntfs nls=utf8,umask=0222 0 0   and save the file.
(remember to add a space after 0222 and between the 0 0 )

Finally, when you exit the file and return to the terminal type :

sudo mount -a

If all went well your NTFS drive should appear under the file system Windows folder.

Remember it is read only!

---

### Post by jtccjt on 2006-12-01
I can't edit the fstab file.  I can't even make a backup of the file.  It gives an error (above post) when I try.  When I use 'sudo nano /ect/fstab' it opens the editor and it is completely empty.  If I type in what you said (in that blank file) and try to exit and save it tells me that the file doesn't exhist.

---

### Post by jtccjt on 2006-12-01
In all honesty, I would like to be able to write/read the drive from both OpS.  Would it be best to reformat the drive to another format?  If so, can someone tell me how?

---

### Post by skinny on 2006-12-01
> Ok,

Code:

josh@josh:~$ sudo cp /ect/fstab /ect/fstab_backup cp: cannot stat `/ect/fstab': No such file or directory

As you can see it gave the same thing. 

^i think that should be **etc** not ect (in both places):

sudo cp /**etc**/fstab /**etc**/fstab_backup

$

---

### Post by gagatz on 2006-12-01
I think it is a little lexical thing, look out what you are writing

/eCt or /eTc see the difference? Note that the second and the third letter interchanged!

The fstab is located at /etc!

Type

sudo cp /etc/fstab /etc/fstab_backup

---

### Post by jtccjt on 2006-12-01
> **skinny said:**
> ^i think that should be **etc** not ect (in both places):

sudo cp /**etc**/fstab /**etc**/fstab_backup

$
 Anyone have a hole I can hide in?  I feel silly now!

---

### Post by Hankers on 2006-12-01
The only way that I know of to read/write to a drive using both OS's would be if the drive was formatted FAT32. I'm not sure what the limitations for drive size are in FAT32.

Hopefully you have the etc instead of ect worked out now and can make a backup of the fstab file and edit it to add the line as previously mentioned.

---

### Post by jtccjt on 2006-12-01
Yay! I've learned how to mount a drive.  I have one more question...

I would like to be able to write and read to the drive from both OS.  Should I format it to EXT3 format?  

How do you format a drive in ubuntu?

Thanks you everyone!

---

### Post by jtccjt on 2006-12-01
> [quote]Hopefully you have the etc instead of ect worked out now and can make a backup of the fstab file and edit it to add the line as previously mentioned.

Yes.  :D 

I seen a website ([http://www.fs-driver.org/](http://www.fs-driver.org/) ) that you can read ext2 and ext3 on windows.

---

