---
title: "[SOLVED] 2 cd drives showing - I've only got 1!"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-24
Would anybody be able to explain to me why my computer browser shows 

CD-ROM-1 in places on my computer browser - but in the right pane I have 2 showing - incidentally the one that actually is physically present is the CD-RW/DVD drive 

It's not a new thing thing it's just bugging me now

The CDRW drive automounts and works fine from within the browser - the other only exists as a phantom it would appear 

I've looked at CDROM posts for days but can't seem to find any that match?

I'd quite like a new drive - but while I wait for a new case and drive how can I tell OS I've not got the odd one!:D

---

### Post by Pragmatist on 2007-05-24
Lets see what HAL thinks.  The command **lshal** will give you alot of output, so if you post it here, make sure to attach it in a file.  A quicker, but possibly less accurate, search is:
```
lshal -s | grep CD
```

This should only give you a couple of lines, which you should post here.

---

### Post by bobplano on 2007-05-24
maybe the other one is just a sybolic link. try putting in a cd and looking at both the cd drives. if they show the same one it's just a symbolic link

---

### Post by discmaster on 2007-05-24
Hi forestpixie,

I don't have a solution, but just wanted to mention; I have (2) identical cdr/dvdr drives, but only 1 shows up in computer; however, when I use either one, they both work fine...

---

### Post by fearpi on 2007-05-24
I also have an extra CD-ROM drive showing in nautilus. It refers to /media/cdrom0, which I manually removed some weeks ago after I upgraded to Feisty (Feisty no longer uses cdrom0, but the name of the inserted disc). I get no output from ```
lshal -s | grep CD
``` nor from ```
lshal -s | grep cd
``` I wonder if this issue is only being experienced by users who upgraded older versions to Feisty.

---

### Post by Pragmatist on 2007-05-24
It probably has to do with gnome-volume-manager, which in turn uses HAL, which uses UDEV, etc...etc... :)  It is on the top level, so you need to see what it rests on to understand why it is acting the way it is.  As I said, using **lshal -s |grep CD  **is a very restricted way to search the HAL database.  Try this, replacing "filename" with a name of your choosing:
```
lshal >> filename
```

This will give the complete HAL listing and put it in a file called filename.  Then, attach the file here for us to examine.  If you have trouble attaching, make sure you use an extension that is acceptable to Ubuntu forums (they have restrictions).  If there is a problem, just pick any allowed extension and add it to the file just to be able to attach it.  The main thing is NOT to post the entire output as it is large!

---

### Post by fearpi on 2007-05-24
Thanks for bearing with me. I've attached the output of lshal.

---

### Post by forestpixie on 2007-05-25
HI -I only get 

volume_uuid_2CD403EFD403BA5A

as a result of lshal -s | grep CD.

Have attached output of lshal

I I put a cd in the CDRW it is replaced by the cd name and can be navigated - trying to open the phantom drive gives me the error

mount: special device /dev/hdc does not exist 

- which is to be expected I suppose because it doesn't.

---

### Post by forestpixie on 2007-05-25
sorry didn't attach file

---

### Post by darkworld on 2007-05-25
I had cdromdrive problems, I have two but only one got configured and was usable. I put a symlink in and alls fine.

Things improved a lot when i got a version of feisty 7.04 that didnt install and config everything in sdx format. people told me I have the feisty 7.04 pre release that config in hdx format. A lot of problems just went away.

---

### Post by forestpixie on 2007-05-25
I have actually only got 1 physically - it's only UBuntu which insists on telling me I have 2 of the things 

It's not a symbolic link - because it always gives the device doesn't exixt if I try and open a cd which has been inserted.

The link to the real drive works fine - it's just this phantom drive which is annoying me.

---

### Post by forestpixie on 2007-05-25
'bump

---

### Post by NxvbFngb on 2007-05-25
I got the same issue after upgraded to 2.6.20-16 kernel.  So I downgraded to the 2.6.20-15 version and it's fine now.

---

### Post by rfurman24 on 2007-06-03
I have the same thing. I just installed feisty. I see when I boot I have the old kernel and the new listed in Grub. I do not want to nor do I know how to downgrade kernels. I would like to figure out what to do to fix it the correct way.

---

### Post by Pragmatist on 2007-06-03
Type this in a terminal:
```
ls -l /dev >> devfile
```

Then, attach the file called "devfile" on your next post.

---

### Post by rfurman24 on 2007-06-03
Is it ok for me to post on this thread since I did not start it or should I start a new one? Here is my devfile.

---

### Post by Pragmatist on 2007-06-03
> **rfurman24 said:**
> Is it ok for me to post on this thread since I did not start it or should I start a new one?...

It is ok, if you have the same problem.

You appended the /dev directory twice, so your "devfile" contains duplicates of every file from your /dev directory.   Anyway, if your getting a "phantom" drive appearing in Nautilus (the file manager), then you want to see the symbolic links in /dev  The reason is that many programs use the symbolic link (since they don't necessarily now the exact dev file that your using).  Some common symbolic links are /dev/dvd  and  /dev/cdrom  If you notice, you have these relevant symbolic links:
> 
lrwxrwxrwx 1 root root           3 2007-06-03 05:44 cdrom -> hdc
lrwxrwxrwx 1 root root           3 2007-06-03 05:44 cdrw -> hdd
lrwxrwxrwx 1 root root           3 2007-06-03 05:44 dvd -> hdc
lrwxrwxrwx 1 root root           3 2007-06-03 05:44 dvdrw -> hdd


So your /dev/hdc can be referenced by three names:
/dev/hdc   The real file
/dev/cdrom
/dev/dvd

And, your /dev/hdd can be referenced by three names:
/dev/hdd   The real file
/dev/cdrw
/dev/dvdrw

Do you only have one drive?  If so, which is its dev file?  You can check by trying to eject:
```
eject /dev/hdc
```
```
eject /dev/hdd
```

Which one of those files does not correspond to a drive?

---

### Post by rfurman24 on 2007-06-03
There are two matching folders in /media. If I try to mount the "phantom drives" it says can not  mount and points to /dev/scd0 and /dev/scd1. Neither of them exists in /dev. If I delete the matching folders in /media and try to mount the drives it then says can not mount no /media/cdrom0 and /media/cdrom1. The real symlinks are /dev/dvdrw and dev/dvdrom I think.

---

### Post by Pragmatist on 2007-06-03
> **Pragmatist said:**
> You can check by trying to eject:
```
eject /dev/hdc
``````
eject /dev/hdd
```Which one of those files does not correspond to a drive?

Did you try the eject method that I suggested?

---

### Post by rfurman24 on 2007-06-03
/dev/hdc is my dvd rom. /dev/hdd is my writer. /dev/dvd is also my dvd rom. /dev/dvdrw is also my writer. If I am in, say, Kaudiocreator I can use /dev/hdc or /dev/dvd for my rom or /dev/hdd or /dev/dvdrw for my writer but in places-computer the cdrom1 and cdrom2 icons do absolutely nothing. Your eject commands did exactly what they should they ejected the corresponding drive. I just checked one more thing I can also use /dev/cdrom for my dvd rom and /dev/cdrw for my writer.

---

### Post by fearpi on 2007-06-03
Open your fstab file:

```
gksudo gedit /etc/fstab
```

Comment out the line corresponding to the 'phantom' device. I believe you can find this by going into nautilus and right-clicking the phantom drive and attempting to mount (or dismount) it, and reading the error you should get. Mine was 'cdrom0', so I commented out the line for /media/cdrom0 by adding '#' at the beginning:

```
# /dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
```

Ubuntu no longer mounts a device to that location on startup, and all is peachy for me. Make sure you have the right line, though - you don't want to comment out the wrong one, or you may find that on your next boot, your hard drive isn't mounted!

---

### Post by rfurman24 on 2007-06-03
That did it. Thanks very much. I had three entries in my fstab that did not belong including a phantom floppy drive. I love the Ubuntu Community.

---

### Post by forestpixie on 2007-06-04
Whoops - that's exactly what I had done when I set thread resolved - thought I'd written it in for the next person - sorry!

#-o

---

