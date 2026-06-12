---
title: "Windows 7 partitions"
date: 2011-04-13
forum: Any Other OS
---

### Post by nankura on 2011-04-13
hey guys

ok so basically, ive tried multiple programs and nothing works, and the partition manager in windows reads the drive but wont let me change anything

basically, i have 2 500GB hdd's, one has ubuntu, one has win7, i want windows 7, to read the ubuntu hard drive, without effecting the installation, so i can get a phew games and backup some data, and reinstall ubuntu

---

### Post by SecretCode on 2011-04-13
What are the file systems on each? By default Ubuntu installs with ext3 or ext4 file system. The windows partitions will be ntfs. Ubuntu can read and write ntfs partitions, but windows is unable to read ext3/4 partitions without extra drivers.

Is the Ubuntu install working? If so, boot that and copy the data from there. If not, best option may be to boot from an Ubuntu live CD and copy the data.

---

### Post by mips on 2011-04-13
ext2ifs driver for windows.

Or [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by horia_m on 2011-04-27
I have a similar problem: 
I can write data into NTFS partitions with Ubuntu, but I am unable to read them from within windows. Windows shows only fonders, with no acces to them, or showing no files inside the folders.
I am able to use or read these files alwasys from ubuntu, but not from windows.

If I write files from ubuntu to FAT external drives, I can read them later with windows.

(should I post this somewhere else?)

---

### Post by SecretCode on 2011-04-27
How were the ntfs partitions created? I have a feeling that best results are when you use windows to create ntfs partitions.

Other than that, I have not had any problems accessing files (except files created with illegal characters, especially colons, but so far those have only been rsync backups of files I only need in Linux anyway).

In Ubuntu, can you see files created in Windows?

When you go back to windows, can you still see files that previously existed?

---

### Post by horia_m on 2011-04-27
Hi, thanks for your fast answer! 
Yes:
1) I can access windows normally (in fact, the files Ubuntu wrote, were on an NTFS boot partition, done by Windows XP) and all its files
2) I can access windows files from within ubuntu also perfectly
3) I can access all the files that I created/moved, etc. when using ubuntu
4) I CANNOT access SOME files in SOME folders, created/moved with Ubuntu, when I am in Windows. I see just the main folder that contains those files, and I cannot access the subfolders, and I also cannot access the "properties" feature of the folder (windows says just "access denied" or similar). Those files were originally windows files, but I moved them to other locations on the same disk. So they should have "windows compatible" names and characters in their names.

I am no specialist in Ubuntu (a total beginner in fact) but I could imagine that there are some issues with ntfs settings for those files (access permissions) for some mysterious reason. 

I don't know if I told this before: I use a startup disk with Ubuntu 10.10. (wanted to install, but as I have these problems, I delayed the definitive installation on a separate disk partition)

Could it be that, perhaps, if Ubuntu does not exit/shutdown in a right way (this seems to happen sometimes), the just written files could get some problem with the access permission? (just an idea).

---

### Post by SecretCode on 2011-04-27
By startup disk do you mean a CD that boots Ubuntu? ie a "Live CD"

It could be something to do with mount options. Or it could be invalid file names - the linux ntfs driver does allow some illegal characters in ntfs file names, for unknown reasons.

Running Ubuntu, what is the output of the following commands:
```
mount
```
```
sudo blkid
```

And perhaps also paste here the full path of a file or directory that is visible in Ubuntu but not in Windows. 

To your last point, yes it is important to unmount the ntfs volume properly. This will happen during a normal shutdown of Ubuntu, but not if you just power-cycle...

---

