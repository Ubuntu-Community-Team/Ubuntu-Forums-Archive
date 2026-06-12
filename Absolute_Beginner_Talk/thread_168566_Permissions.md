---
title: "Permissions"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by moondogie on 2006-04-30
I would like to drag and drop some files onto my external hard drive BUT I get an n: "Error while copying to /media/Back...e/Martini's . You do not have permissions to write to this folder "
How do I get permission . I would like to clean up the H.D. and save some files to the external media . Thank you
](*,)

---

### Post by chriscando on 2006-04-30
My guess is that the hard drive is mounted as root. You can edit your /etc/fstab file so that you can mount it, or you can change permissions on the drive so any user can have read/write permission (this is probably easier/quicker).

From the terminal type:
sudo chmod 777 /location_or_hd/ -r
Any user should be able to read/write now.

---

### Post by annda on 2006-04-30
and there is the recurring question whether your HD is not formatted as NTFS. sorry if I'm bringing up the obvious but NTFS drives are not natively writeable by linux at all. it's just that I tried to tinker with /etc/fstab before realizing some things can't be done without tinkering with the whole system (like using experimental NTFS linux drivers).

hope it's just read/write permissions.

---

### Post by moondogie on 2006-04-30
that cammand didn't work . 777 . no such file or directory 
So I have to edit /etc/fstab ?

---

### Post by annda on 2006-04-30
seems you have a problem with the command itself or the path to your drive.

you should be able to do that without modifying fstab.

please post the exact command you've typed and possibly the contents of the /etc/fstab file.

---

### Post by moondogie on 2006-04-30
The command is : sudo chmod 777 /location_or_hd/ -r

---

### Post by 3rdalbum on 2006-05-01
[QUOTE=moondogie]The command is : sudo chmod 777 /location_or_hd/ -r[/QUOTE]

Don't actually put /location_or_hd/ into the command. You should substitute that for the actual location of the hard disk.

In Linux, disks are mounted in one of a number of locations in the file system. So, instead of accessing a disk using drive letters (i.e. C:\ or D:\), you would use (/media/disk_name) or (/mnt/disk_name) where *disk_name* is the name of the disk as it appears on the desktop.

So: Double-click on your hard disk icon. When the Nautilus window opens, click the little "<" arrow button underneath the Back button. Now you will see a number of new buttons pop up in that part of the window. Mine are (in order) a little picture of a disk which represents the Linux filesystem, "media", and "Polly" (which is the name of my hard disk). Each button is a subdirectory - so my hard disk therefore is mounted at the directory path "/media/Polly".

Look at your set of buttons there to find out the directory path where your disk is mounted. It always begins with a slash, and never ends with one. Now, put that into the command Chris Cando gave you.

---

### Post by Bernie01 on 2006-05-01
I have tried using this command and have substituted the correct location and disk name but I still get error message 'cannot access "777" : No such file or directory

---

### Post by AnRuaRi on 2006-05-01
print up here the exact command you're entering.

also if you type man chmod you will bring up the manual for the chmod command.
this tells us to use the following syntax:

       chmod [OPTION]... MODE[,MODE]... FILE...
       chmod [OPTION]... OCTAL-MODE FILE...
       chmod [OPTION]... --reference=RFILE FILE...

using 777 is attempting to use the OCTAL-MODE

try the following

sudo chmod -R +rwxugo [path of drive here]

the -R applies the command to all sub directories and files
the + adds the following list to the properties
r= read access
w= write access
x = execute access (or enter directories)
u= user (owner)
g = group
o = others

the above command should therefore give unrestriced access.

before you do this do double check that you're not attempting to mount an NTFS drive. this cannot safely be mounted with write access.

---

### Post by Prasad007 on 2006-05-01
i dont really understand giving paths in linux... used to c:\

---

### Post by ncappel1 on 2006-05-01
To do this in the GUI, open up a nautilus window as root via 
1)Applications-->system tools-->file browser (root), enter your password and navigate to where you are able to right click on the drive.
2) right click it and select properties, 
3)then simply change the permissions under the appropriate tab to allow others to write to the drive.

hope this helps!

definitely learn the command line way too, though, and figure out what you're doing wrong, becuase you'll be a better person for it!

---

### Post by aysiu on 2006-05-01
We still haven't established what filesystem this is. You can't chmod or chown a FAT32 or NTFS drive, and most external hard drives do not just show up as Ext3 unless you format them that way.

Plug in the external hard drive.

Then go to Applications > Accessories > Terminal (in Gnome) or KMenu > System > Konsole (in KDE) and copy and paste these commands in the terminal. Then copy and paste the output back here.

Here are the commands: ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

