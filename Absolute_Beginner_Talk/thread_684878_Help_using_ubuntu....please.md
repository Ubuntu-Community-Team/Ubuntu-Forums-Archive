---
title: "Help using ubuntu....please"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by tomaso18 on 2008-02-01
hi,I am a brand new beginner with ubuntu,a friend of mine left me the cd so that I could save my machine.
I am trying to find out how can I move my precious folder from my machine (which needs to be reformatted)to an external HD using ubuntu.
My friend did it once but now unfortunately I need to do it again........by myself.:(
knowing that I am knew to Ubuntu could you please be very precise with the information I need? Please don't assume that I know because I don't.......windows is something Ubuntu is something else.
I can see my document but I cannot move them on the external HD......it says that I don't have permission  to write to the HD.

My friend did it so easily. Is there someway around it?

thank you very much in advance for your help.

thomas

---

### Post by jan quark on 2008-02-01
1.

open the terminal

and copy these commands one after the other and post the result here

the first command navigate us to the media folder where all mounted devices are displayed

if this folder is empty (I dont think so) and the second command will show nothing

use this command instead

2.

```
cd /media
```

2b)

```
cd /mnt
```



this command will tell us what permissions are set to the specific mounted devices
and what we must change
3
```
ls-l
```

---

### Post by tomaso18 on 2008-02-02
Hi thank you very much for answering,I have followed your instructions and this is the result:
ubuntu@ubuntu:~$ cd /media
ubuntu@ubuntu:/media$ cd /mnt
ubuntu@ubuntu:/mnt$ ls-l
bash: ls-l: command not found
ubuntu@ubuntu:/mnt$ 
 did I do something wrong?

thanks

thomas

---

### Post by lswest on 2008-02-02
well, first off, you're meant to change directory ("cd") to /media first then run ```
ls -l
``` (there is a space between the "ls" and the "-l") and see if the folder is empty (which it shouldn't be) but if it is, then you're meant to do ```
cd /mnt
``` and to run ```
ls -l
``` again, to see if the folders are there that you want.  post back the results^^

---

### Post by tomaso18 on 2008-02-02
thanks again for your help, this is the result;

ubuntu@ubuntu:/media$ ls -l
total 12
dr-xr-xr-x 1 root root 4096 2008-01-30 17:56 disk
drwxr-xr-x 2 root root   60 2008-02-01 20:27 lrwxrwrwxrwx
drwxr-xr-x 2 root root   60 2008-02-01 20:22 newfile
dr-xr-xr-x 1 root root 8192 2008-01-10 19:06 ThomasNewDrive
drwxr-xr-x 2 root root   60 2008-02-01 20:18 usb
ubuntu@ubuntu:/media$ 


I have created "newfile" by mistake
lrwxrwxrwxrwx- I don't know what it is
usb must be there by mistake,too because is empty.
thomasnewdrive is the external HD where I would like to move my files  
disk is my laptop which I need to reformat

thank you very much

thomas

---

### Post by lswest on 2008-02-02
well, since you're re-formating anyways, we can just ignore the files you created by accident (the usb folder is where your usb gets mounted, once you insert it).  now to continue, do ```
cd disk
```, which will change directory to the drive where your files are.  Then navigate with cd to the folder/file you want to copy. (e.g. cd disk; ls (lists the files); pick the folder you want to navigate to, cd to that folder, until the folder you want to back up appears in ls) then run ```
tar cvpzf backup.tgz [name of folder]
``` which will create a tar archive of the folder (an archive, can be opened with winrar i believe), and to copy that to your external drive do ```
cp backup.tgz /media/[name of external drive]/[path to where you want it saved] (such as /media/ThomasNewDrive/backup/)
``` or, if you don't want to create an archive of the folder, just copy it with ```
cp -r [foldername] /media/ThomasNewDrive/backup
```

---

### Post by billgoldberg on 2008-02-02
Thats the hard way to do it guys.

Simply open up a terminal and enter

```
sudo nautilus
```

Then you can browse to the file and copy it everywhere you want.

The guy is new to ubuntu (linux) and you guys start with complicated commands, while this can be done easily using a gui.

---

### Post by lswest on 2008-02-02
well, from what i gathered, he didn't have a GUI, so i was doing it from the terminal, otherwise, yea, i'd just have made him open nautilus.  I went with jan quark's suggestion and just expanded on that.  However, i also find backing things up is always best if the folder is tarred, as it is just generally more efficient^^  But yea, if you have a gui, go with the above, open nautilus, and just browse to the folders you want, ctrl + c to copy, and then browse to the external drive, and ctrl + v to paste (just like in windows :P)

---

### Post by billgoldberg on 2008-02-02
The terminal works but newcomers might get the wrong idea that for something as simple as moving a folder, you need to be a computer guru in order to do it.

---

### Post by lswest on 2008-02-02
yeah, i know what you mean.  My bad, i thought he was gui-less, at least, i gathered jan quark knew something i didn't :P  Anyways, thanks for pointing that out.  and, i know it doesn't really matter, but most people prefer (or think it's better) to launch gui's with ```
gksudo [program name, in this case nautilus]
```

---

### Post by tomaso18 on 2008-02-02
Thank You Iswest and thank You BillGoldBerg for the time spent on my issue unfortunately both of you are right, I don't know where to start from with Linux systems, I am trying the Nautilus way but the copy and paste doesn't work. 
I got the 
Initializing gnome-mount extension
I got the root windows open from there I navigated in the file system to the media folder where my "disk" and "ThomasNewDrive" folders are but they have a lock on them.I have tried to copy and paste my documents folder but it didn't work.

Sorry but I am very new with this OS and i really need specific directions.


thank you very much for your time

thomas

---

### Post by lswest on 2008-02-02
first off, my name starts with an "L" :P but no worries, not the first one to make that mistake :P secondly, can you check what permissions you have? cd to the directory just before your documents (e.g. if it's /media/disk/username/documents, go to /media/disk/username) and run ```
ls -l
```, or you can go to the folder in the GUI, right-click choose properties and go to the permissions tab, and take a screenshot of that, or just take note of the permissions, and post those back.

---

### Post by tomaso18 on 2008-02-02
hi
sorry Lswest my mistake.

cd /media
ubuntu@ubuntu:/media$ ls -l
total 12
dr-xr-xr-x 1 root root 4096 2008-01-30 17:56 disk
drwxr-xr-x 2 root root   60 2008-02-01 20:27 lrwxrwrwxrwx
drwxr-xr-x 2 root root   60 2008-02-01 20:22 newfile
dr-xr-xr-x 1 root root 8192 2008-01-10 19:06 ThomasNewDrive
drwxr-xr-x 2 root root   60 2008-02-01 20:18 usb
 is this what you where asking for?

by the way I don't know what a GUI is.
thanks 
thomas

---

### Post by tomaso18 on 2008-02-02
I wanted just to add that after trying and trying again I got to this....
ubuntu@ubuntu:/media/disk$ ls -l
total 1180124
-r-xr-xr-x 1 root root      20934 2008-01-19 15:49 ASLog.txt
-r-xr-xr-x 1 root root          0 2008-01-09 16:51 AUTOEXEC.BAT
-r-xr-xr-x 1 root root       3010 2008-01-29 19:39 bootex.log
-r-xr-xr-x 1 root root       4952 2002-09-10 20:00 Bootfont.bin
-r-xr-xr-x 1 root root        210 2008-01-29 20:32 boot.ini
-r-xr-xr-x 1 root root          0 2008-01-09 16:51 CONFIG.SYS
dr-xr-xr-x 1 root root          0 2008-01-28 22:14 Deckard
dr-xr-xr-x 1 root root       4096 2008-01-09 16:57 Documents and Settings
-r-xr-xr-x 1 root root          0 2008-01-09 16:51 IO.SYS
-r-xr-xr-x 1 root root          0 2008-01-09 16:51 MSDOS.SYS
-r-xr-xr-x 1 root root      47580 2002-09-10 20:00 NTDETECT.COM
-r-xr-xr-x 1 root root     235184 2002-09-10 20:00 ntldr
-r-xr-xr-x 1 root root 1207959552 2008-01-30 17:58 pagefile.sys
-r-xr-xr-x 1 root root         72 2008-01-28 20:34 Pollog.txt
-r-xr-xr-x 1 root root      10875 2008-01-28 20:34 PollSt.txt
dr-xr-xr-x 1 root root      12288 2008-01-29 17:26 Programmi
dr-xr-xr-x 1 root root          0 2008-01-10 15:42 RECYCLER
dr-xr-xr-x 1 root root          0 2008-01-09 17:00 SYSTEM.SAV
dr-xr-xr-x 1 root root       4096 2008-01-09 22:53 System Volume Information
dr-xr-xr-x 1 root root     131072 2008-01-30 17:56 WINDOWS
-r-xr-xr-x 1 root root        146 2008-01-10 18:04 YServer.txt
ubuntu@ubuntu:/media/disk$ Documents and Settings
bash: Documents: command not found
ubuntu@ubuntu:/media/disk$ cd /media/disk/Document and Settings
bash: cd: /media/disk/Document: No such file or directory

As you can see here above I cannot go into the Documents and Settings folder.

thanks 
thomas

---

### Post by lswest on 2008-02-03
to change directory to documents and settings you have to either give in (after you've cd'd to /media/disk/ or otherwise add /media/disk/ in before documents and settings) ```
cd Documents\ and\ Settings
``` or ```
cd "Documents and Settings"
``` as the spaces are taken to be the end of the file name, and the backslashes tell it to include the spaces in the name, or putting it in quotes works too.  And yes, that was what i wanted to see, and it tells me that if you run GUI (graphical user interface, pretty much everything you see when you log into a desktop) as root, you should have permissions to access the folder, and copy anything and everything you need.  If you can cd to the right folder, try doing ```
sudo cp -r /[foldername] /media/ThomasNewDrive/backup
``` and see if it copies.  if it does, you're all set and (should be able to) copy and paste everything you need if you run ```
gksudo nautilus
``` in the terminal and browse normally.  If not, it might give you a useful error message.

---

### Post by tomaso18 on 2008-02-03
Hi,thank you once again,I have tried and this is the result.....

ubuntu@ubuntu:/media/disk/Documents and Settings$ ls -l
total 64
dr-xr-xr-x 1 root root  4096 2008-01-09 16:50 All Users
dr-xr-xr-x 1 root root 49152 2008-01-09 16:57 Default User
dr-xr-xr-x 1 root root  4096 2008-01-10 00:17 LocalService
dr-xr-xr-x 1 root root  4096 2008-01-09 16:55 NetworkService
dr-xr-xr-x 1 root root  4096 2008-01-19 16:26 Tomaso Pintus
ubuntu@ubuntu:/media/disk/Documents and Settings$ cd
ubuntu@ubuntu:~$ sudo cp -r /"Tomaso Pintus"/media/ThomasNewDrive/backup
cp: missing destination file operand after `/Tomaso Pintus/media/ThomasNewDrive/backup'
Try `cp --help' for more information.
What am I doing wrong??

thanks
thomas

---

### Post by tomaso18 on 2008-02-05
Hello,:confused:

Can anybody help me,
I am trying to save some files from my almost dead laptop to my external HD.
My friend did it once using UBUNTU but now I am left by myself and I have tried many options,
I have tried this to change the file system,but it didn't work

sudo chown ubuntu /media/ThomasNewDrive
chown: changing ownership of `/media/ThomasNewDrive': Read-only file system

:confused:
Any idea??

thank you.
thomas

---

