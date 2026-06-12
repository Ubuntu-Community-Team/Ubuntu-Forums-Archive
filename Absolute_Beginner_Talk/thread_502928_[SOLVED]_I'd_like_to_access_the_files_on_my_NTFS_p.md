---
title: "[SOLVED] I'd like to access the files on my NTFS partition..."
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Auax on 2007-07-17
Is there a program that will let Linux read/write NTFS?

---

### Post by overdrank on 2007-07-17
> **Auax said:**
> Is there a program that will let Linux read/write NTFS?

Hi if you go to synaptic manager and search for ntfs you will find options ntfs-3g, and ntfs-config and those should work for you. You can also install via the terminal
```
sudo apt-get install ntfs-3g
```
Good luck!:popcorn:

---

### Post by useResa on 2007-07-17
I think that the information you require can be found in the Wiki:
[Mounting Windows Partitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

Hope this information helps.

---

### Post by Auax on 2007-07-17
> **overdrank said:**
> Hi if you go to synaptic manager and search for ntfs you will find options ntfs-3g, and ntfs-config and those should work for you. You can also install via the terminal
```
sudo apt-get install ntfs-3g
```
Good luck!:popcorn:

I got this:
```
admin@Hades:~$ sudo apt-get install ntfs-3g
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

```

---

### Post by overdrank on 2007-07-17
> **Auax said:**
> I got this:
```
admin@Hades:~$ sudo apt-get install ntfs-3g
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

```

I apologize I just noticed you are using dapper. You will need to add the repos's to you app list. You can go to system, administration, software sources and add all the repos to the list. Universe and multi universe I believe.
This link will help.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Edit added link.

---

### Post by Auax on 2007-07-17
> **overdrank said:**
> I apologize I just noticed you are using dapper. You will need to add the repos's to you app list. You can go to system, administration, software sources and add all the repos to the list. Universe and multi universe I believe.

Do I have to reboot afterwards? Because I still get the same message.

---

### Post by useResa on 2007-07-17
After you have altered your sources.list you need to provide the following command in a terminal so the information is updated```
sudo apt-get update
```

---

### Post by Auax on 2007-07-17
Arg, I added a new repository to download something else, and now I get an error for that when I try to update. T_T

---

### Post by useResa on 2007-07-17
Could you post the result of the *sudo apt-get update* command?

---

### Post by Auax on 2007-07-17
> **useResa said:**
> Could you post the result of the *sudo apt-get update* command?

```
admin@Hades:~$ sudo apt-get update
E: Type 'ftp://ftp.videolan.org/pub/videolan/ubuntu' is not known on line 33 in source list /etc/apt/sources.list
```

Edit: I think I was supposed to use this: deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) dapper universe

---

### Post by useResa on 2007-07-17
Sorry forgot to indicate this before, but could you also post the content of your sources.list? You can use the following command to get the content displayed```
cat /etc/apt/sources.list
```

---

### Post by Auax on 2007-07-17
```
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
ftp://ftp.videolan.org/pub/videolan/ubuntu
ftp://ftp.videolan.org/pub/videolan/ubuntu
ftp://ftp.videolan.org/pub/videolan/ubuntu

```

I'm fairly certain I just entered the wrong line now... I just don't know how to remove a repository.

---

### Post by useResa on 2007-07-17
You can edit your file by giving the following command
```
gksudo gedit /etc/apt/sources.list
```
When the file has opened remove the last two lines (those are duplicates).
Alter the line
> [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu)
so that it reads
> deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) dapper universe
Save the file and try the command again
```
sudo apt-get update
```

---

### Post by Auax on 2007-07-17
Ok, that's done... but now I still get ```
admin@Hades:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

```

---

### Post by overdrank on 2007-07-17
> **Auax said:**
> Ok, that's done... but now I still get ```
admin@Hades:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

```

Hi take a look at this page 
[http://doc.gwos.org/index.php/NTFS-3g#DAPPER](http://doc.gwos.org/index.php/NTFS-3g#DAPPER)

---

### Post by useResa on 2007-07-17
Sorry ... just read the [following article]("http://doc.gwos.org/index.php/NTFS-3g")
It indicates that the package is NOT in the DAPPER repositories.
However, it indicates the lines that you have to add to your sources.list to get the package anyway.

Hope this will -- finally? -- solve your issue.
Good luck

---

### Post by Auax on 2007-07-17
Thank you, very much.

---

