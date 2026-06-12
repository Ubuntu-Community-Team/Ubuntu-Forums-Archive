---
title: "Auto-mount OS X (hfsplus) Partition"
date: 2007-04-04
forum: Apple Intel Users
---

### Post by davidsiegel on 2007-04-04
In the Feisty beta, when I mount my hfsplus partition /dev/sda2 it shows up as a volume on my Desktop - this behavior is so great! But how do I make this automatically occur every time I boot? I added a script to my session, but since it uses gksudo to execute as root I have to type my password every time I log in, even if the partition is already mounted from a previous session. I think I have to add a line to /etc/fstab, but I tried:

/etc/fstab:
```

/dev/sda2    /mnt/mac    hfsplus user,r    0    0

```

This didn't have any effect. What do I need to do to make this work?

---

### Post by cyberdork33 on 2007-04-05
That looks almost identical to mine, that works fine! did you create the mac folder first? I think the r needs to be 'rw' or 'ro'

Here's mine:

```
/dev/sda2       /home/cyberdork33/OSX           hfsplus user,rw 0 0
```

---

### Post by davidsiegel on 2007-04-05
I see - I left off the 'w' thinking 'r' would be read-only. I will try 'ro' - thank you!

---

### Post by davidsiegel on 2007-04-05
```
/dev/sda2    /mnt/mac    hfsplus user,ro    0    0
```

Results in the partition automounting to /mnt/mac, but now the volume does not show up in Nautilus/on the Desktop. Any ideas?

---

### Post by cyberdork33 on 2007-04-05
Mine wouldn't show up that way either... I don't know why. I have a Samba partition mounted just below it in my fstab and it DOES show... You can always just make a link to the folder on your desktop if that is what you are after.

---

### Post by darkmaster on 2007-04-05
Hi cyber (you're helping me a lot these days!!), I used your mount line in fstab and now Macintosh HD gets auto mounted at startup but... I cannot access some folders inside of it, Ubuntu answers me I have no permission to do it. As root, I can access those folders, but I need at least to be able to read 'em as a normal user, 'cause I have all my music in there. I cannot even enter into my Music dir in the Mac HD! Any help?

---

### Post by cyberdork33 on 2007-04-05
The OSX filesystem stores permissions the same way as in linux. The problem is that you are a separate user from the user under OSX, and thus do not have permission to view the OSX user's files, just as one user could not view the files of another user on ubuntu. This can be fixed by making both users have the same UserID (UID) in both systems. Check this thread on instructions:

[http://ubuntuforums.org/showthread.php?t=396125](http://ubuntuforums.org/showthread.php?t=396125)

PS... On getting the Drive to show on the desktop, I think it shows for my samba mount because I am specifying uid and gid for my username. These are special options dependent on the filesystem, but I think that HFS supports them as well. Using your above line, try:

```
/dev/sda2    /mnt/mac    hfsplus user,ro,uid=username,gid=username    0    0
```

EDIT: Adding the above does not work.

---

### Post by darkmaster on 2007-04-05
> **cyberdork33 said:**
> The OSX filesystem stores permissions the same way as in linux. The problem is that you are a separate user from the user under OSX, and thus do not have permission to view the OSX user's files, just as one user could not view the files of another user on ubuntu. This can be fixed by making both users have the same UserID (UID) in both systems. Check this thread on instructions:

[http://ubuntuforums.org/showthread.php?t=396125](http://ubuntuforums.org/showthread.php?t=396125)

PS... On getting the Drive to show on the desktop, I think it shows for my samba mount because I am specifying uid and gid for my username. These are special options dependent on the filesystem, but I think that HFS supports them as well. Using your above line, try:

```
/dev/sda2    /mnt/mac    hfsplus user,ro,uid=username,gid=username    0    0
```

Dammiiiit! Very well, then, let's calm down. I changed my short name (username for OSX session) to the one I have in Ubuntu Feisty. I used a fantastic automated tool called changeshortname

[http://www.macupdate.com/info.php/id/16620](http://www.macupdate.com/info.php/id/16620)

It worked very well, now both Ubuntu and OSX has got the same username: darkmaster (No caps pressed, everything as you can see here)

Even in this way, if I try to access the Mac HD, I cannot enter into the Music folder!! Nor many other folders into the folder darkmaster (Of the Mac HD). Why? Any clue? What did I do wrong?

---

### Post by davidsiegel on 2007-04-05
Here's what I did to make this work. First, in OS X, I changed my user id through Netinfo Manager to match my user id in Ubuntu. Then in Terminal in OS X:

```

sudo chown -R dave /Users/dave
sudo chgrp -R dave /Users/dave

```

(Use your own short user name instead of 'dave'!)

This updated the owner and group of all files in my home directory to reflect the change in my OS X user id. Once I booted into Ubuntu, all of the files in and below /Users/dave on my OS X partition were readable.

Some people have suggested that this is dangerous, but I didn't encounter any difficulties. You may experience some strange behavior before you run the commands above because the permissions are out of sync. If you encounter these problems, log out then back into OS X, run the commands above, then log out and back in again.

---

### Post by darkmaster on 2007-04-05
> **davidsiegel said:**
> Here's what I did to make this work. First, in OS X, I changed my user id through Netinfo Manager to match my user id in Ubuntu. Then in Terminal in OS X:

```

sudo chown -R dave /Users/dave
sudo chgrp -R dave /Users/dave

```

(Use your own short user name instead of 'dave'!)

This updated the owner and group of all files in my home directory to reflect the change in my OS X user id. Once I booted into Ubuntu, all of the files in and below /Users/dave on my OS X partition were readable.

Some people have suggested that this is dangerous, but I didn't encounter any difficulties. You may experience some strange behavior before you run the commands above because the permissions are out of sync. If you encounter these problems, log out then back into OS X, run the commands above, then log out and back in again.

Something has gone really wrong. I renamed my short name. I then used the Netinfo application. Before your answer, I rebooted and tryed to read the HD from Ubuntu with no success. I then entered in OSX again and all my user info disappeared. No background image (Standard one), no particular settings or dock icons... If I try to log out, I cannot do it. If I try to turn off the Mac, I cannot do it. I run Netinfo and try to change back things to what they where (Uid was 501) and when I try to log in with the password it tells me it is wrong (It isn't, I log in with that pass).

If I open a terminal and try to enter the command you suggested, I get an error. 
darkmaster is not in the sudoers list. This error will be reported.
What can I do to settle down things, man? The situation really looks bad bad bad....

---

### Post by darkmaster on 2007-04-05
I tryed to start OSX in Single User mode. Pratically, a terminal.
Giving the commands you suggested, using darkmaster, the unswer is:
unknown argument darkmaster
The old user id I found in the uid was 501, so, I tryed
chown -R 501 /Users/darkmaster
something looks like working but when I restart nothing changes. Every line of the looking like working commanda, I had the message: read only filesystem.
I dunno what to do....

---

### Post by davidsiegel on 2007-04-05
Step 1: Breathe.

Okay, some of the things that happened to you happened to me. On the other hand, I never ran any strange software to change my short user name, and I certainly didn't run any commands with root privileges which I did not understand - that is a very bad idea, don't do that again!

When I first changed my user id, my OS X session essentially locked up on me because I suddenly lost permissions to read everything - opening a terminal failed because of permissions just like in your case. I logged out, then back in, and just like in your case my desktop was gone, and so were my preferences. What happened is that OS X cannot read your preference files in ~/Library since you don't own them, so it reverts to defaults. I tried opening a terminal and that time it worked, so I did the chown/chgrp commands, logged out and back in, and everything was back to normal with my new uid in place and all of my files belonging to me again. If this does not work for you, you can try single-user booting and running the same commands I already posted (without the sudo), or you can try changing your uid back.

---

### Post by davidsiegel on 2007-04-05
So, assuming your short username is darkmaster and your home folder is /Users/darkmaster, the commands you should run with sudo or as root in single-user mode are:

```

chown -R darkmaster /Users/darkmaster
chgrp -R darkmaster /Users/darkmaster

```

---

### Post by darkmaster on 2007-04-06
> **davidsiegel said:**
> Step 1: Breathe.

Done. Wow! Until now, works :)

> **davidsiegel said:**
> Okay, some of the things that happened to you happened to me. On the other hand, I never ran any strange software to change my short user name, and I certainly didn't run any commands with root privileges which I did not understand - that is a very bad idea, don't do that again!

I would be glad to tell you it was the fault of my incoscienze using strange scripts but it is not :( The script worked like a charm, changed my shortname and I had no conflict even after restarting. I really recommend it if you need to change the short name. It was useless, yes, I misunderstood the problem. It was not the shortname to be changed but, hey, the script did nothing wrong. Let's give to Cesar what belongs to Cesar.

> **davidsiegel said:**
> When I first changed my user id, my OS X session essentially locked up on me because I suddenly lost permissions to read everything - opening a terminal failed because of permissions just like in your case. I logged out, then back in, and just like in your case my desktop was gone, and so were my preferences. What happened is that OS X cannot read your preference files........ 

Ok, now, this is different. If I log in, I'm not admin. I can't do anything an Admin would do. I cannot give sudo commands since my password does not belong to a super user anymore. I cannot change preferences in Netinfo, I cannot unlock the changes... Because I'm not a Super User anymore. And, look at that, I cannot even log out!!! Yes, I cannot log out neither turn the mac off. I have to use the manual button!!! Incredible. Looks kinda different from your case...

> **davidsiegel said:**
> I tried opening a terminal and that time it worked, so I did the chown/chgrp commands, logged out and back in, and everything was back to normal with my new uid in place and all of my files belonging to me again. If this does not work for you, you can try single-user booting and running the same commands I already posted (without the sudo), or you can try changing your uid back.

It does not work. But using the single user mode it does not work either! Incredible. I turned to Single User mode but nothing changed. I tryed the chown: as I sayd in the last post, error if I use the name darkmaster (Unknown argoment) and if I use a strange hybrid command (Read above the other post) it warns me about the fact that the HD is read only at evry single damned line. From single user mode, I tryed to start the graphic interface: the mac freezes. I try to create a new user, so that at least I can access OSX with an admin of some kind: nothing, the mac freezes at  the first command to create a folder.

Really, I dunno what to do, I dunno why this is different from your experience bu if something comes in your mind, please, feel free to help me :_(

btw: thanks aniway for trying to help me out, I appreciate it.

---

### Post by cyberdork33 on 2007-04-06
Locking the filesystem is common in Unix/Linux when there are problems. It would probably be beneficial to start in single user mode, and follow the directions to run a fsck:
[http://macs.about.com/od/osx/a/running_fsck.htm](http://macs.about.com/od/osx/a/running_fsck.htm)

It sounds like that script you used was not all that great at cleaning up after itself.

If that doesn't work there are some other things we can try. (Like creating a new user from the console.) Here is a tutorial on creating a full OSX user from the command line:
[http://www.macosxhints.com/article.php?story=20030603190314390](http://www.macosxhints.com/article.php?story=20030603190314390)

After that you should be able to login with that user, and change the permissions on your old files.

---

### Post by davidsiegel on 2007-04-06
Have you tried using that script to change your short username back? The unknown argument errors might be caused by some inconsistency in what OS X thinks your short username is.

---

### Post by darkmaster on 2007-04-06
> **cyberdork33 said:**
> Locking the filesystem is common in Unix/Linux when there are problems. It would probably be beneficial to start in single user mode, and follow the directions to run a fsck:
[http://macs.about.com/od/osx/a/running_fsck.htm](http://macs.about.com/od/osx/a/running_fsck.htm)

It sounds like that script you used was not all that great at cleaning up after itself.

If that doesn't work there are some other things we can try. (Like creating a new user from the console.) Here is a tutorial on creating a full OSX user from the command line:
[http://www.macosxhints.com/article.php?story=20030603190314390](http://www.macosxhints.com/article.php?story=20030603190314390)

After that you should be able to login with that user, and change the permissions on your old files.

As for the first solution, I'll try it now. Speacking about the second... I allready wrote in the last post that I tryed creating a new user from single user mode.... and I used the exact how to you posted.... I wrote in the other post that the system freezes the moment I give the command to create a new user folder, this one:

sudo niutil -create / /users/ftpuser

So this does not work.... because the HD cannot be accessed at all! Guess the first solution won't work either for the very same problem but I'll try.

---

### Post by cyberdork33 on 2007-04-06
As stated... the filesystem is locked because there are errors... you need to do the fsck to recover.

---

### Post by darkmaster on 2007-04-06
> **cyberdork33 said:**
> As stated... the filesystem is locked because there are errors... you need to do the fsck to recover.

Did it, no errors detected. All OK.

---

### Post by cyberdork33 on 2007-04-06
Single-User mode make the root partition mount as read-only. you have to mount it to make it writable. This is why it fails when creating the user directory.

```
/sbin/mount -uw /
```

From here:
[http://salingfamily.net/trav/osx/regain_admin.html](http://salingfamily.net/trav/osx/regain_admin.html)

---

