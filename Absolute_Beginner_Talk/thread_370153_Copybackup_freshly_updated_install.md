---
title: "Copy/backup freshly updated install"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by mikeescott on 2007-02-25
Is there a wy to copy or backup all the files or a freshly updated new install from Windoze or live cd? I would like to be able to copy everything back to its original location with the updates and installed packages, etc.. if I have to reinstall again. I just spent 4 days updating a new intsall and I do not want to do that again (3rd time now) I tried to backup using Nero in Windoze and it could not read a lot of the files. I tried to copy and paste in Windoze and it could not access a lot of the files. I tried to copy and paste using the live cd and it could not copy a lot of the files.

---

### Post by houstonbofh on 2007-02-25
> I tried to copy and paste using the live cd and it could not copy a lot of the files.
What files?  Keep in mind that a lot of things in the file system are not really files.  The /dev directory comes to mind...

That said, you can tar.gz the root filesystem.  You can also copy the apt cache to a USB drive, or a CD.  (Search for some instructions on how to add this to a repository)  You would still have to reinstall, but the upgrades would be local.

---

### Post by mikeescott on 2007-02-25
How do I tar.gz?

---

### Post by rusty4r on 2007-02-25
Obviously you can't create a backup while you are in the system you want to backup, and Windoz can't do it either as you have already found out. But if i'm not mistaken there is a live cd that can do this for you. I'll see if I can find it and get back to you.

---

### Post by rusty4r on 2007-02-25
OK I think I found it its called partimage. Check out this link
[http://www.ubuntuforums.org/showthread.php?t=367981&highlight=backup]("http://www.ubuntuforums.org/showthread.php?t=367981&highlight=backup")

Hope this helps you

---

### Post by houstonbofh on 2007-02-26
> **mikeescott said:**
> How do I tar.gz?
What a fantastic opprotunity to tech people how to answer there own questions!
If you took "tar.gz" to google, you would get a lot of unhelpfull stuff.  However, if you were to google "howto tar.gz" you still get some unhelpfull stuff, but the first answer is [http://www.fluidthoughts.com/howto/tar-gzip/](http://www.fluidthoughts.com/howto/tar-gzip/) which fully answers you question , and is very helpfull.  I even bookmarked it to give to lots of others later.

Now I am not doing this to be mean...  Just that often you can find an answer yourself faster than waiting for someone else to answer your question.  Also, if you have researched, your questions can become more "interesting" to the "great old ones" that come here. :)

---

### Post by dannyboy79 on 2007-02-26
you can install sbackup for directory and file backup or you could use the links in my signature for partition level backup which maybe is what you want to be sure you capture it all. but there are also plenty of guides within this forum for backing up your system. good luck

---

### Post by Duck2006 on 2007-02-26
[http://www.linuxquestions.org/questions/showthread.php?t=362506](http://www.linuxquestions.org/questions/showthread.php?t=362506)

These may help with backing up your system

---

