---
title: "Error Installing .deb file, need assistance/advice"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by ubuntuforums on 2007-08-09
I get this error when I try to install this specific nero .deb file.

[http://img166.imageshack.us/img166/1192/debinstallerroror8.jpg](http://img166.imageshack.us/img166/1192/debinstallerroror8.jpg)

I am NOT running any other management tool (even tried restarting pc and installing right after login, same problem).  I have installed .deb files previously no problem, it's something with this particular .deb file.  I converted it from an rpm to a deb with alien, no problems.  So is there something special I have to do, or should I re-download the rpm and convert it again (already tried converting the rpm different ways, same problem.).

What am I missing here?  Is the deb just corrupted or something of that sort?

The icon has a lock in the corner, don't know what that means:
[http://img54.imageshack.us/img54/5706/deblockpp5.jpg](http://img54.imageshack.us/img54/5706/deblockpp5.jpg)

---

### Post by satkata on 2007-08-09
Well, it means just what it says in the pop-up.

You have probably parallel started synaptic? opened another package with gdeb? or on the command-line apt-get or dpkg.

So, you should first close/ wait to finish the package management applications, that is already running and then try to install that deb package.

BTW, the final version of nero 3 is already realesed, why do want to install that Beta package?

-----

sorry, didn't read till the end :)

The could be something with the package itself. Try installing the released version.

The icon means, that your user has no write-rights for the package, but that's not the problem as you're gaining root rights to install.

---

### Post by ubuntuforums on 2007-08-09
Seems I'm dumb.  Since the previous deb packages worked, I assumed it had to be a problem with that particular package.  So I did as you suggested, I downloaded the latest release of Nero and of course I got the same problem.  So now I know that its probably all deb packages, so here is a list of my running processes:
[http://img375.imageshack.us/img375/4043/runningprocessespv3.jpg](http://img375.imageshack.us/img375/4043/runningprocessespv3.jpg)

What do I have to close to get deb packages working?   Also how come when I restart my computer and login to Ubuntu, then try to install the deb, I still get the same error?  How can I fix this?

Any help would be great.  Thanks.

---

### Post by splintercellguy on 2007-08-09
ps -A | grep synaptic, then if there's an entry, sudo killall synaptic.

---

### Post by aysiu on 2007-08-09
Have you tried pasting this command into the terminal?: ```
sudo apt-get update && sudo apt-get install k3b
```

---

### Post by splintercellguy on 2007-08-09
Or, just do sudo dpkg -i nerolinux* in the directory where the deb is located.

---

### Post by ubuntuforums on 2007-08-09
Thanks for the quick response guys.

Weird, ran "sudo apt-get update" this morning, all uptodate.  Ran it now and told me
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```
So I did what it said, and voila, deb packages are working again.  Thanks a lot.

Great support here.  :)

edit: my guess is that my first attempt to install my nero deb messed up somehow, freezing and staying in memory... causing my problem,,, all is fix now though, super happy.

---

### Post by por100pre1 on 2007-08-09
> **ubuntuforums said:**
> Seems I'm dumb.  Since the previous deb packages worked, I assumed it had to be a problem with that particular package.  So I did as you suggested, I downloaded the latest release of Nero and of course I got the same problem.  So now I know that its probably all deb packages, so here is a list of my running processes:
[http://img375.imageshack.us/img375/4043/runningprocessespv3.jpg](http://img375.imageshack.us/img375/4043/runningprocessespv3.jpg)

What do I have to close to get deb packages working?   Also how come when I restart my computer and login to Ubuntu, then try to install the deb, I still get the same error?  How can I fix this?

Any help would be great.  Thanks.

I think Nero for Linux is waste of money. k3b does the job well and has a nice GUI. Give it a try first!

---

### Post by ubuntuforums on 2007-08-09
lawl, everything on the internet is free.  Where are you from?

---

