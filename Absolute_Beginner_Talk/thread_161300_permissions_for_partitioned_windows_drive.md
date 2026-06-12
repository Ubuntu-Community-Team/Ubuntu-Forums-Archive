---
title: "permissions for partitioned windows drive?"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-16
I partitioned and set up a dual boot yesterday, all went good i think.  I have /windows mounted as well as /datashare (fat32 for both os's) if im in windows and save a file in my fat32 partition i can get it through linux, cool.  but if i go to home>filesystem, my /windows has a red x and it says i dont have permissions to view it, (so does my 'lost and found folder')  how do i get permissions?

Edit:

[IMG]http://members.arstechnica.com/x/ryanx5452/System.png[/IMG]

screenshot of my sysmonitor, looks mounted to me

---

### Post by xyz on 2006-04-16
Try this. Hope it helps. Good day.
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
[http://www.linuxquestions.org/questions/showthread.php?t=245670](http://www.linuxquestions.org/questions/showthread.php?t=245670)

---

### Post by Princey on 2006-04-16
You can follow the advise I gave in these two threads. One is for NTFS  [http://www.ubuntuforums.org/showthread.php?t=148056]("http://www.ubuntuforums.org/showthread.php?t=148056") and the other for FAT32 drives [http://www.ubuntuforums.org/showthread.php?t=154681]("http://www.ubuntuforums.org/showthread.php?t=154681").

---

### Post by x5452 on 2006-04-16
sorry, I am not following. I have windows mounted, it recognizes it, and in system>admin>disks says its there, and says accessible, yet in my folder it says i dont have permissions.  
[http://www.ubuntuforums.org/attachment.php?attachmentid=8405&stc=1&d=1145244143](http://www.ubuntuforums.org/attachment.php?attachmentid=8405&stc=1&d=1145244143)
do i understand wrong what mounting is?

edit: sorry for the thumb and link, i didnt know how to do it

---

### Post by Sutekh on 2006-04-16
Yes you have those partitions mounted, but they may not have the correct settings to allow you access.

Can you post the contents of your mounting configuration file /etc/fstab?
```
cat /etc/fstab
```will display the contents of the file, just copy and paste them into a post.

---

### Post by x5452 on 2006-04-16
ryan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /datashare      vfat    defaults        0       0
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda2       /windows        ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
ryan@ubuntu:~$

whats all that say? lol  i thought i set it all up the same, my partition called 'datashare' i just named cause thats the fat 32 i want both to have access to, and it works, i put a pic in there while in windows, logged into ubuntu, opened it up and got the pic. just to test, why would that one work but windows not?

---

### Post by Sutekh on 2006-04-16
[QUOTE=x5452]
/dev/hda7       /datashare      vfat    defaults        0       0
/dev/hda2       /windows        ntfs    defaults        0       0[/QUOTE]
It just tells Ubuntu where to mount each partition,  so currently the partition /dev/hda2 (the NTFS one) is told to mount to the folder /windows.  

There's no problem with that.  The problem are the current options; **defaults**.

You need to change the lines in the fstab

Backup and edit the file with these commands```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```
and change those lines with```

/dev/hda7       /datashare      vfat    iocharset=utf8,umask=0000        0       0
/dev/hda2       /windows        ntfs    nls=utf8,umask=0222        0       0
```Save the file (Ctrl+O) and exit (Ctrl+X) then unmount and remount the partitions with the new options```
sudo umount /datashare
sudo umount /windows
sudo mount -a
```

You won't be able to write to the NTFS partition, as it is unsupported.  You will however have read and execution access.

---

### Post by x5452 on 2006-04-17
thanks for all that, before i go do it how do i remount them? your last code command says unmount, but once that is done, how do i get them back mounted, properly, so theyll come back automatically everytime i boot up?

---

### Post by Sutekh on 2006-04-17
Sorry that was stupid, should be
```
sudo mount -a
```

---

### Post by x5452 on 2006-04-17
haha, no it was I who was stupid,  you typed it correctly i just saw two unmount words and read to fast, didnt realize the last one said mount -a.  my bad, sorry, thanks again!:mrgreen:

---

### Post by Sutekh on 2006-04-17
Glad to help, but it *was* I who was stupid.  :) 

I edited the post already in case anyone looked over this. 

Check out the bottom of my post to see that I edited it.

I actually did what you said, I was typing umount so fast I forgot to leave the 'u' off the last one.

But if its working now, then its all good :D

---

### Post by x5452 on 2006-04-17
uh, im not sure what i did, first i thought i could copy and past in there, but it didnt, and pasted somewhere esle, i didnt save, just x'd out and retried... then did all your commands and when i sudo mount -a it said:

ryan@ubuntu:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda7,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

so i did that first thing you said again to see what it says:

ryan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /datashare      vfat    iocharset=utf8,unmask=000        0       0
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda2       /windows        ntfs    nls=utf8,unmask=222        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
ryan@ubuntu:~$

and now the red x is gone from the windows folder, but it is empty, and so is the datashare folder, which i know i put a picture in, (when i was checking it out)  any ideas?

---

### Post by Sutekh on 2006-04-17
[QUOTE=x5452]
/dev/hda7       /datashare      vfat    iocharset=utf8,**unmask**=000        0       0
/dev/hda2       /windows        ntfs    nls=utf8,**unmask**=222        0       0[/QUOTE]
These should have **umask** not **unmask**

---

### Post by x5452 on 2006-04-17
ok i went and changed those to what they should have been, could doing that have messed it up?  after i fixed it, then mount -a, the stuff came back in folder, but windows has that red x through it saying i dont have permission to view.

ryan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /datashare      vfat    iocharset=utf8,umask=000        0 0
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda2       /windows        ntfs    nls=utf8,umask=222        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
ryan@ubuntu:~$

thats what it is now

---

### Post by Sutekh on 2006-04-17
[QUOTE=x5452]
/dev/hda2       /windows        ntfs    nls=utf8,umask=222        0       0[/QUOTE]
Change this to
```
/dev/hda2   /windows   ntfs   nls=utf8,umask=**0**222   0   0
```

---

### Post by x5452 on 2006-04-17
that worked! thanks a lot, any chance you could tell me, or direct me to where i can read about, what that did? and why it made me able to read my windows files?  on a kind of side note, in my home folder is a folder called 'lost and found' withthe same red x in it, i dont even know what that file is, but can i 'unlock' its permissions too? 

thanks for all of your help, I really appreciate it! :KS

---

### Post by Sutekh on 2006-04-17
Ok the **/etc/fstab** is a file that contains the information that the program **mount** uses when it is called.  The file tells **mount **what partition is to be mounted, where it is mounted to and any other options as well.

So if you now used```
sudo mount [COLOR="Blue"]/dev/hda2[/COLOR]
```OR```
sudo mount [COLOR="Red"]/media/windows[/COLOR]
```**mount** looks to the /etc/fstab and finds
```
[COLOR="Blue"]/dev/hda2[/COLOR]    [COLOR="Red"]/media/windows[/COLOR]   [COLOR="Green"]ntfs[/COLOR]   [COLOR="DarkOrchid"]nls=utf8,umask=0222[/COLOR]   0   0
```
where it sees that it should mount the partition [COLOR="Blue"]/dev/hda2[/COLOR] to the folder [COLOR="Red"]/windows[/COLOR].  

It also tells **mount** that the filesystem is [COLOR="Green"]ntfs[/COLOR] and needs to be mounted with the options [COLOR="DarkOrchid"]nls=utf8,umask=0222[/COLOR].  The [COLOR="DarkOrchid"]nls=utf8[/color] option sets the character encoding to UTF8, which allows special characters to be viewed.  The [COLOR="DarkOrchid"]umask=0222[/COLOR] allows read and execute access to the partition only.

Here's a table for describing the way the permissions are controlled using umask (from the Gentoo Wiki)
[quote=Gentoo-Wiki]
umask: octal file permissions

You can change permissions using the parameter umask. But be aware that it must be the bitmask of permissions that are **not present** for the mountpoint. It is an octal number, formed like this:

* character '0': Indicates that this is an octal number, not decimal.
* first digit: owner user permissions
* second digit: owner group permissions
* third digit: world permissions (every other user on the system)

The modes are as follows (the first column is the mode octal number):

M | R W X
-------------
0 | * * *
1 | * * -
2 | * - *
3 | * - -
4 | - * *
5 | - * -
6 | - - *
7 | - - -

For example, if you want that everybody be able to read, write, and execute every file in your /mnt/c, you should specify the mask 0000:[/quote]
So by using a umask=0222, you are specifying that the mount point shall have read and execute permissions.

If say, for arguments sake, you had a umask=0356.  You would be allowing read only access to the mount owner, write only access to the mount group owner, and execute access to everyone else.

Currently the mount point would be owned by the user **root**, and the group owner would be **root** as well.  You can change these options to give you more refined control over the partition if you like.


Here are some more links on mounting and the fstab

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")
[http://www.tuxfiles.org/linuxhelp/mounting.html]("http://www.tuxfiles.org/linuxhelp/mounting.html")
[http://www.die.net/doc/linux/man/man5/fstab.5.html]("http://www.die.net/doc/linux/man/man5/fstab.5.html")
[http://www.die.net/doc/linux/man/man8/mount.8.html]("http://www.die.net/doc/linux/man/man8/mount.8.html")

---

### Post by x5452 on 2006-04-17
ha, excellent, thank you very much.  I hate not learning as I am doing so you just made it much better.  :mrgreen:  So now I can look at all my windows files while in linux, but I cant "use" any of the programs that way, correct? Like I have visual c++ on my windows, but I cannot execute that program, am I understanding right?  Thank you again so much for all of your help, you have been awsome!

---

### Post by Sutekh on 2006-04-17
[quote=x5452]I hate not learning as I am doing so you just made it much better[/quote]
That's good, I don't really like saying do this, do that, without explaining what its going to do.  Glad its working now.


Well you could possibly use the programs on your Windows partitions, using [Wine](www.winehq.com/)

You'd be most interested in their [Application Database](http://appdb.winehq.org/) for [Visual C++](http://appdb.winehq.org/appview.php?appId=53)

You may have some success in using Wine to run Visual C++.  
I can show you how to install Wine and how to use it.

First though, is there any reason why you need Visual C++, as there are a number of native Linux equivalents.

Try checking out this table.  [The table of equivalents / replacements / analogs of Windows software in Linux.](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) 
You want to look for Section 7 - Programming and Development.

---

### Post by x5452 on 2006-04-17
no particular reason for visual c++ only that I mentioned it because it was the first link on my windows desktop that i could think of.  I am still just starting to learn c++, ( my college classes for it start this summer, and I want to know something going in) so I will Probably find a linux program that is similar that I can use.

---

### Post by Sutekh on 2006-04-17
Ok cool, if you are still interested in running your Windows applications through wine, here's how you can do it.

All you need to do is add the WineHQ repository to your current sources, then you can install it using apt-get

Open a terminal window and issue the commands
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
sudo nano /etc/apt/sources.list
```This will backup your apt-get repository sources list, so you can always change it back, and then allow you to edit the list.

To install wine you will need the wine repository; add these lines to your sources.list
```

deb http://wine.sourceforge.net/apt/ binary/ 
deb-src http://wine.sourceforge.net/apt/ source/
```Then save the file (Ctrl+O) and exit (Ctrl+X).

Update the repositories and install wine using
```
sudo apt-get update
sudo apt-get install wine
```

Once wine is installed you should run **winecfg** to setup options such as sound, extra drives, etc.
```
winecfg
```

To install a game/program use wine in the following manner
```
wine /path/of/program.exe
```

For example running the setup.exe program on a CD-ROM
```
wine /media/cdrom0/setup.exe
```

To run a particular program, say from your other partition, use
```
wine /windows/Program\ Files/DVD\ Shrink/DVD\ Shrink\ 3.2.exe
```
Noting that to call a folder that contains spaces, you need to 'escape' them with a backslash (\).  Otherwise the command line will try to run```
wine /windows/Program
```and ignore the rest.  You can also use the <TAB> button to help you, it can auto-complete entries.  Just start typing a few letters and press <TAB>, if there is a unique filename/folder then it will autocomplete it for you or list the possible combinations.

Alternatively you can use quotation marks```
wine "/windows/Program Files/DVD Shrink/DVD Shrink 3.2.exe"
```

Don't forget to check the [Wine Application Database](http://appdb.winehq.org/) to see how the program runs with wine and find out about any issues that you may encounter.

---

### Post by pellgarlic on 2006-05-06
this thread helped me fix the same problem - i had installed breezy (5.10) and it found and mounted all my ntfs partitions (there were 3 of them) which i could copy files from no problem. then i made changes to the partitions, and lost them in ubuntu, so had to edit my fstab to get them back, only i couldn't copy stuff from them any more. any way, thanks to this thread, and other similar ones, i was able to get the permissions back :) 

i also found this page, which has a really good explanation of the fstab file, which might be interesting to some:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

