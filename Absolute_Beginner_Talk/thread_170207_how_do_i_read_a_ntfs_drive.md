---
title: "how do i read a ntfs drive?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Vlatko on 2006-05-04
?? i don't need to be able to write to it, just read it. cause there is where all my music and mp3's are. i'm a total noob btw, i heard i have to mount it. the easiest way will do.

thanks!:mrgreen:

---

### Post by rado_london on 2006-05-04
The easiest way is [here!]("http://ubuntuguide.org/#automountntfs")
Good luck

---

### Post by Buffalo Soldier on 2006-05-04
From the user documentation -> [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by rado_london on 2006-05-04
I always forget that user documentaton. Shame on me!

---

### Post by Vlatko on 2006-05-04
is there a chance of making my drive(ntfs) unusable by doing that?

---

### Post by Jimmey on 2006-05-04
You can't write to an NTFS drive - But when you mount it, you can read all the files you like. :P

---

### Post by Vlatko on 2006-05-04
[QUOTE=Jimmey]You can't write to an NTFS drive - But when you mount it, you can read all the files you like. :P[/QUOTE]
i know but these commands tend to make a newbie like me really nervous and wanting to say to hell with it all i'm going back to windows. i have  one hard disk that has 110gb really important stuff in it, no os's, which i use daily. i don't wanna loose that because of some ubuntu experimenting.

---

### Post by rado_london on 2006-05-04
When you have read only permissions you cannot fcuk anything. But again use the method on your behalf. And a tip- if you are so scared doing stuff like that you shouldnt use linux- its just clear pain for people wwho dont want to learn and try new stuff.

Good luck

---

### Post by mips on 2006-05-04
[QUOTE=Vlatko]i know but these commands tend to make a newbie like me really nervous and wanting to say to hell with it all i'm going back to windows. i have  one hard disk that has 110gb really important stuff in it, no os's, which i use daily. i don't wanna loose that because of some ubuntu experimenting.[/QUOTE]


You know what scares me, people without backups !

You have zero gaurantee that your drive will not crash, die, corrupt or whatever for any unforseen reasons. Things break, therefore it is a good policy to have backups.

---

### Post by Jimmey on 2006-05-04
I've, quite lazily, not bothered to click the link. I'll explain, in depth, how I'd mount a drive.

The first command I'd use would be 
> sudo fdisk -l

And the output of this should make it fairly obvious which partition ( or drive ) I am mounting. I'll use an example from my PC - my 5.10 partition, with an ext filesystem.
Here's my output:
> sujames@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 50.0 GB, 50018393088 bytes
255 heads, 63 sectors/track, 6081 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2802    22507033+  83  Linux
/dev/hda2            5077        5295     1759117+   5  Extended
/dev/hda3            5296        6081     6313545   83  Linux
/dev/hda4   *        2803        5076    18265905   83  Linux
/dev/hda5            5077        5295     1759086   82  Linux swap / Solaris

Partition table entries are not in disk order


My 5.10 install is on /dev/hda1 - And yours will be on the one marked "Windows", "NTFS", or similar.

When you've established that, then you can mount the drive ( which will not erase, or otherwise change the data on the drive ).

You first need to pick a destination. Mine's /home/5.10, because I created a directory to suit the purpose of mounting this drive. If you'd like to do the same, you can execute the command 
> sudo mkdir /home/windows
which will create a directory in /home called "windows" ( even though Windows may not be on the drive, it's just a word to use so that it's recognisable ).

Now, to mount the partition to that directory, you'll use the mount command.
In my case, the command will look like this:
>  sudo mount -t ext3 /dev/hda1 /home/5.10

But in your case, you'll replace ext3 with "ntfs", and /home/5.10 with the place you'd like to mount this drive. It might look something like this:
> sudo mount -t ntfs /dev/hda1 /home/windows

When you're done with that drive / partition, you can unmount it using the umount command:

> sudo umount /dev/hda1

Although it seems like a lot of commands, you quickly get used to them. I promise.

---

### Post by rado_london on 2006-05-04
In depth explanations scare noobs more than anything. But this is good explanation and I think it is helpful.

---

### Post by MHlavsa on 2006-05-04
I mounted my windows drive according to the [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

After I restarted, as Ubuntu listed all processes.........................ok, something about local drives or whatever failed, and when I go to File System/Media/windows, i see (*empty*)

What went wrong?

---

### Post by MHlavsa on 2006-05-04
Good news!  I just fixed it (I'm becomming less noobie every day, how exciting!)

For the record, and anyone who runs into the same problem.

After running 
"sudo mount -a" it output that 
"mount: special device /dev/hda1 does not exist", so I figured /hda1 was incorrect, which I was right on.

I installed Gparted, and checked what the windows drive was for me, which for some reason was /sda2, so I ran
"sudo gedit /etc/fstab", replaced /hda1 with /sda2, ran
"sudo mount -a" again, and poof, windows drive!

---

### Post by ComplexNumber on 2006-05-04
i've just enabled the ability to read the windows directory. 
1) install the packages: ntfsprogs, kmod-ntfs, ntfs-kmod-common, ntfs-vfs2-gnome

[B]2) MAKE A BACKUP COPY OF THE /etc/fstab FILE (ultra important! don't mess up this file and keep it safe!)
[/B]
3) add the following line to fstab and save
"/dev/hda1   /media/windows  ntfs  umask=0000    0 0"

the "umask=0000" just means that everyone can write(if possible) and read windows directory.

4) created the directory /media/windows

5) cd'd into the /media directory and typed:
"mount -a"

6) rebooted.

---

### Post by rado_london on 2006-05-04
Told you people.It isnt that hard. Well done for the workarounds. It is so nice when you discover something!

---

