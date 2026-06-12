---
title: "Load &amp; run data from mapped drive"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by tim15856 on 2007-08-26
Just a minor problem that I wish to fix. All my data is on a Win2k file server (when I built this file server Ubuntu had known problems with RAID. I couldn't get RAID to work). On my Windows systems the "My Documents" folders are all mapped to a share on the file server. I have no problems clicking on a file and have it load and run in an application. On my Ubuntu system, I am mapped to the share and can access it with no problem, but I'd like to be able to click on a file and have it load and run in the proper application. Currently I must copy the file to my home folder in order to get it to do that. For most data files that's not much of a problem but it's a PITA when I want to play my music files. I don't have SAMBA installed since I'm not sharing anything on my Ubuntu box.

---

### Post by nexu56 on 2007-08-29
How did you "map the share"? If you used "Connect to server..." you should be able to do this (click on the file and have it run).

---

### Post by tim15856 on 2007-08-29
I'm pretty sure I did it that way or used the search network. Either way, I used the GUI to map it.

---

### Post by jimrz on 2007-08-29
> **tim15856 said:**
> I'm pretty sure I did it that way or used the search network. Either way, I used the GUI to map it.

seems that in order to properly runs some files (at least video files, in my case) you need to first create a mount point  in ubuntu 
```
mkdir samba_share
```

do that somewhere in your /home directory (you can name the directory whatever you want),then mount the folder you want to run the file from to the mount point you created
```
sudo smbmount //<target server name>/<target file name /home/<user name>/samba_share -o username=j<user name>,password=<yourPW>,charset=utf8,file_mode=0777,dir_mode=0777
```
the file_mode and dir_mode assume that your target drive is formatted ntfs

---

