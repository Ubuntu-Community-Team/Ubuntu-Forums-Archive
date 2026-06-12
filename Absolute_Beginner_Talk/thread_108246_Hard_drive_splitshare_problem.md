---
title: "Hard drive split/share problem"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by hojimoe on 2005-12-25
Hey, yes I'm new to Ubuntu, i just installed 5.10 last night after getting the cd's in the mail :D

anyway, what I have is two hard drives.  one 80GB (main with windows), and a 100GB secondary, 80GB storage for windows, 20GB for Unbuntu....

I have a boot up menu (choose OS, duh ;))

anyway, i need to access my other harddrive / other partition to get at some of the files, I never had problems when I used other distro's before, maybe it was just a default from those ones. does anyone know how I can access my other drives so i can get at like my music and stuff? 

thanks in advance, I know its a dumb question but I couldn't find my answer :S

btw Im using ext3 for unbuntu partition and NTFS for all the others (windows did it..lol)

---

### Post by Snakey on 2005-12-25
Hi, you'll have to configure this manually, here's a howto from the [Ubuntuguide]("http://www.ubuntuguide.org/#mountunmountntfs"):

   [Q: How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?]("http://www.ubuntuforums.org/")[LIST=1]
[*]Read [General Notes]("http://www.ubuntuguide.org/#generalnotes")
[*]Read [How to list partition tables?]("http://www.ubuntuguide.org/#listpartitiontables")
[*]e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows
[*]To mount Windows partition     sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
[*]To unmount Windows partition     sudo umount /media/windows/[/LIST][Q: How to mount/unmount Windows partitions (FAT) manually, and allow all users to read/write?]("http://www.ubuntuforums.org/")[LIST=1]
[*]Read [General Notes]("http://www.ubuntuguide.org/#generalnotes")
[*]Read [How to list partition tables?]("http://www.ubuntuguide.org/#listpartitiontables")
[*]e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
     Local mount folder: /media/windows
[*]To mount Windows partition     sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
[*]To unmount Windows partition     sudo umount /media/windows/[/LIST][Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?]("http://www.ubuntuforums.org/")[LIST=1]
[*]Read [General Notes]("http://www.ubuntuguide.org/#generalnotes")
[*]Read [How to list partition tables?]("http://www.ubuntuguide.org/#listpartitiontables")
[*]e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows
[*]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
[*]Append the following line at the end of file     /dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
[*]Save the edited file ([sample]("http://www.ubuntuguide.org/sample/fstab_automountntfs"))
[*]Read [How to remount /etc/fstab without rebooting?]("http://www.ubuntuguide.org/#remountfstabwithoutreboot")[/LIST][Q: How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write?]("http://www.ubuntuforums.org/")[LIST=1]
[*]Read [General Notes]("http://www.ubuntuguide.org/#generalnotes")
[*]Read [How to list partition tables?]("http://www.ubuntuguide.org/#listpartitiontables")
[*]e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
     Local mount folder: /media/windows
[*]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
[*]Append the following line at the end of file     /dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
[*]Save the edited file ([sample]("http://www.ubuntuguide.org/sample/fstab_automountfat"))
[*]Read [How to remount /etc/fstab without rebooting?]("http://www.ubuntuguide.org/#remountfstabwithoutreboot")[/LIST]

---

