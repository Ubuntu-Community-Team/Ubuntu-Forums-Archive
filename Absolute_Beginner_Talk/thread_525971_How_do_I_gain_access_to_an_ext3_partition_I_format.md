---
title: "How do I gain access to an ext3 partition I formatted for uBuntu?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by tmcarson1 on 2007-08-14
I have installed uBuntu to a 160gb hard drive, I partitioned as

2gb /swap
20gb /
20gb /home
remainder as /ubuntumedia


Yet I don't see the /ubuntumedia partition when I am browsing my files.
How do I get uBuntu to let me access/read/write to this partition?
I planned to use it for storage, yet I cannot find it.

Any help is appreciated.

I tried to mount it and this is what I get:

thomas@thomas-desktop:~$ sudo mount /dev/hdc4

mount: /dev/disk/by-uuid/c4035859-e553-4207-a872-997da8e4f9b0 already mounted or /ubuntumedia busy

mount: according to mtab, /dev/hdc4 is already mounted on /ubuntumedia

So it says it is already mounted, but how do I access it or find it in Places->Computer

Thanks

---

### Post by moffa on 2007-08-14
output from
```
 cat /etc/fstab 
```
please

If you go to Nautilus and find the /ubuntumedia folder you can drag it to the left column and it'll add the shortcut to Places

---

### Post by creedog on 2007-08-14
I think that you need to unmount it and then create the mount point

mkdir /ubuntumedia
then mount again and
bam.... maybe something will happen.

---

### Post by tmcarson1 on 2007-08-14
Is Nautilus a seperate program or is it the one that runs when I click on Places ->Computer?

---

### Post by tmcarson1 on 2007-08-14
> **creedog said:**
> I think that you need to unmount it and then create the mount point

mkdir /ubuntumedia
then mount again and
bam.... maybe something will happen.

This is what I get:

thomas@thomas-desktop:~$ mkdir /ubuntumedia
mkdir: cannot create directory `/ubuntumedia': File exists

---

### Post by tmcarson1 on 2007-08-14
> **moffa said:**
> output from
```
 cat /etc/fstab 
```
please

If you go to Nautilus and find the /ubuntumedia folder you can drag it to the left column and it'll add the shortcut to Places

Ok, I did find it, I tried dragging the icon like you said and it says:

You do not have permissions to write to this folder (also I noticed the lost and found folder is inside here if it matters).
It also says that 'root' is the owner if that helps.

I would like to get this so that I can read/write to it, it is almost 110gb! =)

---

### Post by moffa on 2007-08-14
> **tmcarson1 said:**
> Ok, I did find it, I tried dragging the icon like you said and it says:

You do not have permissions to write to this folder (also I noticed the lost and found folder is inside here if it matters).

If you go to Places, Computer then

Filesystem, then drag the icon for the ubuntumedia folder to the left column, below Floppy Drive and Filesystem

If you go into the ubuntumedia folder can you see your files there?

---

### Post by tmcarson1 on 2007-08-14
> **moffa said:**
> output from
```
 cat /etc/fstab 
```
please

If you go to Nautilus and find the /ubuntumedia folder you can drag it to the left column and it'll add the shortcut to Places

Here is what cat /etc/fstab says:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=8b285b70-4139-427a-853a-430320e265f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc3
UUID=72d4396a-da58-49da-a66f-e3789dfbbd2e /home           ext3    defaults        0       2
# /dev/hda1
UUID=52C467B6C4679ACD /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc4
UUID=c4035859-e553-4207-a872-997da8e4f9b0 /ubuntumedia    ext3    defaults        0       2
# /dev/hdc2
UUID=f434423d-9fc2-496a-be7e-da71e18d0900 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by tmcarson1 on 2007-08-14
> **moffa said:**
> If you go to Places, Computer then

Filesystem, then drag the icon for the ubuntumedia folder to the left column, below Floppy Drive and Filesystem

If you go into the ubuntumedia folder can you see your files there?

When I drag the icon it says I don't have permission to write to this folder /media/hda1


There are no files in there since I just formatted/partitioned the drive, but I would like to store files there.

---

### Post by djchandler on 2007-08-14
Are you seeing /ubuntumedia as a folder in the filesystem main directory? It is already mounted. Can you write a test file to /ubuntumedia? You may need root (sudo) privileges to create a folder in it, but give ownership to your login account. Drag that folder to Places, then try writing a test file to it.

You can do this in the gui, striking the key combination "Alt-F2", and entering "gksu nautilus" in the command line dialog box. Nautilus is the program that runs when you click on one of the Places items. When you click on About under the Help menu, it should say "Nautilus 2.18.1."

---

### Post by moffa on 2007-08-14
You are dragging it to a folder in the left column, drag it to the open white space below it.  It look like the folder is already mounted.

You may need to be root to copy files there.  You can change it but I can't remember how at this moment.

---

### Post by tmcarson1 on 2007-08-14
> **djchandler said:**
> Are you seeing /ubuntumedia as a folder in the filesystem main directory? It is already mounted. Can you write a test file to /ubuntumedia? You may need root (sudo) privileges to create a folder in it, but give ownership to your login account. Drag that folder to Places, then try writing a test file to it.

You can do this in the gui, striking the key combination "Alt-F2", and entering "gksu nautilus" in the command line dialog box.


I do see it as a folder in the Filesystem directory.

I am able to create a new folder in /ubuntumedia

I actually am able to save a file to it (a pic file from a website).
Does this mean I already have read/write access to this area if I am able to save
an image in /ubuntumedia?

---

### Post by djchandler on 2007-08-14
> **tmcarson1 said:**
> I do see it as a folder in the Filesystem directory.

I am able to create a new folder in /ubuntumedia

I actually am able to save a file to it (a pic file from a website).
Does this mean I already have read/write access to this area if I am able to save
an image in /ubuntumedia?

Yes.

DJ

---

### Post by moffa on 2007-08-14
> **tmcarson1 said:**
> I do see it as a folder in the Filesystem directory.

I am able to create a new folder in /ubuntumedia

I actually am able to save a file to it (a pic file from a website).
Does this mean I already have read/write access to this area if I am able to save
an image in /ubuntumedia?

Since you used gksudo nautilus you are running it as root.

If you go and edit /etc/fstab (using that root version of nautilus) you need to change the line:

# /dev/hdc4
UUID=c4035859-e553-4207-a872-997da8e4f9b0 /ubuntumedia ext3 defaults 0 2

to:

# /dev/hdc4
UUID=c4035859-e553-4207-a872-997da8e4f9b0 /ubuntumedia ext3 defaults,**umask=0000** 0 2

I think the umask=0000 should give everyone access to it

---

### Post by tmcarson1 on 2007-08-14
> **djchandler said:**
> Yes.

DJ

Thank you everyone for your help!!

Hopefully one day I will be as well versed in this as you are and am able to return
the favor here to someone else seeking help.  :guitar:

---

### Post by djchandler on 2007-08-14
> **moffa said:**
> Since you used gksudo nautilus you are running it as root.

If you go and edit /etc/fstab (using that root version of nautilus) you need to change the line:

# /dev/hdc4
UUID=c4035859-e553-4207-a872-997da8e4f9b0 /ubuntumedia ext3 defaults 0 2

to:

# /dev/hdc4
UUID=c4035859-e553-4207-a872-997da8e4f9b0 /ubuntumedia ext3 defaults,**umask=0000** 0 2

I think the umask=0000 should give everyone access to it

If he changes the permissions in nautilus as gksu, there is no need for all this command line stuff.

Why are we trying to scare this guy off by telling him he has to do all this command line stuff. He's root when he's doing that too. All he needs to do is close nautilus to discontinue running it as root. I guess we need to expalin that running as gksu is for making system level changes, which we normally don't need to do.

I don't understand all the adversity to running a GUI program as root. Doesn't anybody but me use Synaptic and update-manager?
:confused:
DJ

---

