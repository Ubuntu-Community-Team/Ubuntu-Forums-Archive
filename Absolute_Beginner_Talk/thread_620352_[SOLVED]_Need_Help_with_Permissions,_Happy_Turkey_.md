---
title: "[SOLVED] Need Help with Permissions, Happy Turkey Day"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by uboodumdum on 2007-11-22
Happy Thansgiving All!

Trying to drop my bookmarks into my FireFox files, as directed in a previous thread I typed in the following command

*code:*
**sudo chown -R $USER ~/.mozilla**

I also tried substituting my actual user name for $USER

I got this error message:
*chown: missing operand after `jck8~.mozilla*

Can anbody tell me what I'm doing wrong?

regards all

---

### Post by dward526 on 2007-11-22
> **uboodumdum said:**
> Happy Thansgiving All!

Trying to drop my bookmarks into my FireFox files, as directed in a previous thread I typed in the following command

*code:*
**sudo chown -R $USER ~/.mozilla**

I also tried substituting my actual user name for $USER

I got this error message:
*chown: missing operand after `jck8~.mozilla*

Can anbody tell me what I'm doing wrong?

regards all

Try chmod instead of chown...if you cant change owner, change the permissions.:)

---

### Post by uboodumdum on 2007-11-22
Need Help with Permissions, Happy Turkey Day 

--------------------------------------------------------------------------------

Happy Thansgiving All!

Trying to drop my bookmarks into my FireFox files, as directed in a previous thread I typed in the following command

code:
sudo chown -R $USER ~/.mozilla

I also tried substituting my actual user name for $USER

I got this error message:
chown: missing operand after `jck8~.mozilla

Can anbody tell me what I'm doing wrong?

regards all
__________________

---

### Post by Paul820 on 2007-11-22
In firefox, go to Bookmarks->Organise Bookmarks, then when the other window opens click on File->Import and browse to your bookmarks file.

EDIT: Why did you start another thread for the same subject when you could have carried on using the other one?

---

### Post by uboodumdum on 2007-11-22
**sudo chmod -R $USER ~/.mozilla**

Yes?




regards

---

### Post by bodhi.zazen on 2007-11-22
with chown you need user.group

so 

```
sudo chown user.user ~./mozilla
```

---

### Post by Arthur Archnix on 2007-11-22
You are already the owner of all files in ~/ and below, there shouldn' be a need to change anything. If you have bookmarks you want to put in there and you can't seem to do it, for whatever strange permission issue, just use sudo cp to copy the files you need in there.

It would be something like:
```
sudo cp /sourcedirectory/bookmak_files /destinationdirectory/
```

---

### Post by uboodumdum on 2007-11-22
Thanks but the bookmarks.html file is on another hard drive.  I need the permissions, owner, whatever to work for mozilla anyways

regards

---

### Post by uboodumdum on 2007-11-22
It will not let me drop or replace any files in mozilla even though I am the owner!  Yeah I can fix the bookmarks but I want control of the file if possible.  I'm getting lots of different opinions here!

---

### Post by Arthur Archnix on 2007-11-22
Posting the commands you have used and the error messages you receive will help to simplify the advice you receive.

---

### Post by bodhi.zazen on 2007-11-22
Well, what file system ?

Permissions / ownership is different on FAT / NTFS.

You need to set them at the time of mount :

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by uboodumdum on 2007-11-22
1st thread in this Post!
regards

---

### Post by uboodumdum on 2007-11-22
I just loaded it yesterday, i gues I'll just do the bookmarks by hand.  I did use NTFS not FAT, but you lost me completely.  

Firefox was in the installation, i didn't download it.  When i download a program that was nort originally included in the install, I won't have this problem, right?
regards

---

### Post by Arthur Archnix on 2007-11-22
You didn't say whether you'd tried to copy the files as i suggested, and if so what commands you used, and what (if any) errors you got.

This, suggests to me that you're trying something, but what you're describing doesn't look anything like what those commands in your first post will do. 
> "It will not let me drop or replace any files in mozilla even though I am the owner! Yeah I can fix the bookmarks but I want control of the file if possible. I'm getting lots of different opinions here!"

Why don't you give the full path of the bookmarks you want to copy. Then I'll give you the commands to copy those bookmarks to a folder on your desktop, change the ownership of that folder, at which point you should just be able to use firefox to import the bookmarks. That's probably the safest way to proceed anyway.

---

### Post by overdrank on 2007-11-22
> **Arthur Archnix said:**
> You didn't say whether you'd tried to copy the files as i suggested, and if so what commands you used, and what (if any) errors you got.

This, suggests to me that you're trying something, but what you're describing doesn't look anything like what those commands in your first post will do. 


Why don't you give the full path of the bookmarks you want to copy. Then I'll give you the commands to copy those bookmarks to a folder on your desktop, change the ownership of that folder, at which point you should just be able to use firefox to import the bookmarks. That's probably the safest way to proceed anyway.

Arthur Archnix   [http://ubuntuforums.org/showthread.php?t=620360](http://ubuntuforums.org/showthread.php?t=620360)

---

### Post by uboodumdum on 2007-11-22
The BM file is on my external HD, I can make a folder and drop it on my desktop, I think anyways!

regards

---

### Post by Arthur Archnix on 2007-11-22
> **overdrank said:**
> Arthur Archnix   [http://ubuntuforums.org/showthread.php?t=620360](http://ubuntuforums.org/showthread.php?t=620360)

This is cross posted? Looks like Bodhi is on it.

---

### Post by bodhi.zazen on 2007-11-22
> **uboodumdum said:**
> I just loaded it yesterday, i gues I'll just do the bookmarks by hand.  I did use NTFS not FAT, but you lost me completely.  

Firefox was in the installation, i didn't download it.  When i download a program that was nort originally included in the install, I won't have this problem, right?
regards

What problem ?

The problem you have I think is with NTFS. NTFS does not support permissions. See the links I gave you, the psychocats and ntfs-3g in particular. If you want the technical details, read the one on FSTAB.

Your permissions problems in not related to where you download an application from, although best to stay with the Ubuntu repositories if at all possible.

---

### Post by uboodumdum on 2007-11-22
> **Arthur Archnix said:**
> This is cross posted? Looks like Bodhi is on it.

Yeah, I got in trouble for that, sorry.

---

### Post by philinux on 2007-11-22
Why the need to change owner .mozilla is in your home directory so you are the owner.

All you need to do is copy the bookmarks file over from wherever it is now into the .mozilla/firefox/xxxxx.defaults directory

---

### Post by bodhi.zazen on 2007-11-22
Threads merged.

FYI I think the problem is he is trying to change the perrmissions of a directory on a NTFS partition and if so he needs ntfs-3g ie ntfs-config, although I am not certain...

---

### Post by uboodumdum on 2007-11-22
> **philinux said:**
> Why the need to change owner .mozilla is in your home directory so you are the owner.

All you need to do is copy the bookmarks file over from wherever it is now into the .mozilla/firefox/xxxxx.defaults directory

Well that's the crux of the bisquit, Ubuntu won't let me replace the bookmarks.html file in FireFox.  

regards

---

### Post by Arthur Archnix on 2007-11-22
uboom, at this point I don't think anyone even really understands what you're trying to do. At this rate you'll never get this problem solved. Please, take a few minutes and try and be very clear about what you're doing and what problem you're having.

For example, I have one computer with Ubuntu installed, and I want to import my Firefox bookmarks from another computer onto this one. How can I do this? OR, I have one computer that dual boots between windows and ubuntu. I want to import my bookmarks from windows to my ubuntu firefox. OR. I have one computer that dualboots windows and ubuntu, and I want them to share all their settings, bookmarks, etc.

---

### Post by uboodumdum on 2007-11-22
Ok Archie

The facts is I have two hard drives in my PC, so not a dual boot.  I just loaded FeistyF with it's version of FFox.  I have 4 bookmarks in it now, I can put all in the same way, slowly!  I tried to install GG and import, it brought in the **wrong** bookmark.html from FireFox.  One from the backup bookmarks folder.  I was having other problems, possibly I had a bad disk I burned so I installed FF over it but without importing.  I have copied the correct bookmark file on my external harddrive, I was thinking by dropping it into the firefox folder and replacing the bookmarks.html file I could save time.  WRONG!

The bookmarks are really no biggie and i have already used up enough time that i could have put in 100 bookmark pages by now!  But i would like to know how to have permissions, ownership, whatever it is for all my files

regards

---

### Post by Arthur Archnix on 2007-11-22
Ok, so if you've already got the file you want, say it's called "bookmarks.html" and you have it on your desktop, which in ubuntu is located at ~/Desktop/

Depending on how you copied this file to your desktop and such you might not be its owner, so you want to use chown. In a terminal type:
```
sudo chown user:user ~/Desktop/bookmarks.html
```
You'll have to change user to your user name. Lets say it's tom. Then it would be:
```
sudo chown tom:tom
```

Then you'll have to replace the existing bookmarks file, with the one you just changed. You can use nautilus for this, and drag the file from your desktop to your firefox bookmarks folder. If sometime pops up on the screen saying you can't do this, post back and type out what the error was.

---

### Post by uboodumdum on 2007-11-22
> **Arthur Archnix said:**
> Ok, so if you've already got the file you want, say it's called "bookmarks.html" and you have it on your desktop, which in ubuntu is located at ~/Desktop/

Depending on how you copied this file to your desktop and such you might not be its owner, so you want to use chown. In a terminal type:
```
sudo chown user:user ~/Desktop/bookmarks.html
```
You'll have to change user to your user name. Lets say it's tom. Then it would be:
```
sudo chown tom:tom
```

Then you'll have to replace the existing bookmarks file, with the one you just changed. You can use nautilus for this, and drag the file from your desktop to your firefox bookmarks folder. If sometime pops up on the screen saying you can't do this, post back and type out what the error was.

Thanks.  I was able to import right from the Organize BookMarks ,  I didn't think of importing from the external drive for some reason, too used to dropping and dragging I guess!
PROBLEM SOLVED!

Now if I can get my password manager KeePass set up I'm good to go! 

My next dum dum question which won't make sense I'm sure!  I download my program and manage to get it installed.  Will I be able to move, replace, delete my files like i do XP?  Or will I have ownership, permissions problems?   

regards

---

