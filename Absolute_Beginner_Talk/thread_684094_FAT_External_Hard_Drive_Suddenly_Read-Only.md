---
title: "FAT External Hard Drive Suddenly Read-Only???"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by joeyt2k on 2008-01-31
None of the posts I've read solved this problem.

FAT 500GB external USB drive mounted in /media -- never had a problem with it -- now it's read-only. Changed nothing, modified nothing that I know of. Happened in the middle of a session. One second I could r/w, next I couldn't. 

Permissions tab says the owner can read/write.

ls -l for the drive says: 

drwx------   4 joeyt2k root 32768 2007-11-14 16:22 Documents
drwx------   2 joeyt2k root 32768 2008-01-31 15:01 Movies
drwx------ 208 joeyt2k root 32768 2008-01-29 22:11 Music
drwx------  19 joeyt2k root 32768 2008-01-17 19:48 Pictures
drwx------   4 joeyt2k root 32768 2008-01-28 07:12 Video

There's also a torrent that I stopped and deleted from the drive in my trash, won't let me delete it because the drive is read-only. I uninstalled bittorrent thinking maybe that was hanging it up somehow, no dice. 

Help is greatly appreciated.

---

### Post by approaching on 2008-01-31
with those permissions, it looks as if you should be able to read it. but, another user may not be able to. some programs belong to different groups, and i am not sure if you are trying to access this using something strange. if you want to test to see if permissions are the issue, you can add read, write, execute  to everyone (not fantastic security wise, please keep that in mind) you can do this.

sudo chmod -R +rwx <top directory>

that will make everything below that top directory and the top directory as well read, write, and executable by everyone. but i suggest you go look up a page on permissions before, so that you are aware how to change things back when you are done.

---

### Post by oedha on 2008-01-31
go to the root of the external HD
sudo chown -Rf root.root /  <--- if it's map before maybe will looks like /media/xxx
sudo chmod -rf 777 /    <--- if it's map before maybe will looks like /media/xxx

regards;
~E~

---

### Post by joeyt2k on 2008-01-31
Thank you both for replying.

sudo chmod -R +rwx /media/EXTHD results in the terminal running through every file in my HD and following with ": read-only file system." Still can't write to the disc.  

sudo chown -Rf root.root /media/EXTHD results in "chown: cannot access `/media/EXTHD/.Trash-joeyt2k/torrent: Input/output error" -- "torrent" being that torrent I can't delete from my trash. 

I get the same error about that torrent in my trash running sudo chmod -Rf 777 /media/EXTHD.

So is this torrent I stopped and sent to trash screwing something up?

Again, thanks for your prompt replies, any additional help is appreciated.

---

### Post by oedha on 2008-01-31
how if you unmount that disk then mount it again ?
sudo umount /media/hdext
then :==> sudo mount -a

the worst is reboot.......:( 

~E~

---

### Post by joeyt2k on 2008-01-31
I've tried unmounting and remounting both in terminal and with right-click unmount. Nothing. 

Are you suggesting I reformat the disk?

---

### Post by oedha on 2008-01-31
no......
reboot is better than reformat !!

~E~

---

### Post by Rocket2DMn on 2008-01-31
Do you have an entry in fstab for this drive?  Post the output of
```
cat /etc/fstab
```
Otherwise, have you tried mounting it manually?  What command are you using for that?

---

### Post by joeyt2k on 2008-01-31
fstab:

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=655b1f75-453c-4684-b8e3-06e416d760de / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=9cf38f6e-3f1f-4978-936e-ef3b0c6a15e2 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

I'm a noob, but it doesn't look like it's in there, right? 

Ubuntu mounts the drive, I never did anything, just plugged it in, dragged and drop with no problem, until today.

Thanks.

---

### Post by peitschie on 2008-01-31
Whats the output from running the following code in a terminal:
```
mount
```

Oh, and if it's an external hard drive, it will be detected and mounted by the udev scripts, not the fstab :)

---

### Post by Rocket2DMn on 2008-01-31
> **peitschie said:**
> Whats the output from running the following code in a terminal:
```
mount
```

Oh, and if it's an external hard drive, it will be detected and mounted by the udev scripts, not the fstab :)

Indeed, but it's always smart to ask anyway.  Some people have claimed to have entries in fstab and still get automount (though I don't know how, it never worked for me).

I would suggest unmounting the drive, turning it off, rebooting the computer, and then plugging it back in.

---

### Post by peitschie on 2008-01-31
Oh, I wasn't faulting your asking :)... it's always one of the best ways to learn/clarify...

It'd be good to get the output of the mount command before doing much more in case the drive is suddenly reporting filesystem errors or similar (which will commonly cause the drive to remount read-only).

I have had this problem with an NTFS drive on occasion when I tried to do something stupid to the permissions or file system.

---

### Post by Rocket2DMn on 2008-01-31
Yeah, I was just pointing out my reasoning.  Also, if we STILL couldn't get it to work, I was gonna go for specifying options with the mount command or try it from fstab.  If it STILL failed, then it's time for a little fsck :)  I probably just shoulda asked for "mount" at the same time, but you beat me to it before my next post, hehe.

---

### Post by Medieval_Creations on 2008-01-31
I didn't see this as an alternative an previous posts, so if I over looked it I appologize.

One thing that you can do as well is mount the drive manually and add options in the mount command to assign the any owne or group to that drive, such as:
```
sudo mount -o uid=<username>,gid=<username> /dev/sd## /media/
```
This is how I mount my external hard drives, so I know that no matter what type of drive I mount I will always have full permissions on it.

*Note: fill in the <username> with your ID (or whom ever you want to give permission to & replace the ## with the appropriate driver letter & # (example /dev/sdc1).

---

### Post by joeyt2k on 2008-02-04
Sorry for my delayed response.

Problem solved! Sort of ...

I decided to at least download some stuff while I was tinkering with this problem, try out some different bittorrent clients (NB: When I couldn't delete that torrent in my trash, I uninstalled bittorrent thinking it might be hanging up the drive).

So I installed rtorrent. Went to my hard drive. It was filled with .RXT files that weren't there before the rtorrent install. I checked, and I did not have "display hidden files" enabled. These files just showed up. 

Selected all the junk files, and, yes, I could delete them.

Full R/W access back to normal. No problems since. 

?

Thanks again.

---

### Post by zms on 2008-04-07
I am having the same problem. One day all of a sudden my external hd became read only...and i really do not want to format it i have tried everything posted here and have had no success...when i try to physically mount it in terminal and it says the folder doesnt exist...can someone please help me

---

