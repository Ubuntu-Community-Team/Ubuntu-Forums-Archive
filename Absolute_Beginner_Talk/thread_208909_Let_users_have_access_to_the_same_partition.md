---
title: "Let users have access to the same partition"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Thiesen on 2006-07-04
I suppose most of you guys know how Windows treats partitions. And I suppose some of you know how the world of Linux do the same. If not:

Windows:
C:
D:
E:
and so fourth

Linux:
/
/bin
/etc
/home
/home/some_account
and so fourth

That's not too hard to get the hang of. I just wanted to give you an example of what I mean.

My real question is that in Linux you can mount any partition anywhere under /. I did exactly that as an experiment and ofcourse I made it. I mounted one partition on a second harddrive as /home/my_account/stuff and gave myself ownership of that partition. This means that only I have ownership of it. What I would like to do is to let every user on my computer (not that there are other users on my computer) get read/write access to that partition (not necessarily write access).

For example, let's say that I have two users (Billy and Joe) on my computer. They both have their own /home on the same physical partition. I intend to let them both have access to a partition with all kinds of emulators on it (let's say they both like emulators alot) so they can play NES and MAME. If I now mount this particular partition as /home/billy/emulators only Billy would be able to access the games and not Joe.

What would I have to do to let them play those games on that partition?

I used that Drives configuration(I think it's called that... I have a Swedish locale so I don't know what it's called in English) under the System menu in Gnome to mount my first partition so it would be nice if it could be done as easy as it was the first time.

---

### Post by ProjectGod on 2006-07-04
you'll have to give the mounted partition all permissions for all users... that is you'll have to set permissions on the newly created directory (mount point)... i'm not 100% sure... 

you can use the chmod command

something like **sudo chmod -R 777 /media/windowsdriveD**

etc
etc

hope that helps!

---

### Post by Thiesen on 2006-07-04
[QUOTE=ProjectGod]you'll have to give the mounted partition all permissions for all users... that is you'll have to set permissions on the newly created directory (mount point)... i'm not 100% sure... 

you can use the chmod command

something like **sudo chmod -R 777 /media/windowsdriveD**

etc
etc

hope that helps![/QUOTE]

Wow... that was a really quick answer and a pretty good one too... I know what you're telling me and that might actually work ofcourse... but I wonder if it's smart of me mounting the partitions in the /home/some_user/some_partition directory or maybe mount it in /some_directory directly under / ?

---

### Post by ProjectGod on 2006-07-04
ahh... that might be part of the initial problem... you see your home directory has very restrictive access permissions to begin with... so its better to create a new partition straight under root or use the existing /media directory...

:D

---

### Post by Thiesen on 2006-07-04
[QUOTE=ProjectGod]ahh... that might be part of the initial problem... you see your home directory has very restrictive access permissions to begin with... so its better to create a new partition straight under root or use the existing /media directory...

:D[/QUOTE]

Hmmm... the /media directory... interesting... what could that be used for?

---

### Post by muep on 2006-07-04
/media has subdirectories where many non-essential filesystems are mounted. For example, Windows partitions and usb drives are usually mounted there.

Making /media/emulators would be a consistent way to solve your example.

---

### Post by Thiesen on 2006-07-04
[QUOTE=muep]/media has subdirectories where many non-essential filesystems are mounted. For example, Windows partitions and usb drives are usually mounted there.

Making /media/emulators would be a consistent way to solve your example.[/QUOTE]

would that also make the partition accessible to other users as well? If that's the case then I would be glad... :-)

---

### Post by aysiu on 2006-07-04
Even if you chmod it all to be 777, every newly created file will be 644 after that... unless you chmod them all again every time.

What you need is [this](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9).

---

### Post by Thiesen on 2006-07-04
[QUOTE=aysiu]Even if you chmod it all to be 777, every newly created file will be 644 after that... unless you chmod them all again every time.

What you need is [this](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9).[/QUOTE]

That link gave me an idea of what can be done, thanks ýou.

interesting ideas and ways of looking at things. Thank you all.

---

