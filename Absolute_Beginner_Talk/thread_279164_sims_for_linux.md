---
title: "sims for linux"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by in2media on 2006-10-17
just got the sims for linux (includes winex), trying to install it on ubuntu 6.06
when i type in the command as the sims manual states,
rpm _i /mnt/cdrom/*.rpm
it says rpm command not found
 anyone any ideas](*,)

---

### Post by Perfect Storm on 2006-10-17
```
cd /media/cdrom
ls -a

```


What does it say?

---

### Post by Klaidas on 2006-10-17
It seems that you're trying to install RPM, while ubuntu uses DEB

---

### Post by in2media on 2006-10-17
so i take it its not gonna work then

---

### Post by Lord Illidan on 2006-10-17
Can you try this, please :

```
cd /media/cdrom
ls -a
```

and post output here?

---

### Post by in2media on 2006-10-17
john@john:~$ cd /media/cdrom
john@john:/media/cdrom$ ls -a
.   00000001.LT1  clcd32.dll    ltdll.dll  simsdata.rpm  sources
..  clcd16.dll    f0ad3041.bin  README     sims.rpm      winexsim.rpm
john@john:/media/cdrom$

---

### Post by rejser on 2006-10-17
sudo apt-get install rpm ?
or alias it to a deb

---

### Post by srt4play on 2006-10-17
I have the sims for linux also, and it works great. It won't work though with the version of winex that's on the cd. You need to go to:

[http://www.transgaming.com/showthread.php?news=82](http://www.transgaming.com/showthread.php?news=82)

and get the updates for the game.

It's been a while since I installed it for my g/f but they give you an updated winexsim.rpm and also an updated sims.rpm I think. That leaves the simsdata.rpm that you have to copy over to your home directory.

You convert those three rpm files into debs with alien, which you get by:

sudo apt-get install alien

Once alien is installed, do:

sudo alien 'file'   

for each rpm file.

Then install them with:

sudo dpkg -i *.deb

---

### Post by in2media on 2006-10-17
john@john:~$ sudo alien simdata.rpm
File "simdata.rpm" not found.
john@john:~$

---

### Post by Perfect Storm on 2006-10-17
copy the simdata.rpm to your Desktop then
```
sudo aptitude install alien
cd Desktop
sudo alien -i simdata.rpm
```

Use the same on the rest of the .rpm files on your CD.

---

### Post by in2media on 2006-10-17
john@john:~$ cd Desktop
john@john:~/Desktop$ sudo alien -i simsdata.rpm
File "simsdata.rpm" not found.

---

### Post by srt4play on 2006-10-17
Did you go get the updates from transgaming?

---

### Post by in2media on 2006-10-17
i was trying to open the simsdata but forgot to cd into the folder
anyway tried what you said and it ran for bout 5 minutes then get the following error
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/.the_sims/c_drive/Program': No such file or directory
chmod: cannot access `Files': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/.the_sims/c_drive/Program': No such file or directory
chmod: cannot access `Files/Common': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/UserData_Asia/Web': No such file or directory
chmod: cannot access `Templates': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/UserData_Europe/Web': No such file or directory
chmod: cannot access `Templates': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/UserData_NA/Web': No such file or directory
chmod: cannot access `Templates': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/Web': No such file or directory
chmod: cannot access `Templates': No such file or directory
john@john:~/Desktop$

---

### Post by justin whitaker on 2006-10-17
There are two ways to do it:

alien -i

Installs the file directly. Make sure you change permissions on the file first.

alien -d 

changes it to a .deb package first. 

Check this article:

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

I'd use alien -d, then dpkg -i the files.

---

### Post by in2media on 2006-10-17
:) just created the deb packages and downloaded the 2 updates from the link someone posted. do i install the 3 packages i created of the cd and the 2 updates or the 2 updates and the 1 package of the cd

---

### Post by in2media on 2006-10-17
trying to log in as su but it asking for password
problem is it never asked me for password during install just asked for user id and password

---

### Post by aktiwers on 2006-10-17
its the same password as you login with. The user password.

---

### Post by in2media on 2006-10-17
no mate its not letting me in 
john@john:~$ su
Password:
su: Authentication failure
Sorry.
john@john:~$

---

### Post by aktiwers on 2006-10-17
its

> sudo su   ;)

EDIT:
But you can use just sudo infront of what you need to do as root.
Like "sudo command" and you do it as root.

---

### Post by in2media on 2006-10-17
thanx il try that, all this to stop the girlfriend from installing the other operating system to play sims

---

### Post by srt4play on 2006-10-17
> **in2media said:**
> :) just created the deb packages and downloaded the 2 updates from the link someone posted. do i install the 3 packages i created of the cd and the 2 updates or the 2 updates and the 1 package of the cd

Install the 2 updates and the 1 package from the cd.

---

### Post by in2media on 2006-10-17
thanx to all that helped i really do appreciate the help, i got it running

one last question
is it possable to put a desktop icon for the sims rather then going through the terminal etc

---

### Post by CatKiller on 2006-10-17
> **in2media said:**
> is it possable to put a desktop icon for the sims rather then going through the terminal etc

You probably already have one, in ~/.gnome/apps/Wine. If you copy the Sims launcher to the desktop, you're all set.

---

### Post by in2media on 2006-10-18
i looked for the file but cant see it anywhere

---

### Post by CatKiller on 2006-10-18
Oh well. A lot of the games that I've installed under Wine have put launchers there.

Right-click on the desktop and select Create Launcher. In Name, put The Sims, in Command put > wine "C:\Program Files\Maxis\The Sims\Sims.exe", select an icon that you like if you want one and click on OK. I've put the path in from memory from when I used to play The Sims on Windows, so it's probably wrong. Case is important. I'm sure you know what the path is from launching it from the command line.

Actually, Maxis used to have a fan-site kit that you could download from their site. You could use that to get an icon for the launcher if you can't find one from the install.

Oh, another thing - if you did already have a launcher, it's Ctrl-H to show hidden files (like ~/.gnome), and it might be in a subfolder of Wine - mine has Programs/Microids/Syberia DVD under that one, for example.

---

### Post by in2media on 2006-10-18
tried many abbreviations of the path but get the same message. no such path
in the command line i just use 
the_sims](*,)

---

### Post by srt4play on 2006-10-18
Why not just right-click the desktop, choose create launcher, in the name field put "The Sims" and in the command field put the_sims ?

---

### Post by in2media on 2006-10-18
thanx mate problem solved

---

### Post by in2media on 2006-10-19
now i got it working on my pc my daughter wants it on hers, and theres a little problem
john@john:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package alien

---

### Post by Perfect Storm on 2006-10-20
check and see if your sourcelist is at it should be.
```
cat /etc/apt/sources.list
```

---

### Post by in2media on 2007-08-11
trying to install sims (you know women and the sims) but following these instructions from last time and getting the following errors
john@john-laptop:~/Desktop/sims$ sudo alien -d simsdata.rpm
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/UserData_NA/Web': No such file or directory
chmod: cannot access `Templates': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/UserData_Europe/Web': No such file or directory
chmod: cannot access `Templates': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/.the_sims/c_drive/Program': No such file or directory
chmod: cannot access `Files': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/.the_sims/c_drive/Program': No such file or directory
chmod: cannot access `Files/Common': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/Web': No such file or directory
chmod: cannot access `Templates': No such file or directory
chmod: cannot access `The_Sims_Data-1.1/./usr/lib/the_sims/UserData_Asia/Web': No such file or directory
chmod: cannot access `Templates': No such file or directory

---

