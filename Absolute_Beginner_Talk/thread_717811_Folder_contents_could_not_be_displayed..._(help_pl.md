---
title: "Folder contents could not be displayed... (help please!)"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by red11rover on 2008-03-07
Hey everyone, 

I apologize if this question has been answered elsewhere... but I have tried a number of the suggestions from the other threads and they don't seem to work or apply to this specific problem. If they do please re-direct me there.

I very recently installed Gutsy and it is the only OS I have on my computer. I also bought a new FreeAgent Seagate 350GB external hd which worked fine for a while. When I can't access the drive I just have to unmount and remount it. However, a new problem has developed recently:

It gives me "The folder contents could not be displayed. Sorry, couldn't display all the contents of "MF"." when I try to access the movie folder on my hd. I can open other folders on there (which do not contain media files) just fine.

I have tried remounting the hd, rebooting, killall nautilus, turning off the sound preview, and ctrl+alt+backspace ...I'm not sure what else to do.

Please help!

Thanks a lot.

---

### Post by herbster on 2008-03-07
Paste output of

```
df -h
```

and

```
ls -la /media
```

with the drive plugged in.

---

### Post by red11rover on 2008-03-07
I did and recieved:

```
pavanidg@arnold:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G   32G   37G  47% /
varrun                248M  108K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M  100K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             299G   48G  252G  16% /media/FreeAgent Drive
pavanidg@arnold:~$ ls -la /media
total 24
drwxr-xr-x  4 root root 4096 2008-03-07 10:03 .
drwxr-xr-x 21 root root 4096 2008-02-05 10:11 ..
lrwxrwxrwx  1 root root    6 2008-02-05 09:48 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-02-05 09:48 cdrom0
drwxrwxrwx  1 root root 8192 2008-03-07 08:30 FreeAgent Drive
-rw-r--r--  1 root root   85 2008-03-07 10:03 .hal-mtab
-rw-------  1 root root    0 2008-03-07 10:03 .hal-mtab-lock
pavanidg@arnold:~$ 
```

---

### Post by herbster on 2008-03-07
Hmm, you have 777 on the drive. Is your movies folder you're trying to get into a subdirectory of the FreeAgent Drive? For example if you browse FreeAgent Drive, would you normally see your movies folder right there?

Try:

```
cd /media/FreeAgent\ Drive/yourmoviesfolder
ls
```

Paste output, and of course replace "yourmoviesfolder" with the name of your movie folder

Also paste output of:

```
ls -la /media/FreeAgent\ Drive/
```
Paste output.

---

### Post by red11rover on 2008-03-08
This is what I got... I hope I did it right! Yes, my movies are in a folder inside the external hd. 

```
pavanidg@arnold:~$ cd /media/FreeAgent\ Drive/MF
pavanidg@arnold:/media/FreeAgent Drive/MF$ ls
ls: reading directory .: Input/output error
pavanidg@arnold:/media/FreeAgent Drive/MF$ ls -la /media/FreeAgent\ Drive/
total 142685
drwxrwxrwx 1 root root      8192 2008-03-07 08:30 .
drwxr-xr-x 4 root root      4096 2008-03-07 15:57 ..
drwxrwxrwx 1 root root      8192 2007-05-07 07:46 EULA
-rwxrwxrwx 2 root root     22486 2006-10-30 18:39 FreeAgentPro.ico
-rwxrwxrwx 2 root root 146041088 2007-02-08 17:29 Install FreeAgent Tools.exe
lrwxrwxrwx 1 root root        84 2008-03-05 21:34 Link to Pavani's Movies -> /media/FreeAgent Drive/Pavani's Movies
drwxrwxrwx 1 root root     12288 2008-03-04 09:45 MF
drwxrwxrwx 1 root root      4096 2008-02-04 20:47 System Volume Information
drwxrwxrwx 1 root root         0 2008-03-07 08:15 .Trash-pavanidg
drwxrwxrwx 1 root root      4096 2007-05-07 07:47 User Manuals
drwxrwxrwx 1 root root         0 2007-05-07 07:47 Warranty
pavanidg@arnold:/media/FreeAgent Drive/MF$ 

```

---

### Post by herbster on 2008-03-09
You may find the solution here: [http://ubuntuforums.org/showthread.php?t=494673](http://ubuntuforums.org/showthread.php?t=494673)

---

### Post by red11rover on 2008-03-10
Thank you for trying to help but I think I'm just going to go back to Windows. Ubuntu is obviously not for someone like me haha.

---

