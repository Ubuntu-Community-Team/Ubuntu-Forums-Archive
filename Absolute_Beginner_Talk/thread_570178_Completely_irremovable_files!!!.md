---
title: "Completely irremovable files!!!"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-07
Does anyone know what I'm talking about?  Usually in Linux, root is all powerful, but sadly there's somethings even *it* can't do!

Well, somehow I've managed to create some of these, and it's really annoying!  There seems to be absolutely no way to remove them!  The files look like this: The normal icon and name, but it has a "read-only" sign, a "no access/unreadable" sign, and a shortcut sign.  Does anyone know how to get rid of them!?! :mad:

---

### Post by SpiritIsReality on 2007-10-07
howdy
interesting , sounds like those mysterious automatic update cookies in micsoft.
could you please give us a screenshot of one. and so we know, 
could you run an ls -la so we can have a look at the permissions?
and the result of an attempted 
sudo chmod a +rwx <filename> or whatever it takes?
buds

---

### Post by LaRoza on 2007-10-07
I don't know exactly what you did, but it can be removed. The easiest (and most dangerous) method is too use a live cd.

You can use "gksudo nautilus", to use a GUI (be very careful) and check permissions and attributes.

---

### Post by ryanVickers on 2007-10-07
**To first response:**
Permissions (on the one in the screenshot):
```

lrwxrwxrwx 1 root root    41 2007-09-15 09:17 FlashPlayer8 -> /home/ryan/system/scripts/runFlashPlayer8

```
Note: I doubt if it matters, but "/home/ryan/system/scripts/runFlashPlayer8" does not exist anymore...
This one happens to be a (shortcut to a) simple script to open flash player in wine... ;)

Well, they are actually all shortcut, according to the icons, but I don't believe that for some of them...
[B]
To second response:
[/B]I don't know why they happened either! :p

Don't worry - I know what I'm doing ;) (unless using a live CD makes it more risky :p)I might try that if nothing else works - but how does the live cd root have more permission than "*my"* root exactly? ;)

---

### Post by skipb on 2007-10-07
I agree with the Live CD method. I ran into a similar problem a while back and was able to zap the file using a Live CD.

---

### Post by SpiritIsReality on 2007-10-07
is this something to do with can't remove a file until the links to it are all removed first? > 
The Linux file system makes it possible for a file to have more than one name or directory entry. The **ln** command allows you to create these additional names or links. If these links are *hard links*, links created with the **ln** command without the **-s** option, you have a file that can be accessed by these multiple names.
 By using the **rm** command on one of these names, you only delete the name, not the actual file. When the last name pointing to the file is removed, the file is finally removed. from here 

[http://www.linuxjournal.com/article/50](http://www.linuxjournal.com/article/50)

---

### Post by LaRoza on 2007-10-07
> **ryanVickers said:**
> 
To second response:
[/B]I don't know why they happened either! :p

Don't worry - I know what I'm doing ;) (unless using a live CD makes it more risky :p)I might try that if nothing else works - but how does the live cd root have more permission than "*my"* root exactly? ;)

Just be careful what you delete when using the live cd, or root permissions. The live cd isn't restricted by the OS. The Operating system enforces the read/write to the disk. When it is not running, he disk might as well be FAT32, unless it is encrypted.

---

### Post by ryanVickers on 2007-10-08
Oh, that's good then - I'll do it!

---

### Post by dwhitney67 on 2007-10-08
What are you trying to remove?

[FONT="Courier New"]lrwxrwxrwx 1 root root    41 2007-09-15 09:17 FlashPlayer8 -> /home/ryan/system/scripts/runFlashPlayer8[/FONT]

To remove the link:

$ sudo rm -f FlashPlayer8

To remove the actual file (or is it a directory?):

$ sudo rm -rf /home/ryan/system/scripts/runFlashPlayer8

Note the "-r" is included in case it is a directory.

It is plausible to have a dangling link that points to nothing.


> Does anyone know what I'm talking about? Usually in Linux, root is all powerful, but sadly there's somethings even it can't do!
A myth.  The root user can do anything, to a file, directory, link, etc.  Operators on the other hand, do have their shortcomings.

---

### Post by ryanVickers on 2007-10-08
> 
It is plausible to have a dangling link that points to nothing.

Well, yeah, that's what it is! :p

I think I'll just do the live CD thing when I get the chance!

---

### Post by dwhitney67 on 2007-10-08
I'm still at a loss to understand what it is that you are trying to remove.  You also failed to provide evidence of the steps you took to delete whatever it is you are trying to delete.

I've been using Unix/Linux almost exclusively since 1988.  Any file, directory, and link can be deleted by the root-user of the system.

---

### Post by bodhi.zazen on 2007-10-08
LOL

No, there are ways of locking files such that even the almighty root can not change them.

Let us know how the live CD goes ...

To remove a link, consider using unlink

```
unlink <path-to_link>
```

---

### Post by ryanVickers on 2007-10-08
> **dwhitney67 said:**
> I'm still at a loss to understand what it is that you are trying to remove.  You also failed to provide evidence of the steps you took to delete whatever it is you are trying to delete.

I've been using Unix/Linux almost exclusively since 1988.  Any file, directory, and link can be deleted by the root-user of the system.

I am trying to remove shortcuts that are somehow unable to be deleted by my method of deleting them using root. ;)

---

### Post by ryanVickers on 2007-10-08
:-k
> **fmat said:**
> and god said let them be entertained. and it was so. lol
this is good ... thanx

---

### Post by dwhitney67 on 2007-10-08
> **bodhi.zazen said:**
> LOL

No, there are ways of locking files such that even the almighty root can not change them.

Let us know how the live CD goes ...

To remove a link, consider using unlink

```
unlink <path-to_link>
```

Please show me how to create one of these "locking files".

---

### Post by bodhi.zazen on 2007-10-08
> **dwhitney67 said:**
> Please show me how to create one of these "locking files".

```
sudo chattr +i <file>
```

where <file> is the path to a file

even root can not change the file

To undo this :

```
sudo chattr -i <file>
```

Have fun ...

---

### Post by dwhitney67 on 2007-10-08
> **bodhi.zazen said:**
> ```
sudo chattr +i <file>
```

where <file> is the path to a file

even root can not change the file

To undo this :

```
sudo chattr -i <file>
```

Have fun ...

Thanks for the insight.

However I'm not quite sure I understand why one must boot from the LiveCD in order to remove a file?  It seems like you have provided the information on how to work around the "hidden" attribute setting of the the file.

---

### Post by macogw on 2007-10-08
> **dwhitney67 said:**
> 
A myth.  The root user can do anything, to a file, directory, link, etc.  Operators on the other hand, do have their shortcomings.

Except in cases where the file has been chattr'd +i and the root user doesn't know about chattr.  But that's PEBKAC, when you get down to it.  Root itself can still chattr.

---

### Post by bumanie on 2007-10-08
I had a problem with files that became stuck on my desktop. They had padlock symbols on them and would not remove by any regular method. Fixed the problem by typing 'gksudo nautilus' into terminal. Was then able to go to the desktop folder in my home folder and send the files to garbage bin. From there they removed without a problem. Hope this helps, but be careful when using gksudo, it is the graphical form of sudo and anything you delete will be gone (I think. I am no expert on this).

---

### Post by SpiritIsReality on 2007-10-08
> **bumanie said:**
> I had a problem with files that became stuck on my desktop. They had padlock symbols on them and would not remove by any regular method. Fixed the problem by typing 'gksudo nautilus' into terminal. Was then able to go to the desktop folder in my home folder and send the files to garbage bin. From there they removed without a problem. Hope this helps, but be careful when using gksudo, it is the graphical form of sudo and anything you delete will be gone (I think. I am no expert on this).
thanks for the gksudo nautilus

---

### Post by bodhi.zazen on 2007-10-08
> **dwhitney67 said:**
> Thanks for the insight.

However I'm not quite sure I understand why one must boot from the LiveCD in order to remove a file?  It seems like you have provided the information on how to work around the "hidden" attribute setting of the the file.

Well, I was answering the question you asked :

> **dwhitney67 said:**
> Please show me how to create one of these "locking files".

It was not my idea to try to delete the file from a live CD, 

> **ryanVickers said:**
> Well, yeah, that's what it is! :p

I think I'll just do the live CD thing when I get the chance!

It is hard for me to advise the OP as I do not have insight to the original problem as of yet.

/bodhi awaits further information

---

