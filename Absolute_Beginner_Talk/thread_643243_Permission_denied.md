---
title: "Permission denied"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by edhunter on 2007-12-17
i was copying some movies into a directory and then it told me ¨sorry it could not display all the contents of the folder¨  what have i done wrong?? is there a total size limit per folder?

---

### Post by bodhi.zazen on 2007-12-17
I moved this post to a more visible place.

It is likely a permissions problem :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

You can circumvent this to some extent by putting :

```
gksu nautilus
``` in a terminal and then navigation to the directory, but, IMO , best to read about permissions.

---

### Post by edhunter on 2007-12-17
ahh many thanks for that, still at my very early stages of learning linux, im pretty sure i did acidentally stuff around with the permissions, as i was trying to change it from the folder having to have a password for protection to one that the rest of my flatmates could access without the need for a password

---

### Post by vanadium on 2007-12-17
No, you are facing a Gutsy bug. In a nautilus window, select "Edit - Preferences". On the "Preview" tab, set "Preview sound files" to "never", click close. This will stop the issue.

---

### Post by edhunter on 2007-12-17
tried that and it still didnt work. i read through the permissions page you posted and even though i understand that part, i still cannot link it to my problem, more that i dont know how to change the permissions of each and individual folder

---

### Post by bodhi.zazen on 2007-12-17
Now I am not certain if you aer dealing with a bug or not.

To change permissions, use chmod. You can use octal, chmod 760 <file> or chmod o+r

[http://www.washington.edu/computing/unix/permissions.html](http://www.washington.edu/computing/unix/permissions.html)

change ownership with chown

---

### Post by vanadium on 2007-12-18
Note my previous post: this is the workaround to this issue. Playing with permissions as root can be dangerous if you do not know what you do and in fact is not a solution to your issue.

---

### Post by edhunter on 2007-12-18
> **vanadium said:**
> Note my previous post: this is the workaround to this issue. Playing with permissions as root can be dangerous if you do not know what you do and in fact is not a solution to your issue.

i think it stems from me trying to change it so i didnt have to enter a password to go into that particular folder, and all this trouble has occured since then, still unsure the exact path to take, as the help that has been offered is somewhat vague, or that im still very unclued in gusty

---

### Post by anewguy on 2007-12-19
Okay, let's ask a more basic question:

What folder, and what did you do (please be explicit) when you were trying to "make it not ask for a password"?

Also, please post back the results of the following:

ls -al xxxxxxxxx     <--- where xxxxxxxx is the folder in question


This should give us a little more basic understanding of what you did versus what you intended, and stop us from assuming you need to do "x" or "y".:)

---

### Post by edhunter on 2007-12-19
flat@ubuntu:~$ ls -al /media/movies/MOVIES
ls: reading directory /media/movies/MOVIES: Input/output error

i think i right clicked on the MOVIES folder and went into permissions to try and disable the password protect for that specific folder, its weird as all the other folders in the /media/movies directory dont need a password to access them. i think i might have clicked the executable file, or something similar?

also in the MOVIE properties under permissions it tells me im not the owner so i cannot change the permissions, even though im logged in under the administrator

---

### Post by anewguy on 2007-12-19
> **edhunter said:**
> flat@ubuntu:~$ ls -al /media/movies/MOVIES
ls: reading directory /media/movies/MOVIES: Input/output error

i think i right clicked on the MOVIES folder and went into permissions to try and disable the password protect for that specific folder, its weird as all the other folders in the /media/movies directory dont need a password to access them. i think i might have clicked the executable file, or something similar?

also in the MOVIE properties under permissions it tells me im not the owner so i cannot change the permissions, even though im logged in under the administrator

Try posting this back:

ls -al /media/movies 

I don't have the "movies" subdirectory in media, so I can't see it directly.  However, the "media" directory is owned by root, and since the "movies" directory was created within it, I would assume it inherited the same ownership and permissions.

EDIT:  I'm probably being stupid - you are somehow mounting something (with a name of "MOVIES") to /media/movies??

---

### Post by edhunter on 2007-12-19
yeh the /media/movies/MOVIES folder contains all my movies, its just a sub folder from the /media/movies

ahhh wait a second, the /media/movies is my 320gig hdd called funnily enough ¨movies¨  so the directory ¨MOVIES¨ is the main folder in that hdd if that makes any more sense, i have my 40gig hdd totally dedicated for ubuntu

---

### Post by edhunter on 2007-12-19
drwxrwxrwx 1 root root    12288 2007-12-19 19:07 .
drwxr-xr-x 5 root root     4096 2007-12-19 18:54 ..
drwxrwxrwx 1 root root     4096 2007-12-04 17:35 Alcohol.120.v1.9.6.4719
-rwxrwxrwx 1 root root 53976416 2007-12-18 17:59 ati-driver-installer-8.28.8.run
drwxrwxrwx 1 root root        0 2007-12-17 23:06 downloads
-rwxrwxrwx 1 root root   525752 2007-12-18 17:47 envy_0.9.9-0ubuntu2_all.deb
drwxrwxrwx 1 root root        0 2007-12-18 17:59 fglrx-install
drwxrwxrwx 1 root root        0 2007-12-18 09:03 MOVIES
drwxrwxrwx 1 root root    12288 2007-12-19 19:07 Music Vids
drwxrwxrwx 1 root root     8192 2007-12-18 09:04 New Folder
drwxrwxrwx 1 root root        0 2007-12-03 05:12 RECYCLER
drwxrwxrwx 1 root root     4096 2007-12-03 06:16 System Volume Information
drwxrwxrwx 1 root root     8192 2007-12-18 09:13 .Trash-edhunter
drwxrwxrwx 1 root root        0 2007-12-18 18:58 .Trash-flat
drwxrwxrwx 1 root root        0 2007-12-17 22:35 TV Episodes


yeh the /media/movies/MOVIES folder contains all my movies, its just a sub folder from the /media/movies

ahhh wait a second, the /media/movies is my 320gig hdd called funnily enough ¨movies¨  so the directory ¨MOVIES¨ is the main folder in that hdd if that makes any more sense, i have my 40gig hdd totally dedicated for ubuntu

---

### Post by anewguy on 2007-12-19
> **edhunter said:**
> drwxrwxrwx 1 root root    12288 2007-12-19 19:07 .
drwxr-xr-x 5 root root     4096 2007-12-19 18:54 ..
drwxrwxrwx 1 root root     4096 2007-12-04 17:35 Alcohol.120.v1.9.6.4719
-rwxrwxrwx 1 root root 53976416 2007-12-18 17:59 ati-driver-installer-8.28.8.run
drwxrwxrwx 1 root root        0 2007-12-17 23:06 downloads
-rwxrwxrwx 1 root root   525752 2007-12-18 17:47 envy_0.9.9-0ubuntu2_all.deb
drwxrwxrwx 1 root root        0 2007-12-18 17:59 fglrx-install
drwxrwxrwx 1 root root        0 2007-12-18 09:03 MOVIES
drwxrwxrwx 1 root root    12288 2007-12-19 19:07 Music Vids
drwxrwxrwx 1 root root     8192 2007-12-18 09:04 New Folder
drwxrwxrwx 1 root root        0 2007-12-03 05:12 RECYCLER
drwxrwxrwx 1 root root     4096 2007-12-03 06:16 System Volume Information
drwxrwxrwx 1 root root     8192 2007-12-18 09:13 .Trash-edhunter
drwxrwxrwx 1 root root        0 2007-12-18 18:58 .Trash-flat
drwxrwxrwx 1 root root        0 2007-12-17 22:35 TV Episodes


yeh the /media/movies/MOVIES folder contains all my movies, its just a sub folder from the /media/movies

ahhh wait a second, the /media/movies is my 320gig hdd called funnily enough ¨movies¨  so the directory ¨MOVIES¨ is the main folder in that hdd if that makes any more sense, i have my 40gig hdd totally dedicated for ubuntu

I think you will need to check fstab (?) to see how that drive is getting mounted.  Judging just from the list above, the world has complete access to your "MOVIES" subfolder.  Try checking the permissions on the /media/movies folder via:

sudo ls -al /media/movies

:)

---

### Post by anewguy on 2007-12-19
Okay this is probably a dumb question, but instead of just mounting that volume to /media/movies why don't you try mounting /media/movies to a folder in your home folder called "MOVIES" - that way you should be mounting the block device  and the root of that mounted device should be visible under the "MOVIES" folder in your home folder.

I'm not sure if this is correct or not, but try this in a terminal:

cd ~         to get to home folder
mkdir MOVIES        to create folder "MOVIES"
sudo mount /media/movies  ~/MOVIES

it will ask for your password to mount it.  After that try the following:

cd ~/MOVIES
ls 


Hopefully it will find the movies then.  

I have to tell you I only have 1 hard disk so I have never tried this.  I think it is supposed to work, and it won't hurt anything.  I just don't know what Ubuntu does to mount a second disk initially ->  I'm assuming in your case the drive is known as /media/movies when the system mounts it.

I'm sure someone will say if I'm giving you bad info, but I think it's worth a try!:)

---

### Post by edhunter on 2007-12-20
i think what i did was format the 40gig hdd for ubuntu, but kept the 320 hdd  as original xp ntfs format, i tried both suggested options, but im guessing it would be easiest to reformat the 320gig hdd and start over, luckily ive got the movies etc backed up on another computer in the network, so maybe just a reformat would be the go? ive tried looking into just reformatting that hdd but havent found the right way to do it

---

### Post by anewguy on 2007-12-20
I think you can mount a NTFS partition to a local folder just by specifying -t ntfs in the mount statement.  What I don't know is if you can do anything other than read from a NTFS partition.  It used to be you could only read them, not write them, from Ubuntu, but that may have changed.  I have no NTFS partition to try it out on.

Assume you have a folder of "myntfs' that you have created off your home folder.

Assume your NTFS drive is sdb in the /dev folder

Assume you have a single ntfs partition on that drive, as partition 0

I think all you would need to do is:

sudo mount -t ntfs /dev/sdb0 ~/myntfs


You should be able to "see" the device contents in the folder ~/myntfs.  Judging from an earlier post, I would assume you should be able to see ~/myntfs/MOVIES  there.

I really don't think reformatting your hard drive would do you any good.  Permissions can be reset, etc., and I really think it's just a matter of getting it mounted locally to your directory.

As an example, sometimes I mount a CD volume locally by doing the following:


mount /dev/cdrom  ~/mycd    (I think that's it - I usually get it right the first try for that)

Try the mount of the hard drive and partition to a local folder and post back what happens.:)

EDIT:  If sdb0 shows when you click on "Places", you might have to do "sudo umount /dev/sdb0"  first - I've never tried it with a hard disk.  I know a floppy can show as mounted and show on the desktop and I can still locally mount it to a subfolder.

---

### Post by vanadium on 2007-12-22
Can you list the contents of /media/movies/MOVIES? Is the drive mounted? This can be checked using the command "mount". Is the drive recognized by the system (sudo fdisk -l). It probably is in /etc/fstab, but perhaps it cannot mount for one or another reason: run "sudo mount -a" and note any error messages: this will give a clue on how to solve the issue. If you want others to help interpreting what the output means, then post all output here.

---

### Post by thelatinist on 2007-12-22
This is an NTFS device?  Then my guess is that you need to instal ntfs-3g.  The default drivers on Ubuntu do not support writing to NTFS, only reading.

Try posting the results of

```
cat /etc/fstab
```

---

### Post by btq123 on 2007-12-22
In a nautilus window, select "Edit - Preferences". On the "Preview" tab, set "Preview sound files" to "never", click close

try!

---

### Post by vanadium on 2007-12-23
I already suggested that two times but he doesn't seem to want to listen to me ;)

---

