---
title: "Help with setting permision"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Swimerdude on 2007-03-19
Hello i'm new here and have searched for about an hour fro this question and since i've been unable to find it i figured i'd ask.  I've recently figure4d out how to mount hard drives into folders so i can see ntfs systems files.  The only problem i am having is that the permissions where never changed, even though i thought i typed a command to change them.  the command was 
sudo chmod 777 /media/[SAME NAME

Did i type in a wrong number someplace?  Thanks very much in advance for the help.

---

### Post by justleen on 2007-03-19
What is it what your trying to achive?

Writing to NTFS from Ubuntu wont work (by default..)  you can mount the partitions and see what is on them, but you cannot write to them.

---

### Post by Swimerdude on 2007-03-19
I am trying to either a, view movies off another hard drive instead of having to re burn everything in ext3.

---

### Post by justleen on 2007-03-19
> **Swimerdude said:**
> I am trying to either a, view movies off another hard drive instead of having to re burn everything in ext3.


for just viewing you shoulnd have to change any file permissions.. The permissions are on read only, which is fine for video files

Can you actually see the files, if you do 
```

ls /media/windows 
``` (replace windows with the name of the dir)

---

### Post by Swimerdude on 2007-03-19
It says you do not have the permission to view these files when i go to that directory.  but found a topic about ventrilo and it had an extra called automatix so i installed that and it had an auto mounter, so i am about to restart and try that out.

---

### Post by justleen on 2007-03-19
> **Swimerdude said:**
> It says you do not have the permission to view these files when i go to that directory.  but found a topic about ventrilo and it had an extra called automatix so i installed that and it had an auto mounter, so i am about to restart and try that out.



ah, the DIRectory itself is not readable...
try a sudo ls /media/windows thats should work


if you do a ls -la  on /media, you'll probaly find that the owner is root, instead of your username.


you should change the owner of the directory so your username may access is.
```

sudo chown USERNAME /media/windows 
```
chmod - change permissions
chown - change owner

a file or dir can have full read write permissions, but if the ownership is not set correctly, you still wont be able to change anything..

---

### Post by hyper_ch on 2007-03-19
I'm afraid but without write permissions I think you can't view the vids and stuff... or is it exec permission?
I noticed the same when I migrated from windoze to linux... at first I had all my mp3s on my ntfs drive... I could browse them but not play.

---

### Post by Swimerdude on 2007-03-19
Well i couldn't browase them but i used the automatix to install (i forgot what i installed but its the only option that correlates to mounting, reading, and writing ntfs files.  I can now see them all, and i am very happy.  Thanks for the help guys:)

---

### Post by justleen on 2007-03-19
> **hyper_ch said:**
> I'm afraid but without write permissions I think you can't view the vids and stuff... or is it exec permission?
I noticed the same when I migrated from windoze to linux... at first I had all my mp3s on my ntfs drive... I could browse them but not play.

anybody else  reading this, correct me if im wrong..

Read access should be sufficient. If can list the directory contents, and the file permissions are on Read, you should have no problems...

im @work, so i cant test/verify anything here, but from the top of my head, thats how it works..

---

### Post by hyper_ch on 2007-03-19
justleen:

It should be but it wasn't enough permissions to have the mp3 played in Amarok... it worked once I copied them over to my home folder or to the FAT32 partition but I couldn't get them to play from a ro-ntfs drive.

---

### Post by Najand on 2007-03-19
I think you should change mount paremeters not permissions of /media/blahblah folder.
Can you send us your /etc/fstab file if you used automount or the command you used to mount the media including its options here?

---

### Post by hyper_ch on 2007-03-19
I used this:

> 
/dev/hda1 /media/c_drive ntfs ro,defaults,umask=0222 0 0


---

### Post by Swimerdude on 2007-03-19
Hmm the old ones i used where sudo dirmak /media/volume1
the i was told to do sudo chmod 777 /media/volume1
and then i typed in sudo mount /dev/sda1 /media/volume1

and at that point it mounted it.  now if i went through the system window i couldn't see the files because the owner was root.  but if i typed to see it in terminal it would ask for my pw and then i could see them.  now though i have downloaded a different mounter that auto mounts the ntfs AND fat32 drives and i can see them both and use the files i wanted from them.

---

### Post by Najand on 2007-03-19
Remove "umask=0222" and use "users" instead. Then use:
```
 
sudo umount /dev/hda1

``` and then do
```

mount /dev/hda1

```
again.

---

### Post by Najand on 2007-03-19
As far as it is an NTFS drive there is no point in changing the folder permissions, because it is a READONLY device. You should assign permissions when mounting your device.

---

### Post by justleen on 2007-03-19
GLad its solved then...

I will do some testing on my own machine though, there must be an easy way to set this up! did it in the past... so should be able to do it now...

Thanks for thje feedback people!

---

