---
title: "[SOLVED] I demolished 7.04, recover or redo?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by neander on 2007-08-17
I had a healthy new 7.04 install, then did stuff with bash and dash (attempting to repro some stuff that worked with 6.10), and seem to have lost it. sudo no longer worked and when I rebooted it gives me a lot of exciting "unable to execute bin/sh" for rcS: not a directory messages.

I wouldn't mind reinstalling for the practice but there is a text file on the desktop that I'd like to recover, it had a shorthand of the steps I took to get 7.04 up and running. I can live without it but...booting from the cd, is there a way to get that doc, save it to floppy or email to myself? I've tried su - root and the pswd for that is not known to me, and su - mylogin, and it reports not valid or something. I started the reinstall process and on step approx 5, no users were found to import from. How can I get to that user's desktop? Not visible from Nautilus, so far.

---

### Post by Pragmatist on 2007-08-17
> **neander said:**
> ....is there a way to get that doc, save it to floppy or email to myself?....

Have you tried a LiveCD?

---

### Post by neander on 2007-08-17
Yes I can boot with the cd but I don't know how to get to my orig user's doc with that more generic login...the livecd req's no password etc. I would guess that there is a way to recover that doc with livecd but I'm looking for some help with how to go about that.

---

### Post by Pragmatist on 2007-08-17
Do you know where the file is, and do you know its name?

---

### Post by mikewhatever on 2007-08-17
You have to mount the partition Ubuntu is on to get access to the files.
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by neander on 2007-08-17
Yes I know the file name and location. I'll scope out remounting the partition.

---

### Post by neander on 2007-08-17
I have found the file, it's in home/root, probably because I didn't know what I was doing at the time <g>

I would like to copy it, but must use the command line to do so since at Nautilus won't show me the home/root dir. I'm not able to use cp because the file name has spaces in it. I have been searching for a concise explanation of how to deal with that...no luck so far. Anyone want to clue me in? Example of what is not working:

cp /dev/null/media/ubuntu/root/Desktop/'ubuntu 7.04 config 20070816' /media/ubuntu 

I'm attempting to copy the file to /media/ubuntu, the partition I mounted to attempt this rescue.

---

### Post by schorsch on 2007-08-17
Please try:

```
cp "/dev/null/media/ubuntu/root/Desktop/ubuntu 7.04 config 20070816" /media/ubuntu
```
or
```
cp /dev/null/media/ubuntu/root/Desktop/ubuntu\ 7.04\ config\ 20070816 /media/ubuntu
```
or use the famous bash completion:

type: "cp /dev/null/media/ubuntu/root/Desktop/ubuntu" and then double type the TAB-Key; it should expand the file name(s?) with the right quotes, so you simply have to add the destination afterwards.

---

### Post by Pragmatist on 2007-08-17
> **neander said:**
>  Example of what is not working:

cp /dev/null/media/ubuntu/root/Desktop/'ubuntu 7.04 config 20070816' /media/ubuntu 

I'm attempting to copy the file to /media/ubuntu, the partition I mounted to attempt this rescue.

Is it a directory?  If so, you use **cp -rf** not **cp** If it is just a file, try double quotes:
```
 cp /dev/null/media/ubuntu/root/Desktop/[COLOR=Red]**"**[/COLOR]ubuntu 7.04 config 20070816[COLOR=Red]**"**[/COLOR]/media/ubuntu 
```
You may need to use sudo if you don't have permissions.

---

### Post by schorsch on 2007-08-17
BTW: The mount pount /dev/null/.... looks a little bit .... weird .... ;-)

---

### Post by neander on 2007-08-17
Thanks for trying to help, both of you.

None of those work. Frustrating. The failure is always

cp: cannot stat: '/dev/null/media/ubuntu/root/Desktop/ubuntu 7.04 config 20070816' is not a directory

Same error message for both these:
cp /dev/null/media/ubuntu/root/Desktop/"ubuntu 7.04 config 20070816" /media/ubuntu
cp -rf /dev/null/media/ubuntu/root/Desktop/"ubuntu 7.04 config 20070816" /media/ubuntu

The file's name that I'm trying to copy is 

ubuntu 7.04 config 20070816

---

### Post by neander on 2007-08-17
Re the odd mount point...I just tried to follow the instructions that someone pointed to, maybe didn't turn out as expected, this is all foreign to me.

Thanks

---

### Post by schorsch on 2007-08-17
I guess there is something wrong with your path starting with "/dev/null" as mentioned before. Where exactly have you mounted the HD partition while running the Live-CD?:
```
mount
``` and post the output here please.

---

### Post by Pragmatist on 2007-08-17
> **neander said:**
> Thanks for trying to help, both of you.

None of those work. Frustrating. The failure is always

cp: cannot stat: '/dev/null/media/ubuntu/root/Desktop/ubuntu 7.04 config 20070816' is not a directory

Same error message for both these:
cp /dev/null/media/ubuntu/root/Desktop/"ubuntu 7.04 config 20070816" /media/ubuntu
cp -rf /dev/null/media/ubuntu/root/Desktop/"ubuntu 7.04 config 20070816" /media/ubuntu

The file's name that I'm trying to copy is 

ubuntu 7.04 config 20070816
Use the **file **command:
```
file "/dev/null/media/ubuntu/root/Desktop/ubuntu 7.04 config 20070816"
```
edit: and post the output here :)

---

### Post by neander on 2007-08-17
Entered:

file "/dev/null/media/ubuntu/root/Desktop/ubuntu 7.04 config 20070816"

ERROR: cannot open 'blah blah' (not a directory)

then:

ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda1 on /media/ubuntu type ext3 (rw)

---

### Post by schorsch on 2007-08-17
> **neander said:**
> /dev/hda1 on /media/ubuntu type ext3 (rw)

ok, from all the command options we gave to you, just delete the starting "/dev/null" so to start with "/media/ubuntu" and you should be done ...

---

### Post by neander on 2007-08-17
Aha, I'd just tested without the dev/null and it was good

ubuntu@ubuntu:~$ file "/media/ubuntu/root/Desktop/ubuntu 7.04 config 20070816"
/media/ubuntu/root/Desktop/ubuntu 7.04 config 20070816: ASCII text

And yes clipping that prefix off made the cp work (in combination with sudo)

Thanks, you guys are incredible! I really appreciate the help. The file was not worth the trouble in itself but I have to get exposure to more of this stuff if I'm going to have any chance of being able to walk ten feet with ubuntu and not fall over.

---

### Post by schorsch on 2007-08-17
Glad to hear that! If you have any further questions, just ask; there are many helping hands around .... And could please mark this and the other thread for the same questions as solved as this could help other users?

---

