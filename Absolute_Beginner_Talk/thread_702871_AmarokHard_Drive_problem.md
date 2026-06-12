---
title: "Amarok/Hard Drive problem"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by lbarnes on 2008-02-20
hey guys, i've just started using ubuntu and am loving it, however
i'm having a problem keeping a library in amarok
before ubuntu, using windows only, i had a separate drive for all media - 300gb of stuff
i used itunes to control my massive library
i dual boot windows and ubuntu now - they're on the same drive 
i started using amarok because of the stated simularities to itunes
but i can't make amarok keep my files, though
everytime my pc restarts they're gone

i know it's a mounted volume, but i don't understand why windows can keep
all my files in itunes from a separate hard drive, but ubuntu cannot
i must be doing something wrong, because this cannot possibly be the case

sorry for the longwindedness
thanks guys

---

### Post by Origin415 on 2008-02-20
Amarok automatically scans and reloads its library, so it will see you music doesnt exist anymore and remove it -- try turning off that feature and see if that helps

---

### Post by lbarnes on 2008-02-20
wow, quick response

i'll try that - you're talking about "scan folders recursively" in Configure Amorok, right?

it'll be a while to see if it works, thank you

---

### Post by Iceni on 2008-02-20
You mention a "mounted volume" - does this mean you mount it manually after boot or does it automount via fstab? If you mount it manually it might be the problem.

---

### Post by AndyCooll on 2008-02-20
And in the Amarok settings is the drive ticked as one to watch?

:cool:

---

### Post by lbarnes on 2008-02-20
unchecking "scan folders recursively" did not fix it.  do i need to save playlist or something?
the drive is checked in configure collection

drive does not automount at startup - what's the code for it? drive name is DISC2_VOL1

why would i even have to mount a drive, or does windows do it automatically?

i guess i'm a complete noob, but i'm getting tired of adding 20,000 songs everytime i restart

thanks guys

---

### Post by lbarnes on 2008-02-22
is it hopeless guys?

---

### Post by AndyCooll on 2008-02-23
Well, assuming the drive is permanently attached, you need to do a search on these forums regarding mounting a second hard drive. Typically you'd edit /etc/fstab and add a line in that, something along the lines of:
```
/dev/sdb1 /mountpoint ext3 defaults 0 0
```
Where /dev/sdb1 is the partition on your second hard-drive that contains your music files, and /mountpoint is where you want to mount it.

Now every time you boot your pc that drive will be automatically mounted, and when you start Amarok it should remember the folder and not treat it as a completely new folder.

:cool:

---

### Post by MarkX on 2008-02-24
I'm having a similar problem,
 I can't see my 2nd (ntfs) data drive. It seems very silly that  hard drives aren't mounted automatically by default, After all, if it's in your computer you want to use it, you have physically mounted it for that purpose. What's the point in having to laboriously "mount" stuff via a console? Starting to get tired of these nonsensical laborious quirks for very basic essentials now.
Please, could someone explain how I can make my 2nd hard drive visible in the file menus?

---

### Post by forestpixie on 2008-02-24
if it's not mounting at boot then you need to edit fstab to add it, check this page out

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by MarkX on 2008-02-24
> **forestpixie said:**
> if it's not mounting at boot then you need to edit fstab to add it, check this page out

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Thanks for trying to help but the link doesn't show how to do it in 7.10 as the info in fstab is different and presumably needs a different entry to previous version.

---

### Post by AndyCooll on 2008-02-24
> **MarkX said:**
> Thanks for trying to help but the link doesn't show how to do it in 7.10 as the info in fstab is different and presumably needs a different entry to previous version.

Nope, the principles are the same (as pointed out in the note about two-thirds of the way down the page).

:cool:

---

### Post by lbarnes on 2008-02-29
i'm not sure what to do either, is editing fstab that complicated?
my drive name is DISK2_VOL1
could someone make a code for me to edit fstab with this?
i'm assuming you need the drive name to do it

here's what it says in the edit fstab in terminal:

[[IMG]http://img32.picoodle.com/img/img32/4/2/29/t_Screenshotm_6408d1c.png[/IMG]](http://www.picoodle.com/view.php?img=/4/2/29/f_Screenshotm_6408d1c.png&srv=img32)

---

### Post by AndyCooll on 2008-02-29
> **lbarnes said:**
> i'm not sure what to do either, is editing fstab that complicated?
my drive name is DISK2_VOL1
could someone make a code for me to edit fstab with this?
i'm assuming you need the drive name to do it

here's what it says in the edit fstab in terminal:

[[IMG]http://img32.picoodle.com/img/img32/4/2/29/t_Screenshotm_6408d1c.png[/IMG]](http://www.picoodle.com/view.php?img=/4/2/29/f_Screenshotm_6408d1c.png&srv=img32)

Editing /etc/fstab doesn't have to be complicated (and that link you were given pretty much tells you all you need to know).

From an "fstab" point of view your second drive isn't referred to as DISK2_VOL1, that's just a name given to it. It will be something like /dev/sdb1. You can check by copying and pasting into a terminal the following:
```
sudo fdisk -l
```
sda 1st hard disk, sdb 2nd hard disk, sdc 3rd hard disk (if you had one) etc etc, you get the idea. And the numbers are the partitions on each drive. Hence sdb1 is the first partition on the second drive. Make a note of it.
You then need to create a mount point with the following:
```
sudo mkdir /mnt/music
```
You can substitute that last bit with anything, it doesn't have to be called "music".
You then edit /etc/fstab with the following command:
```
sudo gedit /etc/fstab
```
Gedit is a text editor (a bit like notepad), but you could edit it in the command line if you're confident enough, replacing gedit with something like nano or even vi.
You simply add a line into /etc/fstab as I indicated in a previous post, e.g.:
```
/dev/sdb1 /mnt/music ntfs nls=utf8,umask=0222 0 0
```
Save the changes. Then:
```
sudo mount -a
```

Now when you go to Places > Computer, and then navigate through Filesystem > mnt, you should see your folder "music" and if you click on that you should see your music files loaded. And it should automatically be there every time you start up your pc.

You really should take another look at that link given to you earlier, it explains what I've written in more (and clearer) detail. 

What I've shown you is how to mount an ntfs drive as read only (which is the default in Linux, and is what is described in that link too). If you want to write to it, further steps need to be taken, details can be found here: [HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)]("http://ubuntuforums.org/showthread.php?t=217009")

:cool:

---

### Post by lbarnes on 2008-02-29
jesus christ
and that's for read only too?

would it be just better to install ubuntu on my media drive lol

---

### Post by lbarnes on 2008-02-29
i followed that link again
i don't know why but it automounts my windows c drive
i specifically was working with my other drive in the terminal
so my next question is how do i restore an fstab backup?

---

### Post by lbarnes on 2008-02-29
when i do this

sudo cp /etc/fstab.backup /etc/fstab

i get this

lennon@lennon-desktop:~$ sudo cp /etc/fstab.backup /etc/fstab
cp: cannot stat `/etc/fstab.backup': No such file or directory
lennon@lennon-desktop:~$ 

in the etc directory it will not let me save the backup over the fstab file
why do i not have permissions to do anything on my computer
i'm the only user on this thing

---

### Post by AndyCooll on 2008-02-29
> **lbarnes said:**
> when i do this

sudo cp /etc/fstab.backup /etc/fstab

i get this

lennon@lennon-desktop:~$ sudo cp /etc/fstab.backup /etc/fstab
cp: cannot stat `/etc/fstab.backup': No such file or directory
lennon@lennon-desktop:~$ 

in the etc directory it will not let me save the backup over the fstab file
why do i not have permissions to do anything on my computer
i'm the only user on this thing

That's because it should be the other way round:
sudo cp /etc/fstab /etc/fstab.backup
This command makes a backup of your original /etc/fstab

"No such file" is saying (what it says on the tin) that you do not have a file called /etc/fstab.backup to copy over the fstab file (i.e. the file /etc/fstab.backup currently does not exist!). It has nothing whatsoever to do with permissions.

In effect you mustn't have created the file /etc/fstab.backup. You can check by entering into a terminal:
```
ls -l /etc
```]
If fstab.backup is not in the list then either you didn't successfully create a backup or if you did it wasn't created in that directory.

:cool:

---

### Post by lbarnes on 2008-03-01
ok, got it fixed finally
and btw, your little guide worked perfectly for me
my media drive auto mounts now, and i just deleted the windows line in fstab

thank you so much for your patience
and i would recommend your guide over the other one

---

### Post by AndyCooll on 2008-03-01
> **lbarnes said:**
> jesus christ
and that's for read only too?

would it be just better to install ubuntu on my media drive lol

Nope. This is one of the problems with closed formats. The problem is that you're trying to access a drive that is ntfs formatted. Since Microsoft have never released the source code for the ntfs format, Linux developers have had to reverse engineer the ntfs format, and this has been tricky. We've been able to read ntfs formats for years, but traditionally writing to ntfs drives has been circumspect to say the least, it's only recently that this has become more reliable. 

Linux distros (usually) by default uses the ext3 file format.

:cool:

---

### Post by AndyCooll on 2008-03-01
> **lbarnes said:**
> ok, got it fixed finally
and btw, your little guide worked perfectly for me
my media drive auto mounts now, and i just deleted the windows line in fstab

thank you so much for your patience
and i would recommend your guide over the other one

You are welcome. A click on the star to the right of the post you found helpful (and giving it a "thanks") would be appreciated.

:cool:l

---

### Post by lbarnes on 2008-03-01
sure thing, i always wondered how one would give thanks on this board
so thanks for that post as well

i think my confusion was that it is just a storage drive
and never had on os on it, but i guess it was formatted ntfs to work with windows
yeah, it's getting clearer now - thanks for not getting frustrated

---

