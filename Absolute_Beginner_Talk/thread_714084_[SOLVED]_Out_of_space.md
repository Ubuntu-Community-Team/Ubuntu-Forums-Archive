---
title: "[SOLVED] Out of space?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2008-03-03
Apparently, I am out of space. Although I don't know how to check it or what to do about it. I can't even believe it. I installed using WUBI and I have a 10g WUBI folder. I don't get it. I would appreciate some guidance.
Thanks

---

### Post by jeffus_il on 2008-03-03
run ```
df -h
``` in a terminal and post the output.

---

### Post by stevelasvegas on 2008-03-03
steven@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/media/host/wubi/disks/system.virtual.disk
                      5.8G  5.6G     0 100% /
varrun                756M  228K  755M   1% /var/run
varlock               756M     0  756M   0% /var/lock
udev                  756M   68K  756M   1% /dev
devshm                756M     0  756M   0% /dev/shm
lrm                   756M   34M  722M   5% /lib/modules/2.6.22-14-generic/volatile
/media/host/wubi/disks/home.virtual.disk
                      2.0G  663M  1.2G  36% /home
overflow              1.0M  200K  824K  20% /tmp

---

### Post by Cypher on 2008-03-03
> **stevelasvegas said:**
> steven@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[B]/media/host/wubi/disks/system.virtual.disk
                      5.8G  5.6G     0 100% /[/B]
varrun                756M  228K  755M   1% /var/run
varlock               756M     0  756M   0% /var/lock
udev                  756M   68K  756M   1% /dev
devshm                756M     0  756M   0% /dev/shm
lrm                   756M   34M  722M   5% /lib/modules/2.6.22-14-generic/volatile
/media/host/wubi/disks/home.virtual.disk
                      2.0G  663M  1.2G  36% /home
overflow              1.0M  200K  824K  20% /tmp

You are indeed out of space. You can try the following to perhaps see where you're space is going
```

cd /
sudo du -sch

```
This will give you the directory totals..

---

### Post by aysiu on 2008-03-03
> **stevelasvegas said:**
> steven@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/media/host/wubi/disks/system.virtual.disk
                      5.8G  5.6G     0 100% / Yes, you're out of space. The size is 5.8 GB. You're using 5.6 GB. You have 0 GB available, and you've used 100% of the / partition.

You can probably clean out a little space with this command: ```
sudo apt-get clean
``` This deletes all the .deb installer files from /var/cache/apt/archives

---

### Post by stevelasvegas on 2008-03-03
This is all it says:
steven@ubuntu:/$ sudo du -sch
[sudo] password for steven:
78G     .
78G     total

---

### Post by stevelasvegas on 2008-03-03
[IMG]http://farm4.static.flickr.com/3209/2308337734_e6e5a97d78_o.png[/IMG]


I don't understand what is using 5.5 GB. I haven't knowingly used that much space.

---

### Post by jeffus_il on 2008-03-03
Try aysiu's advice running:  
```
sudo apt-get clean
```

---

### Post by Cypher on 2008-03-03
Did you try the command that **aysiu** suggested to see if that'll clear it up?

---

### Post by stevelasvegas on 2008-03-03
Did that - the last screenshot is a reflection of after that command

---

### Post by jeffus_il on 2008-03-03
```
du -h / | less
``` will give you the sizes of all your folders, but will give you lots of output ...

---

### Post by stevelasvegas on 2008-03-03
Isn't there something like the file browser that will allow me to sort the listings by size (both folders and files)? File browser sort of does it but it looks at folder size as number of elements as opposed to size of folder contents.

---

### Post by stevelasvegas on 2008-03-03
Yes there is. Now what?
[IMG]http://farm3.static.flickr.com/2350/2307754135_2dbd06d0fa_o.png[/IMG]

---

### Post by Cypher on 2008-03-03
So the space being taken up in /lib and /share is fine..it's the /var/backup that you need to worry about. Did you run the command
```

sudo apt-get clean

```
?? If not, you should do so and also look into the /var/backup directory and see what you can remove..

---

### Post by stevelasvegas on 2008-03-04
Yes I ran the above code and it had little effect. Apparently, I had previously installed SBackup and configured it to do an automatic daily backup that ran in the background. Why there is no indication that it is running is beyond me. I reset the configuration in SBackup to manual and deleted the folders that contained the backups and regained a ton of space. That was crazy!
Thanks all for the help.

[IMG]http://farm4.static.flickr.com/3248/2309012215_be5e98b937_o.png[/IMG]

---

### Post by jeffus_il on 2008-03-04
For the record:

If you do not want to install a kde application and bring with it the Kde libraries here is an updated version of the du command from a terminal which will give you the thirty largest directories sorted by size:
```
sudo du / | sort -n | tail -n 30
```

---

