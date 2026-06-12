---
title: "Quick question. Whoever answers gets an award.  Can't delete folder!"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-08-26
Ubuntu says that i cannot delete a folder that I MYSELFT created "because you do not have permissions to change it or its parent folder."


Why cant i delete this.:confused:

---

### Post by systemintheglitch on 2006-08-26
It seems i can't create any more folders either!

---

### Post by Tomosaur on 2006-08-26
You must have made the folder as root, or a user in a different group - but are you SURE you made it yourself? Please post the path to the folder first so we can be sure you don't mess anything up before we (or I, whatever) tell you how to do this.

---

### Post by systemintheglitch on 2006-08-26
I am the only user on my ubuntu install.. 

The folder was /Windows..

which is where i was mounting my winfat32 drive, but now i want to change it by creating a windowsFAT32 folder in the /media directory.

Noone else could have made that windows directory.

I CAN create (and probalby destroy - how do i do that?) with the console

"sudo mkdir /yada/yada"


but i can't do it in nautilist.. 

By the way how DO i delete a directory..

---

### Post by BugenhagenXIII on 2006-08-26
To do it in nautilus, go into a terminal and type
```
gksudo nautilus
```

then navigate to what you want to delete, and delete it.

---

### Post by annda on 2006-08-26
the thing is, it's important WHERE you are trying to create the folders. by default (for security reasons) you don't have easy (writing/deleting) access to all the files.

please post exactly where and how you create your folders/files (file manager, e.g. nautilus, terminal?)

---

### Post by wildseven on 2006-08-26
if you wanna delete from console

```
sudo rm <filename>
```
if its a folder like urs and you are sure u wanna delete everything in it, do this
```
sudo rm -r <foldername>
```

so if ur folder name is /Windowsfat32
you would do
```
sudo rm -r /Windowsfat32
```
it will ask you for your password and prompt you for an "Are you sure you want to delete this file?" for every file in there.

if you dont wanna press "Y" for all of them, do:
```
sudo rm -rf /Windowsfat32
```

DO NOT I REPEAT DO NOT DO!!!!!:
```
sudo rm -rf /
```

that will delete your entire drive. and it wont ask you for your permission.

---

### Post by systemintheglitch on 2006-08-26
Why do i have to do that everytime i want to edit directory structure.
Why can't that be the default
how do i make it so that IS the default.

---

### Post by Tomosaur on 2006-08-26
Right well, you shouldn't ever make a folder in root. All your custom stuff should be in your home folder. Here's what you need to do to set up your windows folder properly:
First, UNMOUNT your windows drive.
Now, remove the windows directory you created by typing:
```

sudo rmdir /Windows

```

Now, make a windows directory in your home dir:
```

mkdir ~/windows

```

Then mount your windows drive from your newly created windows directory. Let's say your windows drive is /dev/hda1:
```

sudo mount /dev/hda1 ~/windows

```

Then to get to your windows stuff, just use that directory.

Never make extra files and folders in root, it's just asking for trouble.

---

### Post by systemintheglitch on 2006-08-26
Then to get to your windows stuff, just use that directory.

Never make extra files and folders in root, it's just asking for trouble.

Ok i will try that, but didnt you forget to tell me to add sda1 to the pmount.allow file?  Just curious why i allready did that, hope that was the right thing to do.

But you never answered why it is that i cant just edit directories in nautilist naturally. I am the only one using my computer.

---

### Post by wildseven on 2006-08-26
did u do
```
gksudo nautilus
```
?

this puts u into super user account so u can do all ur graphical needs as if u were root.

even if ur the only account on the computer, someone may have physical access to ur computer/laptop w/e and if there was no prompt for root or SU then he could do w/e he wanted.

---

### Post by systemintheglitch on 2006-08-26
If they have physical access then they could just do gksudo natuilist themselves.

What is the point it didnt ask for a password.

---

### Post by Tomosaur on 2006-08-26
You can add it to pmount.allow if you wish, but it's not absolutely necessary to get the drive mounted.

As for editing files in nautilus - the average user generally doesn't need to alter the various system files which they are prohibited from doing so. This is not a nautilus problem, this is just how linux works. The problem with nautilus is that it doesn't provide you with a way of assuming root priveleges so that you can edit these files if you need to. I personally just use the terminal to edit system files, it's a lot faster.

---

### Post by wildseven on 2006-08-26
high five tomosaur.

think terminal. think shell ftw.

---

### Post by systemintheglitch on 2006-08-26
Problem:

It appears my drive is allready mounted to root!!

sudo mount /dev/sda1 ~/windows
mount: /dev/sda1 already mounted or /home/jordan/windows busy
mount: according to mtab, /dev/sda1 is mounted on /

How do i unmount!!

---

### Post by Tomosaur on 2006-08-26
use the umount command:
```

sudo umount /dev/sda1

```
should do it.

---

### Post by systemintheglitch on 2006-08-26
It says the device is busy!!! Maybe this has to do with the fact that my dumb *** mounted it to root!

What do i do guys.??

---

### Post by Tomosaur on 2006-08-26
Close all other windows and files before you unmount it - you can't be viewing files or folders or whatever on the drive you're trying to unmount.

---

### Post by systemintheglitch on 2006-08-26
I closed everything including this web browser and it still said it was busy.

---

### Post by Tomosaur on 2006-08-26
alright, try a lazy unmount:
```

sudo umount -l /dev/sda1

```

---

### Post by teasum on 2006-08-26
> **systemintheglitch said:**
> If they have physical access then they could just do gksudo natuilist themselves.

What is the point it didnt ask for a password.

Just a quick answer to this point: If you have already entered your root password elsewhere (e.g. for synaptic or for 'sudo su' in the terminal), and you then run 'gksudo nautilus' it will not require a password for a certain period of time (15 minutes, if I'm not mistaken).  If you have not entered your root password for anything for a while, however, running 'gksudo nautilus' should prompt you for your password.  Someone correct me if I'm wrong about this!

---

### Post by systemintheglitch on 2006-08-26
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


This doesnt look good.. What does this mean??

I don't think linux likes me.

---

### Post by Tomosaur on 2006-08-26
:/

Please paste the output of the following command:
```

sudo fdisk -lu

```

---

### Post by systemintheglitch on 2006-08-26
cannot open /proc/partitions

:/

---

### Post by Tomosaur on 2006-08-26
Did you use sudo?

---

### Post by systemintheglitch on 2006-08-26
Yes.. I did..

Is this because I mounted root?

What is going on.

---

### Post by Tomosaur on 2006-08-26
I'm not sure, try
```

ls /proc/partitions

```
and see if the file is there.

---

### Post by TFX360 on 2006-08-26
> **teasum said:**
> Just a quick answer to this point: If you have already entered your root password elsewhere (e.g. for synaptic or for 'sudo su' in the terminal), and you then run 'gksudo nautilus' it will not require a password for a certain period of time (15 minutes, if I'm not mistaken).  If you have not entered your root password for anything for a while, however, running 'gksudo nautilus' should prompt you for your password.  Someone correct me if I'm wrong about this!

Teasum,


Right, 15 minutes.


Kind regards,


TFX

---

### Post by systemintheglitch on 2006-08-26
ls: /proc/partitions: No such file or directory

---

### Post by Tomosaur on 2006-08-26
Then you have a problem.
Try:
```

sudo partprobe

```

---

### Post by systemintheglitch on 2006-08-26
sude partprobe had NO output in the console

---

### Post by Tomosaur on 2006-08-26
Ok, now check to see if /proc/partitions exists:
```

ls /proc/partitions

```

---

### Post by shamrock_uk on 2006-08-26
.

---

### Post by systemintheglitch on 2006-08-26
no such directory exists
still..

Is my computer messed up?

I didnt do anything except accidentally mount the ntfs onto root.

---

### Post by systemintheglitch on 2006-08-26
Dont worry about that right now, i have a fealing we have bigger problems..

I cant mount my ntfs to ANY folder. 
it is busy.. I accidentally mounted it to root.. I unmounted it but cannot remount it.


ATTENTION: I just found something:
When I open computer i cant even see the swap partition, i cant see my fat32 or windows ntfs. All i see are the linux partition and cdrom/floppy what the hell happened.

---

### Post by Tomosaur on 2006-08-26
Can you paste the output of the following command:
```

cat /etc/fstab

```
I think you may have been trying to unmount the wrong drive - ie, you've unmounted your linux drive or something bizarre like that.

---

### Post by shamrock_uk on 2006-08-26
> **systemintheglitch said:**
> no such directory exists
still..

Is my computer messed up?

I didnt do anything except accidentally mount the ntfs onto root.

Well, I wouldn't restart until this is cleared up if I were you. Might also be a good idea to make sure your backups are up to date, purely as a precautionary measure.

Install gparted would you, and see if your partitions are displayed with that.

---

### Post by shamrock_uk on 2006-08-26
Gnyah, what is it with this thread? Double post, sorry :(

---

### Post by systemintheglitch on 2006-08-26
results of fstab

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I am missing sda1 and sda5..



Please i have very important docs on my windows ntfs and my backups arent up to date on my windows partition..

I really need to solve this or i am screwed.

---

### Post by systemintheglitch on 2006-08-26
My sda1 and sda5 appear in gparted but with a giant exclamation mark next to it.

---

### Post by systemintheglitch on 2006-08-26
Can you guys chat with me about it live.. at this page:

[url]http://www.gabbly.com/http://ubuntuforums.org/

Ill be waiting there.. Its very important that i recover my ntfs and be able to mount it.

---

### Post by shamrock_uk on 2006-08-26
> **systemintheglitch said:**
> My sda1 and sda5 appear in gparted but with a giant exclamation mark next to it.

Could you check view -> harddisk information and see what crops up on the left hand side. 

Also, if you could select sda1 and do partition -> information.

---

### Post by systemintheglitch on 2006-08-26
status is not mounted and says that i cannot browse it because i might not have the correct plugin installed for that type of filesystem..
I think that is a bunch of crap.

---

### Post by Tomosaur on 2006-08-26
Ugh this is very weird, but I really have to go now. 

Hope you get this fixed!

---

### Post by systemintheglitch on 2006-08-26
Dude.. I am screwed..

Has everyone just given up?

---

### Post by Tomosaur on 2006-08-26
Just a thought - since fstab is still showing your linux partition, I'm guessing you should be able to reboot with no ill-effects. This MAY allow linux to re-find your windows drives, and then you'll be able to mount them using the instructions a few pages back.

---

### Post by systemintheglitch on 2006-08-26
Thanks tomosaur I will try that.

---

### Post by shamrock_uk on 2006-08-26
> **Tomosaur said:**
> Just a thought - since fstab is still showing your linux partition, I'm guessing you should be able to reboot with no ill-effects. This MAY allow linux to re-find your windows drives, and then you'll be able to mount them using the instructions a few pages back.

And have you tried booting into Windows? A missing /proc/partitions sounds a little bit like Linux is screwed, but it certainly doesn't follow that your ntfs drives must be. 

I would try and backup your most recent changes as a precaution and then reboot. 

See if you can boot into Windows. Also keep in mind that you can always boot from a livecd and probably mount the drives from there. 

Sorry, it's 1am here and I have to be up early tomorrow, but if you wanted realtime help I suggest you try some of the tech support Ubuntu channels on IRC on the freenode servers. There's usually some pretty smart folk hanging around in there. 

Good luck!

---

### Post by systemintheglitch on 2006-08-26
I would try and backup your most recent changes as a precaution and then reboot.

See if you can boot into Windows. Also keep in mind that you can always boot from a livecd and probably mount the drives from there.

Sorry, it's 1am here and I have to be up early tomorrow, but if you wanted realtime help I suggest you try some of the tech support Ubuntu channels on IRC on the freenode servers. There's usually some pretty smart folk hanging around in there.

Good luck!


Thanks you guys, i rebooted and now its showing the partitions.

---

