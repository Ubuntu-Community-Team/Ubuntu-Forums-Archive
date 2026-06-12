---
title: "having problems setting permissions"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by n9uib on 2005-10-14
Hello all...

   Linux n00b here, with a question that i think can be answered very easily by one of the "uber geeks".

I am trying to retrieve mp3, pics, ect from hda1 (windows partition) and i have went and made a folder and went into system-admin-disk- and pointed the win partition to the folder i wanna use to retrieve the stuff off hda1......    but i am getting "you dont have permission to view" and when i look in the properties... its owned by root....   

Any ideas how to make it owen by me ????

steve

---

### Post by n9uib on 2005-10-14
Well, after i sent this.... i went looking and figured out how to do it.... sorry for the bandwith..... still trying to get in the swing of things.....

GREAT DISTRO........

steve

---

### Post by flash on 2005-10-14
OK, let me sake a stab at it.I'm a newbie also so use this info at your own risk. I think what you want to do is use the command "sudo" before everything on the command line. That makes you a "super user" and is suppose to work. I hear you don't wnat to do anything as root. I've had about 0% experience with this but I've read some of the other threads and it sounds like the same stuff. I like looking through some of the threads other people have written and read the ones that sound like they are similar.

---

### Post by LHZ on 2005-10-14
Just tot correct/expand on the previous post:

You can change the owner of a file with the command 'chown'. Start a command line, and type

> sudo chown <username> <file or dir name>

Example:

> sudo chown johndoe readme.txt

The sudo command executes the rest of the line with root privileges. In the case of 'chown', this prevents random people from 'donating' files to root, giving them more permissions. To prevent this sort of thing only root can change file ownership.

You could also try

> sudo cp /dev/hda1/stuff /home/stuff

This simply executes the 'copy' command (cp) with root privileges.

You  generally want to minimize the time you spend as root. As root it's easy to accidentaly delete or mess up critical system files if you type the wrong thing. Normal users don't have write access to those critical files, and therefore can't hurt them. This is why using 'sudo' on a few commands is safer than logging in as root: you minize the potential for accidents.

---

### Post by n9uib on 2005-10-14
Thanks for the help everyone..... i got it........    man, i love "breezy".... makes life a bit more simple


steve

---

### Post by Freddie.Ruddick on 2005-10-14
Hi, similar problem here.

I have BB on one PC, and WinXP on another. The WinXP machine still has all of my MP3s on and will remain in use for the forseeable future. I have mounted the shared MP3s folder and got read/execute access (755). I want to give myself write permissions. 

I tried a chown, both with sudo, and from the root terminal, but got 
```
chown: changing ownership of `/home/freddie/Music': Operation not permitted
```.

If I try to 777 it, I get no feedback from the CLI, and the permissions remain the same.

Please Help!

Thanks

Freddie

---

### Post by LHZ on 2005-10-14
Freddie.Ruddick:

Did you mount the WinXP partition with read/write access?
(You can check this in the file /etc/fstab) .

---

### Post by Freddie.Ruddick on 2005-10-14
[QUOTE=LHZ]Freddie.Ruddick:

Did you mount the WinXP partition with read/write access?
(You can check this in the file /etc/fstab) .[/QUOTE]
Don't think so, I mounted it manually from the CLI. Here is my fstab just in case it helps:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by LHZ on 2005-10-14
Is the Windows filesystem Fat32 (vfat) or NTFS? Linux can read NTFS, but not write to it. If you're not sure, you can check with 

> sudo fdisk -l

which lists everything you have mounted.

---

### Post by Freddie.Ruddick on 2005-10-14
Ahh. It's NTFS. Have got it to automount by editing fstab though. I think I'll attack the 200GB Windoze partition with Partitionmagic and make a nice FAT32 partition.

---

### Post by dubski on 2005-10-14
This worked for me, from [http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs")

Follow these steps to make Ubuntu automatically mount your windows partition and give all users read access.

1. Make the mount point.
[COLOR="Blue"]
sudo mkdir /media/windows[/COLOR]

2. Edit your fstab.

[COLOR="Blue"]sudo gedit /etc/fstab[/COLOR]

3. Include this line in your fstab.  Change relevant details to suit your setup.

[COLOR="Blue"]/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0[/COLOR]

---

### Post by Freddie.Ruddick on 2005-10-15
Thanks dubski, but it's not on the same disk, It's on a seperate computer. I've got read access, but I wanted write access... Ah well, out comes the partitionmagic disk.

---

