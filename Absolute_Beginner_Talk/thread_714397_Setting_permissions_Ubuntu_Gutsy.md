---
title: "Setting permissions Ubuntu Gutsy"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by shanehaua on 2008-03-03
Hi,
I have formated my external Seagate 500 gig ext2. I cannot save, open or delete anything on the drive. I don't have permission. Yet I am the owner of the Laptop!!!!! 
How do I fix that?

---

### Post by glennric on 2008-03-03
After mounting the drive you can do
```
sudo chown username:username /path/to/mountpoint
```
where username is your username and /path/to/mountpoint is the full path to where the drive is mounted.

---

### Post by shanehaua on 2008-03-03
I'm not doing something correctly. Its now set to root, but won't let me copy or paste etc.

---

### Post by glennric on 2008-03-03
If it is set to root you won't have permission to access it.  You need to change it to your username like I said above.

---

### Post by shanehaua on 2008-03-03
Yes, tried that but it set to root. I think I got the path wrong. Not sure.

---

### Post by shanehaua on 2008-03-03
Do I need to restart the computer?

---

### Post by glennric on 2008-03-03
Post the output of the command "mount"

---

### Post by shanehaua on 2008-03-03
Oh dear, I'm new. Don't know how to command it to mount.

---

### Post by glennric on 2008-03-03
Do you know how to open a terminal?

---

### Post by shanehaua on 2008-03-03
'mount'
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/disk type ext2 (rw,nosuid,nodev)

I hope this is what you mean.

---

### Post by glennric on 2008-03-03
It appears as if the external harddrive is /dev/sdc1 and is mounted on /media/disk.  So type in a terminal
```
sudo chown -R username:username /media/disk
```
I added the option -R for good measure.  Your username is what appears before the @ on every line of the terminal in case you didn't know that.

---

### Post by shanehaua on 2008-03-03
This is what happened

shane@shane-laptop:~$ sudo chown -R shane:shane /media/disk
shane@shane-laptop:~$ 

It is still set to root.

---

### Post by glennric on 2008-03-03
What is set to root?  Please be more specific.

---

### Post by shanehaua on 2008-03-03
sorry, my external hd.

---

### Post by glennric on 2008-03-03
How are you determining that your external hard drive is set to root?

---

### Post by shanehaua on 2008-03-03
Looking at permissions tab in properties.

---

### Post by ferdostar on 2008-03-03
Sorry, but it wouldn't be easier to do this using nautilus?

---

### Post by glennric on 2008-03-03
If you did run the "sudo chmod ..." command from a terminal as I told you to before then you should now be able to open nautilus and browse to /media/disk and work with your files.  What permissions tab are you looking at?  The permissions for what file or directory?

---

### Post by shanehaua on 2008-03-03
The hd is empty just trying to put a folder in it.

---

### Post by shanehaua on 2008-03-03
looking at the permissions tab in the disk properties.

---

### Post by glennric on 2008-03-03
Ok, open nautilus.  Browse to /media/disk (Type Ctrl-L and type /media/disk in the address bar)  then right click and select create folder.  You should be able to do this if you ran the command above.

---

### Post by shanehaua on 2008-03-03
I restarted the computer and the permissions have changed for the hd. Thanks for the advice. Yahoo.

---

### Post by ddwaner on 2008-03-20
Just inputting here.

I got done what I needed done with this topic at page 1 with the line.
> sudo chown username:username /path/to/mountpoint
it might be nice to add, "IN MY CASE" /media/disk-1 rather than /path/to/mountpoint but it did set the ownership on the drive.
I have been a Micro$oft Window$ user from DOS 3.3 to Window$ XP Pro, I'm a little unhappy with their End of Life for their operating system that cost "ME" hundreds of dollars that they no longer support. I've been fed up for a while so I started with the Linux operating systems and ended up with Knoppix version 5.1.1 both on CD and DVD. I have had both installed on hard drives as a full HD install and used them for months. I was gett N a little unhappy with the max screen res of 800x600 so I started looking again for maybe a "Better" Linux choice and someone suggested Ubuntu. I was putting it on a old Cyrux 500 that I have had NT 4.0 then Knoppix on. The live Ubuntu CD ran EXTREMELY slow with its 180 meg's of memory (I KNOW 250 is min), I went back and got the alternate and off I went with the install which went pretty well up to installing the Linux generic kernal then SPLAT. I ended up doing the step again with generic and again SPLAT. I ended up using a kernal other than generic which worked. Off again I went and up Ubuntu comes and already it starts default at 1280x700 (something) which was higher than even a Windows XP install would do with the vid card and monitor. GOOD GO'N... 
NOW COMES THE PROBLEMS
I set it for 1024x768 and I was logged on as admin. I get a data drive formatted ext3 and I can't change any of the permissions. I need to get to root terminal and log on, that worked in Knoppix, they put the option right on the bottom bar. It seems to me that logging on as administrator in Ubuntu should let me set things like drive access (OK ASK FOR THE ADMIN PASS each time). I've had a hard time gett N access to stuff as admin in Ubuntu. I guess they have their reasons for locking everything out.

---

