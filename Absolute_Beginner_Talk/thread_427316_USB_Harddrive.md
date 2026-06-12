---
title: "USB Harddrive"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Amru on 2007-04-29
[SIZE="3"][FONT="Arial Black"][COLOR="Blue"]I have just installed Feisty Fawn on my laptop. I've never used Ubuntu before, so I'm sure that there will be a sharp learning curve. Looking through these forums, however, shows me that I am not alone and that there are a lot of patient experienced Ubuntu experts willing to help out.

My first question I have is in regards to my external Seagate 160 GB harddrive. I formatted it using GParted and set the filesystem as ext3. When I attempt to write to the harddrive, it says that I do not have permission to to this. I've repeatedly tried both sudo chmod and chmod, but get error messages saying I do not have permission to do this.

How do I set the permissions for an external harddrive (or device)? I'm the owner, and I just want to be able to use my harddrive.

Thanks for your time, patience, and tireless efforts! :) 

[/COLOR][/FONT][/SIZE]

---

### Post by taurus on 2007-04-29
Where do you mount that external harddrive, mount point?  What's the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
id
df -h
```

---

### Post by Amru on 2007-04-29
[SIZE="3"][COLOR="Blue"][FONT="Arial Black"]I get:[/FONT] 
[/COLOR][/SIZE]
Amru@Demons-Dream-of-Freedom:~$ id
uid=1000(Amru) gid=1000(Amru) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(Amru)
Amru@Demons-Dream-of-Freedom:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              88G  2.2G   82G   3% /
varrun               1010M  104K 1009M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
procbususb           1010M  140K 1009M   1% /proc/bus/usb
udev                 1010M  140K 1009M   1% /dev
devshm               1010M     0 1010M   0% /dev/shm
lrm                  1010M   33M  977M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb1             147G  188M  140G   1% /media/disk
Amru@Demons-Dream-of-Freedom:~$

---

### Post by taurus on 2007-04-29
Do

```
sudo chown -R Amru:Amru /media/disk
ls -la /media
```

---

### Post by josefismael on 2007-04-29
taurus - i'm running into the same issue. When I run the first command you suggested (with my device and username info, of course) i get the following for each file and folder (one example):
[B]
chown: changing ownership of `/media/hda5/reinstall 4.27.07/Program Files/Windows Resource Kits/Tools/regini.exe': Read-only file system[/B]

when i run the second command, i get a **bash: la: command not found**

one thing to note is that this drive is actually a partition of my primary hdd and it had its security permissions set on it in a windows environment - hopefully there's a workaround : )

any tips? thanks in advance....

jm

---

### Post by taurus on 2007-04-29
Is your /dev/hda5 an ntfs filesystem?  You can't change ownership with chmod for ntfs or vfat.

```
sudo fdisk -l
```

---

### Post by Amru on 2007-04-29
[FONT="Arial Black"][SIZE="3"][COLOR="Blue"]From that, I get:[/COLOR][/SIZE][/FONT]

chown: invalid option -- l
Try 'chown --help' for more information.

---

### Post by taurus on 2007-04-29
Can you post the exact command that you ran?

---

### Post by Amru on 2007-04-29
[FONT="Arial Black"][COLOR="Blue"][SIZE="3"]I ran:
[/SIZE][/COLOR][/FONT]
```
Amru@Demons-Dream-of-Freedom:~$ sudo chown -R Amru:Amru /media/disk
ls -la /media
```

---

### Post by josefismael on 2007-04-29
(hey don't mean to hijack this thread, let me know if you want me to post this elsewhere)

yes it is ntfs - Is there any way around this? If i hook the device up to a windows machine and pull ALL security restrictions off of it, will ubuntu still be able to assign permissions to the filesystem? or do i HAVE to reformat?

thanks again

jm

---

