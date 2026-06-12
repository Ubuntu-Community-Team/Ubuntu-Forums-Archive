---
title: "Want to mount 2nd HD.. options?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by FreakinSyco on 2006-10-27
I have 2 HDs in my system. HDA1 is a 1 gig swap HDA2 is my main ubuntu install. My second hard drive (HDB) I have formatted using gparted to FAT32. I want to mount it if possible in my home directory or have it appear as another drive in nautlius (like how HDA2 shows up with its own icon on the left as "file system".

So far I can mount it to any folder I want.. thats easy. But I cant get it to mount to a subfolder in my home directory or make it show as a second drive.

Suggestions?

---

### Post by chuckyp on 2006-10-27
Well just make the subfolder first mkdir ~/whatever    then just mount the drive to that.  mount -t vfat /dev/hdb1 ~/whatever   should work.

---

### Post by FreakinSyco on 2006-10-27
> **chuckyp said:**
> Well just make the subfolder first mkdir ~/whatever    then just mount the drive to that.  mount -t vfat /dev/hdb1 ~/whatever   should work.

Ok.. that got it mounted but I need to use sudo to move files onto it. I was hoping I could just use nautilus and drag and drop into it.

---

### Post by aysiu on 2006-10-27
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bodhi.zazen on 2006-10-27
> **FreakinSyco said:**
> Ok.. that got it mounted but I need to use sudo to move files onto it. I was hoping I could just use nautilus and drag and drop into it.

See if this helps: [How to fstab](http://ubuntuforums.org/showthread.php?t=283131)

Look at the bottom examples, just above referances.

---

### Post by punx45 on 2006-10-27
#nevermind

---

### Post by FreakinSyco on 2006-10-27
> **bodhi.zazen said:**
> See if this helps: [How to fstab](http://ubuntuforums.org/showthread.php?t=283131)

Look at the bottom examples, just above referances.

Ok I think I'm seeing what I need to do. Lets see if this make sense:

Current fstab for HDB1:

# /dev/hdb1
UUID=527C7EEF7C7ECCEB /mnt/BigDaddy     ntfs    
defaults,nls=utf8,umask=007,gid=46 0       1

First of all the disk is formatted as FAT32. Gparted says its fat32.. so should I change that?

Should it look something like this:

# /dev/hdb1
UUID=527C7EEF7C7ECCEB /mnt/BigDaddy vfat
defaults,nls=utf8,umask=007,gid=46 0 1 (<- whats all that saying/doing?)
drwxr-xr-x 7 freakinsyco adm

---

### Post by bodhi.zazen on 2006-10-27
That entry will work.

vfat is fine.

You could try the following options:

auto,users,gid=100,umask=007

Don't think it matters much.....

The 0 1 are explained in the link.

0 = back up on dump (a backup program)

1 = check file system.

---

### Post by FreakinSyco on 2006-10-27
With the following fstab:

# /dev/hdb1
UUID=527C7EEF7C7ECCEB /home/freakinsyco/Media vfat
defaults,nls=utf8,umask=007,gid=46 0 1
drwxr-xr-x 7 freakinsyco adm

I get the following error:

```
$ sudo mount -a
mount: special device /dev/disk/by-uuid/527C7EEF7C7ECCEB does not exist
mount: mount point 0 does not exist
mount: mount point 7 does not exist
```

It appears I have the incorrect UUID. So I did this listed my disks by UUID:

```
$ ls /dev/disk/by-uuid
00944f1b-45cd-4003-9f0b-084db74dfa44  c94dc2ca-1444-4c72-81aa-7c1188ae428a
4542-568B
```

Those 2 listings are for HDA1 HDA2 nothing listed at all for HDB1.

So I looked if it was in the ID listings:

```
$ ls /dev/disk/by-id
ata-SAMSUNG_SP4002H_0411J1FT301951
ata-SAMSUNG_SP4002H_0411J1FT301951-part1
ata-SAMSUNG_SP4002H_0411J1FT301951-part2
ata-SAMSUNG_SP8004H_0544J1FW326203
ata-SAMSUNG_SP8004H_0544J1FW326203-part1
```

yup.. there it is. But. In that fstab tutorial I dont see a way to list mounts by ID. only label which BTW when I attempt to get a list of my labels I get the following:

```
$ ls /dev/disk/by-label
ls: /dev/disk/by-label: No such file or directory
```

So would this work at all for an fstab:

# /dev/hdb1
ID=ata-SAMSUNG_SP8004H_0544J1FW326203-part1 /home/freakinsyco/Media vfat
defaults,nls=utf8,umask=007,gid=46 0 1
drwxr-xr-x 7 freakinsyco adm

So close to having this done. Thanks for the help so far!

---

### Post by bodhi.zazen on 2006-10-27
You can try, with 6.06 I could not get fstab to work with ID=....

Which partition are you trying to mount? hda1 or hdb1?

What is "4542-568B" under uuid ?

---

### Post by FreakinSyco on 2006-10-27
> **bodhi.zazen said:**
> You can try, with 6.06 I could not get fstab to work with ID=....

Which partition are you trying to mount? hda1 or hdb1?

What is "4542-568B" under uuid ?

Im trying to mount HDB1 to the Media folder within my home directory.

Doh you figured it out! that is the UUID for HDB1! I assumed it was a continuation from the first line. 

So now that we know the UUID this fstab:

```
# /dev/hdb1
UUID=4542-568B /home/freakinsyco/Media vfat
defaults,nls=utf8,umask=007,gid=46 0 1
drwxr-xr-x 7 freakinsyco adm
```

gives the following results:

```
$ sudo mount -a
mount: mount point 0 does not exist
mount: mount point 7 does not exist
```

That means were closer. The drive is indeed mounted to the Media folder in my home directory.. but once again I need to be root to write to it. im guessing it has something to do with this line:

```
defaults,nls=utf8,umask=007,gid=46 0 1
```

This drive was an NTFS drive before I formatted it to FAT32 and I think it is a reminance of that.

---

### Post by bodhi.zazen on 2006-10-27
What are those errors ?

At any rate, as root unmount the partition.

edit fstab and try these options:> auto,users,nls=utf8,umask=007,gid=46 0 0

remount the partition AS A USER, NO SUDO

```
mount /home/freakinsyco/Media
```

Also: Fine tuning: Change your mount point and create a link in /home.

**[size=4][color=red]Unmount the partition.**[/color][/size]
```
sudo umount /home/freakinsyco/Media
rm -R ~/Media
sudo mkdir /mnt/Media
ln -s /mnt/Media ~/Media
```

Now you can mount the partition with:```
mount ~/Media
```

Or, if you are in your home directory:```
mount Media
```

---

### Post by FreakinSyco on 2006-10-27
When you say edit the options you mean like so:

# /dev/hdb1
UUID=4542-568B /home/freakinsyco/Media vfat
auto,users,nls=utf8,umask=007,gid=46 0 0
drwxr-xr-x 7 freakinsyco adm

I understand mounting as user not root.. Makes sense.

The part about the link from /mnt/media to ~/media

That creates a folder in my home directory that acts as a short cut to the  /mnt/media folder, correct? So if I did that would I want to change my fstab to mount to /mnt/media/ instead of /home/freakinsyco/media ?

---

### Post by scott stanley on 2006-10-27
Well I've read this thread but the Q and A doesn't exactly apply to me. I have no problem mounting my second HDD using the "Disks" tool under administration. I can rwx everything on the drive. BUT I have to mount it every time I log in. I know this can't be the way it's supposed to be, can someone please enlighten me?
Thanks in advance...

---

### Post by FreakinSyco on 2006-10-27
> **scott stanley said:**
> Well I've read this thread but the Q and A doesn't exactly apply to me. I have no problem mounting my second HDD using the "Disks" tool under administration. I can rwx everything on the drive. BUT I have to mount it every time I log in. I know this can't be the way it's supposed to be, can someone please enlighten me?
Thanks in advance...

Are you running Edgy? I have no System > Admin > Disks and no option to enable it in the menu editor.

---

### Post by scott stanley on 2006-10-27
No, I'm running Dapper. System--->Administration--->Disks

---

### Post by bodhi.zazen on 2006-10-27
> **FreakinSyco said:**
> When you say edit the options you mean like so:

# /dev/hdb1
UUID=4542-568B /home/freakinsyco/Media vfat
auto,users,nls=utf8,umask=007,gid=46 0 0
drwxr-xr-x 7 freakinsyco adm

Yes. "UUID=4542-568B /home/freakinsyco/Media vfat
auto,users,nls=utf8,umask=007,gid=46 0 0" should be in fstab.

You can change gid=100 if you want the partition to bw owned by the users group instead of adm.

> I understand mounting as user not root.. Makes sense.

The part about the link from /mnt/media to ~/media

That creates a folder in my home directory that acts as a short cut to the  /mnt/media folder, correct? So if I did that would I want to change my fstab to mount to /mnt/media/ instead of /home/freakinsyco/media ?

Again, yes.

> UUID=4542-568B /home/freakinsyco/Media vfat auto,users,nls=utf8,umask=007,gid=46 0 0
(All 1 line)

This is not necessary, but keeps you scheme "traditional".

---

### Post by bodhi.zazen on 2006-10-27
> **scott stanley said:**
> Well I've read this thread but the Q and A doesn't exactly apply to me. I have no problem mounting my second HDD using the "Disks" tool under administration. I can rwx everything on the drive. BUT I have to mount it every time I log in. I know this can't be the way it's supposed to be, can someone please enlighten me?
Thanks in advance...

You need to add an entry in fstab with the option "auto"

"auto" means mount at boot. "noauto" meand do not mount at boot.

See my thread on how to fstab.

---

### Post by scott stanley on 2006-10-27
oh thanks. I'll check it out. Thanks!

---

### Post by FreakinSyco on 2006-10-27
Alright it mounts to /home/freakinsyco/Media but I'm throwing 2 errors:

```
mount: mount point 0 does not exist
mount: mount point 7 does not exist
```

And I still do not have write access.

I would prefer just to have HDB1 mount directly to /home/freakinsyco/Media so I'm not going to do the link from /mnt/Media to /home/freakinsyco/Media.

Heres my fstab in its entirety since something else could be throwing the error:

```
# /dev/hda1
UUID=c94dc2ca-1444-4c72-81aa-7c1188ae428a /               ext3    defaults,errors=remount-ro 0 1
# /dev/hdb1
UUID=4542-568B /home/freakinsyco/Media vfat
auto,users,nls=utf8,umask=007,gid=46 0 0
drwxr-xr-x 7 freakinsyco adm
# /dev/hda2
UUID=00944f1b-45cd-4003-9f0b-084db74dfa44 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by scott stanley on 2006-10-27
shoot. I just can't get the syntax right. Here's what I'm doing:

scott@Kyoushiro:~$ sudo /dev/hdb1 /mnt/storage ext3 auto 0 0

and here's what I get:
sudo: /dev/hdb1: command not found

---

### Post by FreakinSyco on 2006-10-27
> **scott stanley said:**
> shoot. I just can't get the syntax right. Here's what I'm doing:

scott@Kyoushiro:~$ sudo /dev/hdb1 /mnt/storage ext3 auto 0 0

and here's what I get:
sudo: /dev/hdb1: command not found

Think you need a "mount" after sudo.

---

### Post by aysiu on 2006-10-27
I think you're confusing an /etc/fstab entry with the manual mount command.

You either manually mount it: ```
sudo mount /dev/hdb1 /mnt/storage -t ext3
``` Or you add it to your /etc/fstab: ```
sudo nano -B /etc/fstab
``` Place this line inside that file: ```
/dev/hdb1 /mnt/storage ext3 auto 0 0
```

---

### Post by scott stanley on 2006-10-27
oh I think it worked...lemme log out real quick...

---

### Post by bodhi.zazen on 2006-10-28
> **FreakinSyco said:**
> Alright it mounts to /home/freakinsyco/Media but I'm throwing 2 errors:

```
mount: mount point 0 does not exist
mount: mount point 7 does not exist
```

And I still do not have write access.

I would prefer just to have HDB1 mount directly to /home/freakinsyco/Media so I'm not going to do the link from /mnt/Media to /home/freakinsyco/Media.

Heres my fstab in its entirety since something else could be throwing the error:

```
# /dev/hda1
UUID=c94dc2ca-1444-4c72-81aa-7c1188ae428a /               ext3    defaults,errors=remount-ro 0 1
# /dev/hdb1
UUID=4542-568B /home/freakinsyco/Media vfat
auto,users,nls=utf8,umask=007,gid=46 0 0
drwxr-xr-x 7 freakinsyco adm
# /dev/hda2
UUID=00944f1b-45cd-4003-9f0b-084db74dfa44 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```


You need to get rid of "drwxr-xr-x 7 freakinsyco adm"

and each entry should be on 1 line.

And I think yor swap is off ? did you modify it ?

Try this:
> # /dev/hda1
UUID=c94dc2ca-1444-4c72-81aa-7c1188ae428a  /  ext3  defaults,errors=remount-ro  0  1

# /dev/hdb1
UUID=4542-568B  /home/freakinsyco/Media  vfat  auto,users,nls=utf8,umask=007,gid=46  0  0

# /dev/hda2
UUID=00944f1b-45cd-4003-9f0b-084db74dfa44  swap  swap  defaults  0  0

# CDROM
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by scott stanley on 2006-11-12
hi there. That night you guys were helping me out with my own issue I had to break away due to my 2-year-old's temper tantrum :)

I'm just now getting around to messing around with auto mounting my second HD and got it to work.

Anyway, I just wanted to thank you all. It's this great community that makes linux all the more appealing. THANKS!

-Scott

---

