---
title: "can't log in, oops!"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by iainr86 on 2008-03-13
ok so i installed ubuntu onto my laptop last night and spent hours getting it all set up how i wanted. now in my ignorance i was messing around with settings and found that each user gets a home directory that has subfolders called music and photos and the like....

so i didnt want that kind of stuff on my linux partition, but rather on my fat32 partition for sharing with windows. so i changed the location of my home directory in the user setup window to the fat32 partition. and now i'm screwed! 

it wont let me log on as it says something about not being able to save the session amongst other scary messages. i tried changing the session to failsafe and i got the same error.

can someone please help?? how can i get logged in to change the location of the home directory back (and also what is the default path for the home directory?)

does ubuntu have any default logins that i can use to get logged in? aghh!!

---

### Post by Tatty on 2008-03-13
I dont think having a home directory on a fat32 partition will work, because fat32 does not have the same permissions system as ext3.

If you want to access your /home from windows, you can install ext3 drivers for windows... [http://www.fs-driver.org/]("http://www.fs-driver.org/")

If you have copied your home directory over to fat32 already then im not sure you could save it as you will have already lost all the permissions.  The best thing you could do is boot to a recovery console, change the /home mount back to an ext3 partition, delete and then re-create your user.

---

### Post by Arthur Archnix on 2008-03-13
You need to log into the recovery console. Choose recovery mode at boot, when you can choose between Ubuntu, Recoery and MemTest.

Then you have two options. Either edit your fstab to tell ubuntu where you put your home dir. Or move your home dir back to where it was. 

Generally speaking, option one would go like this:
```
fdisk -l   # to see what your partitions are called
nano /etc/fstab  #opens fstab to edit partition information
```
Then you'd add information about your fat 32 partition, the sda number, the fstype, any options, and most importantly, the mount point, which would be /home. Then you'd save and reboot.

Option two would perhaps be simpler, you'd still need to fdisk -l to see where the fat partition is and what it's called. Then you'd need to mount it, and move home back to where it was something like:
```
mkdir /mount/fat32
mount /dev/sda# /mount/fat32
cd /mount/fat32
mv home /
```

These instructions aren't precise, they're just an outline of what needs to be done. If you need more specific instructions you'll have to post back with the output of these two commands:
```
fdisk -l
cat /etc/fstab
```
If you can run them from a terminal without having to go into rescue mode (eg., by pressing Ctrl+Alt+F1 when gnome pops up and tells you your system is messed up, then you'll need to add sudo to those commands.

---

### Post by iainr86 on 2008-03-13
ooops, too slow. awesome, i'm on it

---

### Post by iainr86 on 2008-03-13
ok firstly after doing fdisk -l i get:

/dev/sda1        HPFS/NTFS
/dev/sda2        Linux
/dev/sda3        W95 FAT32 (LBA)
/dev/sda4        Linux swap / Solaris

ok, cat /etc/fstab gives me a whole load of stuff, what exactly is it you need to know?

i'm going for option 2 btw

also do i need to tell it which user i'm doing this for at any point? or since i've only got 1 does it not matter?

---

### Post by Arthur Archnix on 2008-03-13
It says something roughly like

#/dev/sda2
UUID: blahblahblah  /    ext3   defaults   0  1 

We need to know the fat32 one. It'll be under #/dev/sda3

---

### Post by iainr86 on 2008-03-13
# /dev/sda3
UUID=0326-0328   /media/sda3    vfat    defaults,utf8,umask=007,gid=46  0            1

---

### Post by Arthur Archnix on 2008-03-13
ok, so in a terminal do:
```
cd /media/sda3
```
then type
```
ls -a
```
if you see
```
home
```
then do:
```
sudo mv home /
```
if you don't see home, then post back what you do see.

---

### Post by iainr86 on 2008-03-13
right, sorry for the delay.

ive done what you said and i see:

.              .gconf        .gnome2_private    Documents   Public
..            .gconfd      .xsession-errors      Music         Templates
.config   .gnome2      Desktop         Pictures         Videos


so no home, what do i do?
thanks

---

### Post by Arthur Archnix on 2008-03-13
> so i changed the location of my home directory in the user setup window to the fat32 partition. and now i'm screwed!
Can you describe in more detail what you did?

As a workaround, go to a terminal and type:
```
sudo useradd -d /home/iain -m iain
sudo passwd iain
```

That should create a new user called iain, and setup a password. Then you can log on with that user and worry about fixing the old account. Feel free to change iain to whatever you like, except the name of your old currently broken user account

---

### Post by iainr86 on 2008-03-13
ok i've added a new account. what i need to do is get into the edit users and groups menu, but to do that it needs the administrator password. i put that in and it said invalid password, probably because its linked to the account which is broken?

is there any other way to get into that setting, or can i reset the admin password somehow?

---

### Post by Arthur Archnix on 2008-03-13
[FONT=Lucida Console]N[/FONT][FONT=Lucida Console]o, you need to add your new user to the admin group. In a terminal, logged in as the old user with the broken home settings do:
```
sudo useradd -G admin audio video cdrom powerdev plugdev
```
That should be enough to get everything working.[/FONT]


---

### Post by iainr86 on 2008-03-13
Hmm that didn't seem to work, i got the same error message saying contact system administrator.
when you say in a terminal logged in as the old user, do you mean do it in recovery mode? Because it wont even let me log in to open up a terminal

when i try to log in to my broken account i get "user's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by the user and not writable by other users.

really wishing i hadn't messed about with this last night!!

---

### Post by Arthur Archnix on 2008-03-13
I mean when the system is booting up hit Ctrl+Alt+F1 to switch to a virtual terminal, where you should be able to log in and run these commands. If you can't then just boot up using recovery mode and run the commands sans "sudo" prefix.

---

### Post by iainr86 on 2008-03-13
ok i've done that and still the same message:

"Failed to run users-admin as user root.

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator"


Is there any way that i can make the user iain take control of the entire fat32 partition and not allow any other users access to it? Maybe that would let me log in as iain and change the setting back?

---

### Post by Oldsoldier2003 on 2008-03-13
> **iainr86 said:**
> ok i've done that and still the same message:

"Failed to run users-admin as user root.

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator"


Is there any way that i can make the user iain take control of the entire fat32 partition and not allow any other users access to it? Maybe that would let me log in as iain and change the setting back?

Though it may be possible to dig around and recover the system, for all intents and purposes the best way to recover after moving your /home directory to a NTFS or FAT partition is to reinstall Ubuntu. 

The underlying problem is that the NTFS and FAT don't support Linux permissions properly. Because of this  simply moving everything to an ext2/3 partition won't fix the permissions. The time you spend tinkering with it will vastly outweigh the time needed for a reinstall.

---

### Post by iainr86 on 2008-03-13
dammit thats what i was afraid of! oh well, it'll keep me busy at the weekend!!

---

