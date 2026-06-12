---
title: "mount/unmount hfs and hfs+"
date: 2004-11-15
forum: Apple PPC Users
---

### Post by trash on 2004-11-15
Can anybody tell me why I can mount, read/write but I can't unmount... it always tells me that the devices are busy

etc/fstab:
dev/hda10      /mnt/macos      hfs     defaults,noauto,user,rw  0       0 
dev/hda11      /mnt/macosx     hfsplus defaults,user,noauto     0       0 


thanks

---

### Post by trash on 2004-11-15
answer:

remove 'defaults'

 \\:D/

---

### Post by sumanjay on 2004-11-16
Darn! Beat me to the answer... :wink:

---

### Post by trash on 2004-11-16
no worries bro, i can almost promise you'll get another chance...

thanks anyway;)

---

### Post by Brian McConnell on 2004-11-27
I am trying to have my two mac partitions show up under the /mount folder in my Ubuntu PPC operating system.
I have so far done:
mkdir /mnt/macboot  <-----for my "main" mac partition, formatted as HFS
mkdir /mnt/110gbHFS  <----for my +/-100gb storage partition, formatted as HFS

Here's the output of fdisk -l:
root@ubuntu:/home/brian # fdisk -l
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_UNIX_SVR2 swap                  262144 @ 64        (128.0M)  Linux swap
/dev/hda3               Apple_HFS Apple_HFS_Untitled_7  64749568 @ 262208    ( 30.9G)  HFS
/dev/hda4              Apple_Free Extra                   2048 @ 65011776  (  1.0M)  Free space
/dev/hda5         Apple_Bootstrap bootstrap               2048 @ 65013824  (  1.0M)  NewWorld bootblock
/dev/hda6              Apple_Free Extra                 258048 @ 65015872  (126.0M)  Free space
/dev/hda7               Apple_HFS Apple_HFS_Untitled_8 215850688 @ 65273920  (102.9G)  HFS
/dev/hda8         Apple_UNIX_SVR2 Linux ext3          31445312 @ 281124608 ( 15.0G)  Linux native
/dev/hda9              Apple_Free Extra                  11888 @ 312569920 (  5.8M)  Free space


Here's my /etc/fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda3       /mnt/macboot    hfs     defaults,umask=0,quiet 0 0
/dev/hda7       /mnt/110gbHFS   hfs     defaults,umask=0,quiet 0 0


Now, when I view the macboot or 110gbHFS folders, they are empty. 
In terminal I typed:
mount /mnt/macboot
mount /mnt/110gbHFS

each time I received the following reply:
mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       or too many mounted file systems

 wrong fs type, bad option, bad superblock on /dev/hda7,
       or too many mounted file systems


So, I need a bit of help here! I have my directories showing up in the /mnt directory, but no data inside. How can I get access to my drives?

I am a newbie, and thought it may be better to use this thread rather than start a new one.
I appreciate any support.
Thanks!!

---

### Post by trash on 2004-11-27
howdy Brian,
I would try...

/dev/hda3 /mnt/macboot hfs noauto,user,rw 0 0
/dev/hda7 /mnt/110gbHFS hfs noauto,user,rw 0 0

I'm not sure what 'umask=0,quiet' is supposed to do but i guess you can keep it in there and see if it works:)

---

### Post by Brian McConnell on 2004-11-27
Thanks for the suggestion. I cut and pasted it into fstab. still same reply as previous. I'm a bit stumped as I've used this method on a pc Ubuntu install with no probs. I'm wondering if there is a problem if, say, the partitions are HFS with journaling enabled.
:scratching head:

I'm wondering about the bad superblock possibility and what it means. Is it something that is correctable?

---

### Post by trash on 2004-11-27
i still get that 'bad superblock' with my cd sometimes and i used to get it with my mac partitions until I finally got the fstab right.... dunno what to say it looks like it should go... have you tried restarting?

---

### Post by Brian McConnell on 2004-11-28
yep, restarted. still no luck. I'm out of ideas, myself.

---

### Post by J_Sine on 2004-11-28
Make sure when you run the mount command in the terminal you also point it
to a device and not just the mount point like this:

mount /dev/hda3 /mnt/macboot
mount /dev/hda7 /mnt/110gbHFS

The /dev/hda# part tells the mount command which device contains the
filesystem you want to mount at the specified mount point. You may already
know this but I just wanted to make sure. Also, you may have to specify what
type of filesystem you are trying to mount so you could enter your command like this:
mount -t hfsplus /dev/hda3 /mnt/osx

---

### Post by Brian McConnell on 2004-11-28
[QUOTE=J_Sine]Make sure when you run the mount command in the terminal you also point it
to a device and not just the mount point like this:

mount /dev/hda3 /mnt/macboot
mount /dev/hda7 /mnt/110gbHFS

The /dev/hda# part tells the mount command which device contains the
filesystem you want to mount at the specified mount point. You may already
know this but I just wanted to make sure. Also, you may have to specify what
type of filesystem you are trying to mount so you could enter your command like this:
mount -t hfsplus /dev/hda3 /mnt/osx[/QUOTE]
That worked! Thanks so much! Now, my question is: can you explain what the -t is for? Great help from both trash and J_Sine. Also, I used the text as you typed it (with appropriate changes), J_Sine, even though, to my knowlege, the partitions are HFS and not HFS+. So, we'll see what I can learn from this.

I'm going to reboot now to see if the partitions reappear after reboot.

After reboot, partitions are not mounted. What can I do to make them automount at startup?

---

### Post by trash on 2004-11-28
Hmmm, i still don't get why your setup is so dif from mine.. strangeness.

check out the man pages... # man mount

I'm not sure if auto mounting is such a great idea though, but i guess if you're not worried about potential data loss it's no big deal.

---

### Post by J_Sine on 2004-11-28
Yeah sorry about that. I typed the command how I would type it in the terminal and forgot to change the
variables for your setup!  :oops:  
By all means, using hfs instead of hfsplus will work as well. And for automount, I have a line like this in my 
fstab to mount my OS X partition on boot:
/dev/hda3         /mnt/osx         hfsplus           rw,exec,auto,users   0         0
hda3 is my OS X partition and osx is the mount point I made for it.
The rw make it readable and writeable, the auto is the automount part and users allows all users to access it.
You could also mount it with ro instead of rw which will make ir read only, or you could change the users to
root to only allow the root user to access it. I'm still very much a newbie at linux so I too am still learning
as I go. Good luck!

---

### Post by eggie on 2004-11-29
i have my osx disk mounted but i am unable to access my files because of permissions. Anyone know how i can change permissions so as to be able to access my movie and music files?
Thanks

---

### Post by eggie on 2004-11-29
scrap that just changed permissions under os x easy as pie

---

### Post by Brian McConnell on 2004-11-29
[QUOTE=trash]Hmmm, i still don't get why your setup is so dif from mine.. strangeness.

check out the man pages... # man mount

I'm not sure if auto mounting is such a great idea though, but i guess if you're not worried about potential data loss it's no big deal.[/QUOTE]
I dunno! I'm running a 1ghz eMac /ATI RV200. Actually, though, I am awaiting the arrivial of my new dual 1.8ghz G5 tower. So, once I get Ubuntu on *that* mac, I'll be modifying fstab again and will try to post my findings here (just in case we find another set of commands to mount the HFS parts).
So, thanks a lot for the help! Ya'll may not find me in the ppc forum until after my new mac arrives. In the meantime, I've got to figure out how to get k3b to recognize my cd burner. It sees it only as a reader, this is on my pc. I couldn't find a k3b for mac.....
Linux newbie forever!

---

### Post by nickfull on 2005-09-09
[QUOTE=J_Sine]Yeah sorry about that. I typed the command how I would type it in the terminal and forgot to change the
variables for your setup!  :oops:  
By all means, using hfs instead of hfsplus will work as well. And for automount, I have a line like this in my 
fstab to mount my OS X partition on boot:
/dev/hda3         /mnt/osx         hfsplus           rw,exec,auto,users   0         0
hda3 is my OS X partition and osx is the mount point I made for it.
The rw make it readable and writeable, the auto is the automount part and users allows all users to access it.
You could also mount it with ro instead of rw which will make ir read only, or you could change the users to
root to only allow the root user to access it. I'm still very much a newbie at linux so I too am still learning
as I go. Good luck![/QUOTE]

I've had no luck accessing files in my OSX users folder using this method. I have in fstab :
/dev/hda12         /mnt/macos         hfsplus           rw,exec,auto,users   0         0
With this I can see the disk has mounted successfully but the folder I'd like to access has a red 'x', and won't open.

Any ideas why it doesn't work?

---

