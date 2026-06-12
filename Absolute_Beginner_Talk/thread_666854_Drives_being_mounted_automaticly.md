---
title: "Drives being mounted automaticly"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Fox McCloud on 2008-01-13
I recently reinstalled Ubuntu, and now all my drives are being mounted automaticly when I log in. How do I return to manually mounting drives?

---

### Post by Rocket2DMn on 2008-01-13
A funny request, normally people want them to mount automatically.  Commenting out the entries in /etc/fstab for each partition should stop them from mounting automatically.
```
gksudo gedit /etc/fstab
```
Place a # sign at the beginning of the lines for the partitions you don't want to automount.

Otherwise, you can leave them enabled and add the "noauto" option to the partitions you don't want to automount.

---

### Post by Fox McCloud on 2008-01-13
Yeah, I got used to mounting them manually. :) Makes it easier for me to keep track of things.

So, like this?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hdb1
UUID=c9adaa0f-aba2-43ea-bea2-c7a6485ef782  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/hda1
UUID=3A945E58945E172B                      /media/hda1    ntfs         defaults,umask=007,gid=46   0  1  
# /dev/hdb2
UUID=45628DD870424EDB                      /media/hdb2    ntfs         defaults,umask=007,gid=46   0  1  
# /dev/hdb4
UUID=d5d43e81-b1ed-40b4-a3fe-49df700b5d71  /media/hdb4    ext3         defaults                    0  2  
# /dev/hdb3
UUID=bd8bbb1c-28bf-40b5-a54b-b35c809eba32  none           swap         sw                          0  0  
#/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto,exec            0  0  
#/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto,exec            0  0  
#/dev/hda1                                  /media/hda1    ntfs         defaults                    0  0  
#/dev/hdb2                                  /media/hdb2    ntfs         defaults                    0  0  
#/dev/hdb3                                  /media/hdb3    swap         defaults                    0  0  
#/dev/hdb4                                  /media/hdb4    ext3         defaults                    0  0  
#/dev/hdb1                                  /media/hdb1    ext3         defaults                    0  0  
```

---

### Post by Rocket2DMn on 2008-01-13
That should work,  If for some reason they still mount (like if it's a USB drive that gets plugged in), uncomment the lines by removing the # and put "noauto" in the options column.

---

### Post by Fox McCloud on 2008-01-13
Huh, it's still auto mounting.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hdb1
UUID=c9adaa0f-aba2-43ea-bea2-c7a6485ef782  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/hda1
UUID=3A945E58945E172B                      /media/hda1    ntfs         defaults,umask=007,gid=46   0  1  
# /dev/hdb2
UUID=45628DD870424EDB                      /media/hdb2    ntfs         defaults,umask=007,gid=46   0  1  
# /dev/hdb4
UUID=d5d43e81-b1ed-40b4-a3fe-49df700b5d71  /media/hdb4    ext3         defaults                    0  2  
# /dev/hdb3
UUID=bd8bbb1c-28bf-40b5-a54b-b35c809eba32  none           swap         sw                          0  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto,exec            0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto,exec            0  0  
/dev/hda1                                  /media/hda1    ntfs         defaults,noauto                    0  0  
/dev/hdb2                                  /media/hdb2    ntfs         defaults,noauto                    0  0  
/dev/hdb3                                  /media/hdb3    swap         defaults,noauto                    0  0  
/dev/hdb4                                  /media/hdb4    ext3         defaults,noauto                    0  0  
/dev/hdb1                                  /media/hdb1    ext3         defaults,noauto                    0  0  
```

And this might be a little off-topic, but it seems every time I reinstall Ubuntu it little different. Like this issue, and last time it was something else. Like something that worked last time doesn't now, but I'm usually able to fix it...oh well, I love this OS anyway. :)

---

### Post by Rocket2DMn on 2008-01-13
You have multiple entries in your fstab for your partitions.  All the entries with UUID= are the same devices but based on ID numbers rather than device labels.  In essence, all your parts with /dev/hd** are being ignored because they are listed above.  Comment out the entires with /dev and add the "noauto" option to the partitions you want.
DO NOT ADD IT TO hdb1 SINCE THIS IS YOUR ROOT PARTITION.  Same with hdb3 as this is your swap partition.  Wouldn't add it to proc either.
Keep hdc and hdb the way they were originally since these are cd drives.
File should probably look like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hdb1
UUID=c9adaa0f-aba2-43ea-bea2-c7a6485ef782  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/hda1
UUID=3A945E58945E172B                      /media/hda1    ntfs         defaults,umask=007,gid=46,noauto   0  1  
# /dev/hdb2
UUID=45628DD870424EDB                      /media/hdb2    ntfs         defaults,umask=007,gid=46,noauto   0  1  
# /dev/hdb4
UUID=d5d43e81-b1ed-40b4-a3fe-49df700b5d71  /media/hdb4    ext3         defaults,noauto                    0  2  
# /dev/hdb3
UUID=bd8bbb1c-28bf-40b5-a54b-b35c809eba32  none           swap         sw                          0  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto,exec            0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto,exec            0  0  
#/dev/hda1                                  /media/hda1    ntfs         defaults,noauto                    0  0  
#/dev/hdb2                                  /media/hdb2    ntfs         defaults,noauto                    0  0  
#/dev/hdb3                                  /media/hdb3    swap         defaults,noauto                    0  0  
#/dev/hdb4                                  /media/hdb4    ext3         defaults,noauto                    0  0  
#/dev/hdb1                                  /media/hdb1    ext3         defaults,noauto  
```

---

### Post by Fox McCloud on 2008-01-13
Ok, I'm going to give that a try.  :)

---

### Post by Fox McCloud on 2008-01-13
Ok, that did the trick. Thank you for the help ^_^

---

### Post by Fox McCloud on 2008-01-14
Huh, I got them to not auto-mount, but now I can't mount them unless I'm root. I get a window with Permission Denied. I want have Ubuntu ask me for a password but I can't seem to get it to work.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                               0  0  
# /dev/hdb1
UUID=c9adaa0f-aba2-43ea-bea2-c7a6485ef782  /              ext3         defaults,errors=remount-ro             0  1  
# /dev/hda1
UUID=3A945E58945E172B                      /media/hda1    ntfs         defaults,umask=007,gid=46,noauto  0  1  
# /dev/hdb2
UUID=45628DD870424EDB                      /media/hdb2    ntfs         defaults,umask=007,gid=46,noauto  0  1  
# /dev/hdb4
UUID=d5d43e81-b1ed-40b4-a3fe-49df700b5d71  /media/hdb4    ext3         defaults,noauto                   0  2  
# /dev/hdb3
UUID=bd8bbb1c-28bf-40b5-a54b-b35c809eba32  none           swap         sw                                     0  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto,exec                       0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto,exec                       0  0  
#/dev/hda1                                  /media/hda1    ntfs         defaults,noauto                        0  0  
#/dev/hdb2                                  /media/hdb2    ntfs         defaults,noauto                        0  0  
#/dev/hdb3                                  /media/hdb3    swap         defaults                               0  0  
#/dev/hdb4                                  /media/hdb4    ext3         defaults,noauto                        0  0  
#/dev/hdb1                                  /media/hdb1    ext3         defaults                               0  0  
```

---

### Post by Rocket2DMn on 2008-01-14
When you mount drives, you typically have to use root permissions through sudo.  So if you want to mount hdb2, you would say
```
sudo mount /dev/hdb2
or
sudo mount /media/hdb2
```
I know for sure this works with ntfs, but if you run into the problem with ext3, you may need to fiddle with the options a little.  The almighty How to fstab thread can be found here - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) - it is a very useful resource.

---

### Post by vanadium on 2008-01-14
There are many options yo can put in your /etc/fstab, see "man mount". Moreover, it makes no sense not mounting the swap.

---

### Post by Fox McCloud on 2008-01-14
> **Rocket2DMn said:**
> When you mount drives, you typically have to use root permissions through sudo.  So if you want to mount hdb2, you would say
```
sudo mount /dev/hdb2
or
sudo mount /media/hdb2
```
I know for sure this works with ntfs, but if you run into the problem with ext3, you may need to fiddle with the options a little.  The almighty How to fstab thread can be found here - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) - it is a very useful resource.

Ok, I will try that when I return form work.

---

### Post by Fox McCloud on 2008-01-14
I looked, at that link and I can't really find what I'm looking for. I basiclly want mounting to work like it does in Live CD, to mount them in GNOME and not the terminal.

After I made those changes I get this prompt:
[img]http://fmccloud.googlepages.com/Screenshot-gnome-mount.png[/img]

Thanks in advance!

---

### Post by Rocket2DMn on 2008-01-14
OK, so are you just trying to mount from Computer in nautilus?  Try adding "user" to the options for the correct partitions (hda1, sdb2, and sdb4 I believe).  Make sure you do it on the UUID ones - you can go ahead and remove the repeated ones at the bottom that we commented out.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                               0  0  
# /dev/hdb1
UUID=c9adaa0f-aba2-43ea-bea2-c7a6485ef782  /              ext3         defaults,errors=remount-ro             0  1  
# /dev/hda1
UUID=3A945E58945E172B                      /media/hda1    ntfs         defaults,umask=007,gid=46,noauto,user  0  1  
# /dev/hdb2
UUID=45628DD870424EDB                      /media/hdb2    ntfs         defaults,umask=007,gid=46,noauto,user  0  1  
# /dev/hdb4
UUID=d5d43e81-b1ed-40b4-a3fe-49df700b5d71  /media/hdb4    ext3         defaults,noauto,user                   0  2  
# /dev/hdb3
UUID=bd8bbb1c-28bf-40b5-a54b-b35c809eba32  none           swap         sw                                     0  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto,exec                       0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto,exec                       0  0  
```
As a sidenote, this disallows executing of binaries from those partitions, this probably won't be a problem.  See the man pages for mount for more details
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)
and
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Fox McCloud on 2008-01-14
This is such a pesky problem, now the error window has changed:
[img]http://fmccloud.googlepages.com/Screenshot-gnome-mount-1.png[/img]
I can mount them using the terminal and a program I found searching Storage Device Manager, but they work because of course I'm under sudo.

---

### Post by Rocket2DMn on 2008-01-14
This is turning into a nightmare.  At this point I'm gonna start postulating some theories.
gid might be causing problems, along with umask (since we are allowing all users to mount).  Also, I think it should be ntfs-3g, not just ntfs (may not matter).
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                               0  0  
# /dev/hdb1
UUID=c9adaa0f-aba2-43ea-bea2-c7a6485ef782  /              ext3         defaults,errors=remount-ro             0  1  
# /dev/hda1
UUID=3A945E58945E172B                      /media/hda1    ntfs-3g         defaults,noauto,user  0  1  
# /dev/hdb2
UUID=45628DD870424EDB                      /media/hdb2    ntfs-3g         defaults,noauto,user  0  1  
# /dev/hdb4
UUID=d5d43e81-b1ed-40b4-a3fe-49df700b5d71  /media/hdb4    ext3         defaults,noauto,user                   0  2  
# /dev/hdb3
UUID=bd8bbb1c-28bf-40b5-a54b-b35c809eba32  none           swap         sw                                     0  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto,exec                       0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto,exec                       0  0
```

Will ANY of these mount?

---

### Post by Fox McCloud on 2008-01-14
hdb4 will mount without a problem,
I've been working so hard on getting hda1, hdb2, to mount, I forgot to check hdb4 would. Which it does.

---

### Post by Rocket2DMn on 2008-01-14
For the ntfs drives, lets try these options:
```
rw,noauto,user,exec
```

---

### Post by Fox McCloud on 2008-01-14
I added that to my hda1 partition, and when I try to mount, nothing happens. :\

---

### Post by Rocket2DMn on 2008-01-14
Show me fstab please.

---

### Post by Fox McCloud on 2008-01-14
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                               0  0  
# /dev/hdb1
UUID=c9adaa0f-aba2-43ea-bea2-c7a6485ef782  /              ext3         defaults,errors=remount-ro             0  1  
# /dev/hda1
UUID=3A945E58945E172B                      /media/hda1    ntfs         defaults,umask=007,gid=46,rw,noauto,user,exec  0  1  
# /dev/hdb2
UUID=45628DD870424EDB                      /media/hdb2    ntfs         defaults,umask=007,gid=46,noauto,user  0  1  
# /dev/hdb4
UUID=d5d43e81-b1ed-40b4-a3fe-49df700b5d71  /media/hdb4    ext3         defaults,noauto,user                   0  2  
# /dev/hdb3
UUID=bd8bbb1c-28bf-40b5-a54b-b35c809eba32  none           swap         sw                                     0  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto,exec                       0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto,exec                       0  0
```

I hope I did it correctly :|

---

### Post by Rocket2DMn on 2008-01-14
Thought so, I meant to replace the current options with the new ones.  Guess I didn't say that very well to begin with, sorry.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
oaproc                                       /proc          proc         defaults                               0  0  
# /dev/hdb1
UUID=c9adaa0f-aba2-43ea-bea2-c7a6485ef782  /              ext3         defaults,errors=remount-ro             0  1  
# /dev/hda1
UUID=3A945E58945E172B                      /media/hda1    ntfs         rw,noauto,user,exec  0  1  
# /dev/hdb2
UUID=45628DD870424EDB                      /media/hdb2    ntfs         rw,noauto,user,exec  0  1  
# /dev/hdb4
UUID=d5d43e81-b1ed-40b4-a3fe-49df700b5d71  /media/hdb4    ext3         defaults,noauto,user                   0  2  
# /dev/hdb3
UUID=bd8bbb1c-28bf-40b5-a54b-b35c809eba32  none           swap         sw                                     0  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto,exec                       0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto,exec                       0  0
```

---

### Post by Fox McCloud on 2008-01-14
Same results. Nothing happens when I mount the partitions.

---

### Post by Rocket2DMn on 2008-01-15
I've been looking around for a solution to this problem and it seems other people have this issue, and I still haven't found a solution.  Technically, the "noauto" option should do it.
So I think right now we have the drives unmounted and NOT mounting on boot right?  But now we are trying to get them to mount?
Can you mount the drives from terminal with like
```
sudo mount /media/hda1
```?
If not, change the options back to
```
defaults,umask=007,gid=46,noauto
``` which is where we were when you got it to not automount.  Please try mounting from terminal with these options (if it doesnt work with current options) and post back.

---

### Post by Fox McCloud on 2008-01-15
Yup, doing it from terminal will mount the drive.

---

### Post by Rocket2DMn on 2008-01-15
Well man, I really can't think of what else there is to do to allow you to mount the drive from nautilus.  Try unmounting the drive and running this:
```
pmount /media/hda1
```
(If you don't have pmount, get it from the repos and try).

What I'm getting at is setting you up with a shortcuts in your taskbar to mount / unmount the drives which will just run the terminal commands.  If we can use pmount, it won't require you to enter a password when you mount.
This would have you create launchers with right click the panel where you want the shortcuts to be and hitting Add to Panel and selecting Custom Application Launcher.  You would want a terminal application with the command that works best (pmount if possible, sudo mount otherwise).  This means you wouldn't have to type out the mount command every time you want to mount the partitions.

---

### Post by Fox McCloud on 2008-01-15
I will try this first thing tomorrow . :) I need to go to bed, and thank you for helping me with this issue. It's much appreciated. :)

---

