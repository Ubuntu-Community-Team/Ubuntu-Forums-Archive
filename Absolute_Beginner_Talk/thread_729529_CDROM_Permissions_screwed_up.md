---
title: "CDROM Permissions screwed up?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-03-19
When ever I stick a disk in my CD/DVD drive I get the following popup:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/cdrom-permissions.png[/IMG]

I went to my user's permissions (System->Administration->Users and Groups) and I have "Use CD-ROM drives" checked off for my user.

Here is what my fstab looks like:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=848e4473-41c7-4d0a-acc5-4aca64117868 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ad1c7fb1-a306-490d-8cd8-593420068929 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```
Why am I getting this message, I think I've covered all my bases, right?

---

### Post by wormser on 2008-03-20
You /etc/fstab looks like mine so it should be fine.  This is a bit of a shot in the dark but give it a try.  Is you user in the cdrom group?

```
less /etc/group | grep -i cdrom
```

---

### Post by BassKozz on 2008-03-20
There is no cdrom group :confused:

---

### Post by wormser on 2008-03-20
> **B/-\ssKozz said:**
> There is no cdrom group :confused:

Where did you look for the cdrom group?  I just checked in System> Administration> User and Groups> Manage Groups and did not see CD-rom in mine.  Did you check in /etc/group?

```
less /etc/group
```

---

### Post by BassKozz on 2008-03-20
> **wormser said:**
> Where did you look for the cdrom group?  I just checked in System> Administration> User and Groups> Manage Groups and did not see CD-rom in mine. 

That's where I looked and there wasn't one...
> **wormser said:**
> 
 Did you check in /etc/group?

```
less /etc/group
```
Just did, and yup my username is listed there right next to cdrom...
```
cdrom:x:24:haldaemon,user
```

So why am I getting these popups claiming I don't have permission?

---

### Post by erginemr on 2008-03-20
Can you please list the permissions on the /media folder and its subfolders:
```
ls -l /media
```
All subdirectories should be owned by root, but other users should have read and execute permissions as in "drwxr-xr-x".

---

### Post by BassKozz on 2008-03-20
> **erginemr said:**
> Can you please list the permissions on the /media folder and its subfolders:
```
ls -l /media
```
All subdirectories should be owned by root, but other users should have read and execute permissions as in "drwxr-xr-x".
```
$ ls -l /media
total 12
lrwxrwxrwx 1 root  root     6 2008-02-17 12:12 cdrom -> cdrom0
drwxr-xr-x 2 root  root  4096 2008-02-17 12:12 cdrom0
drwxr-xr-x 7 user  user  4096 2008-03-19 23:22 extra_storage1
lrwxrwxrwx 1 root  root     7 2008-02-17 12:12 floppy -> floppy0
drwxr-xr-x 2 root  root  4096 2008-02-17 12:12 floppy0
```

---

### Post by wormser on 2008-03-20
The permissions are exactly the same as mine.  It must be something else.  Have you  tried different CDs or try mounting it manually?

```
sudo mount /dev/scd0 /media/cdrom0 -o loop
```

I am not an expert at mounting but that should work.

---

### Post by erginemr on 2008-03-20
Yep. There is nothing wrong with either "cdrom:x:24:haldaemon,user" or the permissions...

---

### Post by BassKozz on 2008-03-20
> **wormser said:**
> The permissions are exactly the same as mine.  It must be something else.  Have you  tried different CDs or try mounting it manually?

```
sudo mount /dev/scd0 /media/cdrom0 -o loop
```

I am not an expert at mounting but that should work.
I just tried manually mounting using the line above and I heard the DVD spin-up, but still getting the same error message about permissions...
I then tried another CD/DVD and it worked... ](*,)
So the culprit was the DVD, but what I don't understand is that the DVD is just a home-made video recording (I transfered some VHS's to DVD a while back) and shouldn't be copy protected, so why isn't it letting me access my home-made DVD's?
Also I was able to copy the DVD successfully using K3b, so why can I copy w/ K3b but I can't access the DVD's contents using Nautilus... I also can't play the DVD on Ubuntu using "Movie Player" or "MPlayer Movie Player" :confused:

---

### Post by erginemr on 2008-03-20
Glad that your DVD drive works...

To rule out the possibility of K3b settings being the culprit, I suggest you to uinstall and use another CD burner software such as Gnomebaker, Brasero or Graveman, burn the same video to another DVD and check if you can access that later on.

---

### Post by jseiser on 2008-03-20
i know in arch you need to be a member of the optical group.  So I would wait for a more knowledgeable person comes along before you try this, but this might help if ubuntu uses that group.

gpasswd -a username optical

---

### Post by BassKozz on 2008-03-20
> **erginemr said:**
> 
To rule out the possibility of K3b settings being the culprit, I suggest you to uinstall and use another CD burner software such as Gnomebaker, Brasero or Graveman, burn the same video to another DVD and check if you can access that later on.
No,no,no, you don't understand K3b works FINE, I was able to successfully backup the DVD using K3b... but that same disk I was unable to access via Nautilus, or Movie Player, or MPlayer.
I can't figure out why because it was a home made DVD (not copy protected)
> **B/-\ssKozz said:**
> So the culprit was the DVD, but what I don't understand is that the DVD is just a home-made video recording (I transfered some VHS's to DVD a while back) and shouldn't be copy protected, so why isn't it letting me access my home-made DVD's?
Also I was able to copy the DVD successfully using K3b, so why can I copy w/ K3b but I can't access the DVD's contents using Nautilus... I also can't play the DVD on Ubuntu using "Movie Player" or "MPlayer Movie Player" :confused:

---

### Post by erginemr on 2008-03-20
I understood that k3b can write to DVD's successfully, but am suspecting of it setting a DVD region code or something. So, that's why, I still suggest you to install, say GnomeBaker with
```
sudo aptitude install gnomebaker
```
burn another video DVD, try it and uninstall gnomebaker with:
```
sudo aptitude remove gnomebaker
```

---

### Post by BassKozz on 2008-03-24
> **erginemr said:**
> I understood that k3b can write to DVD's successfully, but am suspecting of it setting a DVD region code or something. So, that's why, I still suggest you to install, say GnomeBaker with
```
sudo aptitude install gnomebaker
```
burn another video DVD, try it and uninstall gnomebaker with:
```
sudo aptitude remove gnomebaker
```

Sorry for the delay, I finally got around to trying gnomebaker, and no luck :(
Still the same permissions problem :confused:

---

### Post by zeerover on 2008-05-03
I think I'm in the same boat. I just posted a [thread]("http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4874912") (I searched the forums for hours but only came across your post after submitting mine) on a similar topic. In my case CDs (both data & audio) work but DVDs (both data & video) get permission errors. Please crosspost any solutions!

---

### Post by zeerover on 2008-05-04
(Cross-posted to [**Plextor PX-504A won't read DVDs (reads CDs)**]("http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4874912"))

Okay I think I'm on my way to a solution. I won't have time to write up a thorough explanation, or to work through all the kinks, but I did find the source of the problem and a half-decent workaround. It turns out that [COLOR="Red"]this has been a known issue in Ubuntu for 3 1/2 years[/COLOR] (no comment) that has taken a few slightly different forms. It seems to be best documented as [**Bug #10550**]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550"). For now I'll post [**Ric Flomag's helpful reply**]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550/comments/33") to that thread:

[INDENT]"[COLOR="Blue"][B]Quick fix: i have put iso9660 before udf in fstab to always mount dvds as iso9660:
/dev/hdc /media/cdrom0 iso9660,udf user,noauto,utf8 0 0[/B][/COLOR]
(the "utf8" option is a workaround to another long standing and very annoying bug, [https://bugs.launchpad.net/ubuntu/+bug/22623](https://bugs.launchpad.net/ubuntu/+bug/22623), but does not have any effect here.)

Totem now plays my DVD just fine. Obviously, this is not a good solution for everyone, but as i don't mind mounting my udf data DVDs as iso9660, it does not matter to me.

This bug as been here for a long time now"[/INDENT]

So this can be worked around by editing your /etc/fstab file to change the order from udf,iso9660 to iso9660,udf (not auto as some posters here have suggested, though they were clearly on the right track; likewise, the suggestion to fiddle with the utf-8 option was a right-minded trick that worked on a related bug, [**#22623**]("https://bugs.launchpad.net/ubuntu/+bug/22623")). What this does do is gives you access to protected discs (another way would be to format the relevant partitions in pre-protected file formats like fat32. 

A downside, however, is that these methods render the filenames in pre-sulfnbk.exe format, where longfilename.xxx becomes longfi~1.xxx (by chance I happen to have written something about this once: [**Sulfnbk Syndrome, Media Consumption, and the Dry Run that Wasn't**]("http://www.kuro5hin.org/story/2004/7/22/185750/629")). I think I can figure out a fix to this, or find a fix someone else has already figured, but I can't do it for a few days. For now I'm posting this reply, and cross-posting it to the thread I started, so that others can take advantage of the hack and maybe figure it all out without me doing any work. In any event I will post a thorough writeup once I have time, probably Thursday.

 - Isaac

---

