---
title: "[SOLVED] What is wrong with this command ??? Please !"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2008-01-29
```
peter@Gutsy:~$ sudo su
[sudo] password for peter:
root@Gutsy:/home/peter# cd /
root@Gutsy:/# tar xvpzf backup.tgz -C /
tar: backup.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@Gutsy:/# 

```It is the command to restore the tar backup I found i[n this HowTo ]("http://ubuntuforums.org/showthread.php?t=35087&highlight=tar+backup")
I have the backup.tgz package in my / and I have tried it from the command line in the installation and using the live CD. I had the problem up once before [here ]("http://ubuntuforums.org/showthread.php?t=674103")
but even with all that help I could not make it work and had to do a new install. Now at tax time it becomes important again. I need more help.

---

### Post by PinkFloyd102489 on 2008-01-29
Move the tgz to /, cd to there, then do tar xvpzf backup.tgz

---

### Post by kindafunnylookin on 2008-01-29
The tgz is in root - have attached screenshot.tried doing what you said as you see here:```
peter@Gutsy:~$ sudo su
root@Gutsy:/home/peter# cd /restore.tgz
bash: cd: /restore.tgz: No such file or directory
root@Gutsy:/home/peter# 

```
The package is not seen.

---

### Post by Whiffle on 2008-01-29
Where are you wanting to extract it to?  cd to that folder, and then do

tar xvpzf /path/to/tgz

and it will extract to the folder you're in.

---

### Post by kindafunnylookin on 2008-01-29
> **Whiffle said:**
> Where are you wanting to extract it to?  cd to that folder, and then do

tar xvpzf /path/to/tgz

and it will extract to the folder you're in.

It's a compressed tar backup of my entire HD.

---

### Post by vikram on 2008-01-29
can you check the location of the file ?

based on the thumbnail it looks like the file is in /root the home dir of root

```

ls /
ls /root

```

should tell you where it is. go to the correct dir and untar the file from there.

---

### Post by bodhi.zazen on 2008-01-29
> **kindafunnylookin said:**
> It's a compressed tar backup of my entire HD.

If that is the case, you should do this procedure from a live CD and not try to overwrite your / while it is mounted.

---

### Post by kindafunnylookin on 2008-01-29
> **vikram said:**
> can you check the location of the file ?

based on the thumbnail it looks like the file is in /root the home dir of root

```

ls /
ls /root

```should tell you where it is. go to the correct dir and untar the file from there.
Now we have something going.
```
peter@Gutsy:~$ ls /
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
peter@Gutsy:~$ ls /root
backup.tgz  Desktop  nautilus-debug-log.txt
peter@Gutsy:~$ 
```

What do I do now ?? Have to leave now for 1 hour.

---

### Post by kindafunnylookin on 2008-01-29
> **bodhi.zazen said:**
> If that is the case, you should do this procedure from a live CD and not try to overwrite your / while it is mounted.
OK I can do that when I get back, thank you.

---

### Post by Whiffle on 2008-01-29
cd /

tar xvpz /root/backup.tgz

---

### Post by bodhi.zazen on 2008-01-29
Well, here is a detailed how-to using tar :

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

As I said, I would do it a little differently, but give it a read.

You might also want to look at an alternate method such as partimage

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by vikram on 2008-01-29
> **kindafunnylookin said:**
> Now we have something going.
```
peter@Gutsy:~$ ls /
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
peter@Gutsy:~$ ls /root
backup.tgz  Desktop  nautilus-debug-log.txt
peter@Gutsy:~$ 
```What do I do now ?? Have to leave now for 1 hour.



so it is /root and not THE root directory /
cd to /root and run your command from there.

before you do make sure you know what you are going. as warned in the tutorial you will be overwriting many files.

again because you are extracting a tar - you will still keep any new files created after you backed up so it is not an identical restrore. also be careful that any overwritted config files + new files not overwritten by the tar may have unknown effects. i am not a *nix expert or a tar expert but this looks like one of those things  where you want to back up critical data.

---

### Post by jfinkels on 2008-01-29
The 'root' of the filesystem is at "/".

The home folder for the 'root' user is at "/root/".

It is a subtle difference of which you should now be aware.

---

### Post by kindafunnylookin on 2008-01-29
> **Whiffle said:**
> cd /

tar xvpz /root/backup.tgz
OK. I did that from the live cd and the cursor is working, so far the command was not rejected. I' going to wait but I'm not seeing or hearing anything. It's a 4GB compressed file so I expect it to take a while

---

### Post by kindafunnylookin on 2008-01-29
[quote=Whiffle;4232233]cd /
This is what I got:
 
```
peter@Gutsy:~$ sudo su
[sudo] password for peter:
root@Gutsy:/home/peter# cd /
root@Gutsy:/# 
root@Gutsy:/# cd /
root@Gutsy:/# 
root@Gutsy:/# tar xvpz /root/backup.tgz

root@Gutsy:/# 

```At this point I am going to throw in the towel while I still have my new install in one piece. Thanks for trying with me.

---

### Post by drowner on 2008-01-29
Whats wrong? If it says nothing it means it worked!

It would spit errors at you otherwise!

---

### Post by kindafunnylookin on 2008-01-29
This is what did the trick.
Working from command line in /root instead of / and change the command  to ```
tar xvpzf backup.tgz -C /root
```As it turned out it restored for about 6 minutes and quit unexpectedly because the package was broken. Partimage is lookin good !

---

### Post by asmoore82 on 2008-01-29
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

