---
title: "How do i remove CD-ROM 1 and CD-ROM 2 from showing up in GUI?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Dred79 on 2007-07-27
I have Ubuntu 7.04 Fiesty fawn and i moved all my hardware to a new smaller case. I got rid of both of those cdrom drives but they still show up in ubuntu.  How can i get rid of them?
It says /dev/hda does not exist when i try to access them but they still show up.


I have one other question as well. I added a 500gb ext3 drive and everytime i login into ubuntu its never mounted and always asks me for password to mount it. Once its mounted i only have read access and cannot write or create folders. How can i get it mounted by default and give me write permissions to this drive always?

Thanks.
Sincerely 
Windows expert convert to Linux newbie

---

### Post by Pragmatist on 2007-07-28
I'm going to help you with the hard drive first.  Please post your **/etc/fstab**

---

### Post by Dred79 on 2007-07-28
Thanks for replying. It's these basic things in linux that drive me nuts. They are simple questions with simple answers. I just wish these simple things would have a GUI by now. Having to know the command and search for it on google or reading the faq for something that should be easy just kills me. 

anyway here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=36df3709-5775-4f83-9f3d-99f11fceb589 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=B8ACD97AACD9339A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=15b71b0f-3b03-4ded-80ee-0f29b565c0cc none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0



I notice my cdroms are listed here. I am assuming i can delete them so they do no show up. my 500gb hard drive is /dev/sdb1 and i is not listed. =( how would i add that in there?

---

### Post by Trebaruna on 2007-07-28
I hope Pragmatist won't mind my butting in, but I see you have at least one NTFS drive.
If you want full NTFS read/write access, you should install ntfs-3g, and for easy configuration also ntfs-config.
If you get those two (they are in Universe, so in 7.04 just open Synaptic and look for them) there should be an option under system tools in the applications menu which you can use to easily assign mountpoints to NTFS volumes.

---

### Post by Dred79 on 2007-07-28
Thanks Trebaruna. Its nice having some write access to windows. I am a gamer and already have Cedega. I was wondering what the perfomance of ntfs might be in linux. I have not had time to test this yet but my idea is to mount a game partition in either ntfs or ext3 and have windows and linux share the same game folders. Right now i have something called ext2ifs installed on windows and i have already played games from ext3 partition and it ran quite well. i have not tested linux yet. But i assume its better if linux runs games on ext3 and not ntfs.

I hope to hear from ya soon Pragmatist. I rather wait for your expertise on mounting my 500gb with write permissions than reading hundreds of pages on the internet. Course i will eventually do whatever it takes to fix that.  =)

---

### Post by Pragmatist on 2007-07-28
> **Dred79 said:**
> 
I notice my cdroms are listed here. I am assuming i can delete them so they do no show up. 

I think it is worth a shot.  Just back up /etc/fstab first:
```
sudo cp /etc/fstab /etc/fstab.backup 
```> **Dred79 said:**
> 
my 500gb hard drive is /dev/sdb1 and i is not listed. =( how would i add that in there?

To answer that I need to know:

1.  filesystem type 
2. What permissions you want to mount the drive with: read-only, read/write, do you want to give particular users or groups some rights and exclude others? what default permissions do you want files to be created with by default?

3. Do you want to use a specific encoding?  UTF8?
4. Do you want to use UUID?  If so, we need to find out what it is (this shouldn't be hard, I just have to look it up to remind myself how to do it)

Relevant reading:
```
man mount
```
```
man fstab
```
```
man udev
```
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[https://help.ubuntu.com/community/Fstab?highlight=%28fstab%29](https://help.ubuntu.com/community/Fstab?highlight=%28fstab%29)
[https://help.ubuntu.com/community/Fstab?action=fullsearch&context=180&value=mount&titlesearch=Titles](https://help.ubuntu.com/community/Fstab?action=fullsearch&context=180&value=mount&titlesearch=Titles)

---

### Post by Dred79 on 2007-07-29
1. Ext3
2. I am the only one using my computer i just want my user account to have full access to the drive as i like to dump all my large files to this 500gb it also helps as a backup.
3. I have seen that encoding mentioned several times somewhere maybe when burning dvds and stuff but not clear on what it does exactly or why i would want it.
4.UUID i am not clear what that is either. =) This is for personal use no work related.

btw i removed the cdrom drives from fstab and the cdrom drives no longer show up! w00t! =) so now i don't have non exist drives showing up in my gui.

Btw looking at my fstab there is a line i do not understand.

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=36df3709-5775-4f83-9f3d-99f11fceb589 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=B8ACD97AACD9339A /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=15b71b0f-3b03-4ded-80ee-0f29b565c0cc none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0

Its funny i removed the last two lines and they are showing up again after editing fstab to remove them and rebooting. anyway the line that says unknown device what is that refering to?

---

### Post by Pragmatist on 2007-07-29
> **Dred79 said:**
> 
Its funny i removed the last two lines and they are showing up again after editing fstab to remove them and rebooting. anyway the line that says unknown device what is that refering to?


The "unknown device" didn't appear in the fstab you previously posted?  After you removed the last two lines, it suddenly appears?  Weird.  Are you also saying that the last two lines, for the phantom drives, reappear in fstab, even after you removed them?  Also weird.  Backup your fstab and then try this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
** /dev/sda5 /               ext3  defaults,errors=remount-ro 0       1**
[COLOR=Blue] #UUID=36df3709-5775-4f83-9f3d-99f11fceb589 /               ext3    #defaults,errors=remount-ro 0       1[/COLOR][B]
/dev/sda1 /media/sda1     ntfs defaults,nls=utf8,umask=007,gid=46 0 1[/B]
[COLOR=Blue]#UUID=B8ACD97AACD9339A /media/sda1     ntfs    #defaults,nls=utf8,umask=007,gid=46 0       1[/COLOR]
** /dev/sda6 none            swap    sw              0       0**
[COLOR=Blue] #UUID=15b71b0f-3b03-4ded-80ee-0f29b565c0cc none            swap    sw              0       0[/COLOR]
[COLOR=Silver][B] /dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0[/B][/COLOR]

The lines in blue you just put a hash mark (#) in front of them.
The lines in bold you add.
The lines in light-gray you remove.

---

### Post by Pragmatist on 2007-07-29
I forgot to add a line for your "unknown" drive:
**/dev/sdb1 **[B]/media/sdb1               ext3  defaults,errors=remount-ro 0       1

[/B]You must make a directory called "sdb1" in the /media directory:
```
sudo mkdir /media/sdb1
```

---

### Post by Dred79 on 2007-07-29
well i hope i did it right. here is my fstab now. btw the last fstab i posted i accidently edited my backup. heh. =P

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/dev/sda5 / ext3 defaults,errors=remount-ro 0 1
#UUID=36df3709-5775-4f83-9f3d-99f11fceb589 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
#UUID=B8ACD97AACD9339A /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1

/dev/sdb1 /media/sdb1 ext3 defaults,errors=remount-ro 0 1
#UUID=15b71b0f-3b03-4ded-80ee-0f29b565c0cc none swap sw 0 0

anyway i have my 500gb automatically mounted which is nice however i still only have read access. says i do not have permissions when i try to copy stuff to it. After i added your changes ubuntu did a long extensive disk check on bootup tok so long i thought it was doing a bad sector scan or something. did any of the lines i added in fstab force a check on every boot?

---

### Post by Pragmatist on 2007-07-29
> **Dred79 said:**
> ....i still only have read access....
My mistake.  

This:  
/dev/sda5 / ext3 defaults,errors=remount-ro 0 1

Should be this:
[B]/dev/sda5 / ext3 defaults,rw 0 1

[/B]You left out the line for your swap partition:
[B] /dev/sda6 none            swap    sw              0       0
[/B]

---

### Post by Dred79 on 2007-07-29
ok i made those changes but i still only have read only access to /dev/sdb1. So i take i can just change /dev/sdb1 from ro to rw and i will get write access? i am gonna try that and reboot.

---

### Post by Dred79 on 2007-07-29
Thanks for the help i figured out how to get read write access for my 500gb drive. i had to type sudo nautilus and go to media/sdb1 or whatever hard drive partition your trying to get read write access to and enable create and delete / read and write for everyone under permissions tab. Finally =) 

anyway here is my fstab for reference now i got the basic annoying issues out of the way its time to play around with cedega and windows gaming. =) 

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/dev/sda5 / ext3 defaults,rw 0 1
/dev/sda6 none swap sw 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
/dev/sdb1 /media/sdb1 ext3 rw,errors=remount-ro 0 1

---

