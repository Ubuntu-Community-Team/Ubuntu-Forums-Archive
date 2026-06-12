---
title: "Keeping Linux clean?"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by yeahyeahyeah on 2005-11-30
So coming from a Windows world, I am concerned with Ubuntu getting "gunked up" over time. For instance, with Windows over time the registry gets cluttered, files are left behind with un-installs, etc.

I find I need to re-install Windows every year or so to keep it running well.

Will I need to worry about this with Linux? I know there is no "registry", but there are a lot of .conf files, log files, etc, etc. Does Linux keep itself pretty clean, or should I plan on re-installing every once in a while?

Thanks.

---

### Post by earobinson on 2005-11-30
in my expirence linux dose not have this problem like windows

---

### Post by matthew on 2005-11-30
[quote=yeahyeahyeah]So coming from a Windows world, I am concerned with Ubuntu getting "gunked up" over time. For instance, with Windows over time the registry gets cluttered, files are left behind with un-installs, etc.

I find I need to re-install Windows every year or so to keep it running well.

Will I need to worry about this with Linux? I know there is no "registry", but there are a lot of .conf files, log files, etc, etc. Does Linux keep itself pretty clean, or should I plan on re-installing every once in a while?

Thanks.[/quote] You don't need to worry about this with Linux. The idea with Debian (upon which Ubuntu is based) is "install once, upgrade regularly" which basically means you can install Linux and expect to not need to reinstall due to "gunking up" and the like.

---

### Post by Books on 2005-11-30
I'm new to Linux, too. What about defragging? Windows slows down if you don't defrag every few months or so, and running "chkdsk /f" in windows was supposed to be good to do as well.

Does Linux need to defrag?

Books

---

### Post by Rob2687 on 2005-11-30
Ext2 or 3 or some of the other filesystems are set up such that they don't need to be defragged.

---

### Post by Xian on 2005-11-30
[QUOTE=yeahyeahyeah]I know there is no "registry", but there are a lot of .conf files, log files, etc, etc. Does Linux keep itself pretty clean, or should I plan on re-installing every once in a while?[/QUOTE]

When you remove a package, if it did install a config file, that will not be removed completely unless you also purge the pkg. Now, this is easy to check for by using Synaptic. Open that application and from the main window click on the 'Status' button, then look for the line 'Not Installed (Residual Config)'. These are packages which have been uninstalled but do have left over config files on the system. 

To purge those packages right-click on them and choose, 'Mark For Complete Removal'. That will eliminate all traces of the packages and return the system to a pre-install state. Why does Synaptic not purge these by default? Because it is not unusual to have users that reinstall packages and this eliminates the need to configure them again from scratch. Also, having the left over config files on the system does no harm.

---

### Post by az on 2005-11-30
[QUOTE=yeahyeahyeah]
I find I need to re-install Windows every year or so to keep it running well.
[/QUOTE]

(Intense laughter)

Even if you use experimental stuff, you will not have any such problems.  If you install a problematic app, remove it.

You will always be able to fix issues like this.  Things that cannot be fixed are related to corrupted filesystems due to broken down hardware.  Your install can and will outlive your hardware.

You can even install Debian and dist-upgrade to Ubuntu.  You install once and you are done.

---

### Post by aysiu on 2005-11-30
Believe it or not, there's actually a book (part of a degunking series) called *[Degunking Linux](http://www.amazon.com/gp/product/1933097043/qid=1133401413/sr=8-1/ref=pd_bbs_1/102-7921472-1967313?n=507846&s=books&v=glance)*.

---

### Post by Xian on 2005-11-30
[QUOTE=Books]
Does Linux need to defrag?
[/QUOTE]

This is a good resource: [Linux Fragmentation & Optimization](http://dataexpedition.com/~sbnoble/Tips/filesystems.html).

---

### Post by yeahyeahyeah on 2005-11-30
So does that mean Linux will get gunked over time? Or is that book there for people llike me who _think_ Linux needs to be degunked?



[QUOTE=aysiu]Believe it or not, there's actually a book (part of a degunking series) called *[Degunking Linux](http://www.amazon.com/gp/product/1933097043/qid=1133401413/sr=8-1/ref=pd_bbs_1/102-7921472-1967313?n=507846&s=books&v=glance)*.[/QUOTE]

---

### Post by yeahyeahyeah on 2005-11-30
Here is a specific question:

I installed WINE. I've been installing windows programs like crazy. Some work, some don't.

Am I correct when i assume that none of this will hurt Linux, seeing that stuff I'm installing (i.e. internet explorer, media player, DCOM98, various DLLs, etc). And if I want to start over from scratch with WINE, I can just uninstall WINE, and delete the .wine directory?



[QUOTE=Xian]When you remove a package, if it did install a config file, that will not be removed completely unless you also purge the pkg. Now, this is easy to check for by using Synaptic. Open that application and from the main window click on the 'Status' button, then look for the line 'Not Installed (Residual Config)'. These are packages which have been uninstalled but do have left over config files on the system. 

To purge those packages right-click on them and choose, 'Mark For Complete Removal'. That will eliminate all traces of the packages and return the system to a pre-install state. Why does Synaptic not purge these by default? Because it is not unusual to have users that reinstall packages and this eliminates the need to configure them again from scratch. Also, having the left over config files on the system does no harm.[/QUOTE]

---

### Post by Xian on 2005-11-30
You quoted my statement, so I'll just say that I don't know jack about Wine since I don't run any windows programs. But when I did use it a long while back I removed it totally by purging the package and then checking the default install location (which at time was ~/win). I'm sure this has changed somewhat and another member will be better informed.

---

### Post by aysiu on 2005-11-30
[QUOTE=yeahyeahyeah]So does that mean Linux will get gunked over time? Or is that book there for people llike me who _think_ Linux needs to be degunked?[/QUOTE] It's for people like you.

---

### Post by az on 2005-11-30
[QUOTE=yeahyeahyeah] And if I want to start over from scratch with WINE, I can just uninstall WINE, and delete the .wine directory?[/QUOTE]

Just delete the .wine directory, actually.

---

### Post by rusi_pathan on 2005-11-30
You might want to use deborphan and debfoster to keep things clean. More info is available here... [http://ubuntuforums.org/showthread.php?t=90675](http://ubuntuforums.org/showthread.php?t=90675). 

There's also a debian package called cruft but its still experimental and might break things.

---

### Post by az on 2005-11-30
[QUOTE=aysiu]Believe it or not, there's actually a book (part of a degunking series) called *[Degunking Linux](http://www.amazon.com/gp/product/1933097043/qid=1133401413/sr=8-1/ref=pd_bbs_1/102-7921472-1967313?n=507846&s=books&v=glance)*.[/QUOTE]
Was that written for slackware or gentoo?  Does it apply to a package-based distro like debian or ubuntu?

---

### Post by matthew on 2005-11-30
[quote=azz]Was that written for slackware or gentoo? Does it apply to a package-based distro like debian or ubuntu?[/quote]I took a brief look at the book while browsing in the bookstore a while back. I seem to recall the main thrust was learning what processes are vital and which are not and figuring out how to remove unnecessary processes, programs and so on. Kind of like what you can do with System->Administration->Boot-Up Manager.

---

### Post by az on 2005-12-01
Yeah, but Ubuntu is already a desktop system....

---

### Post by 4linux on 2005-12-12
[QUOTE=Xian]This is a good resource: [Linux Fragmentation & Optimization](http://dataexpedition.com/~sbnoble/Tips/filesystems.html).[/QUOTE]

Yes, a good read, thanks. :)

---

### Post by Ruskie on 2005-12-13
Uhm... I don't completely agree with the statement "Linux doesn't get gunked", and here's why.
It is surely true that Linux junk does **not** slow down its operations (for there is no such thing as registry that gets read every time); it is true as well that it's memory doesn't almost get wasted, occupied by unused and useless .dll but...
What about disk space and orphan libraries?
For many of you, and for everybody coming from the corporate world, disk space is probably not an issue, but for home users might be  (and it is for me 'cause I hate disk untidiness): Linux, unlike Windows, has a whole big bunch of libraries on top of which programmers can build their applications. For example libsdl, libc, libc++, glibc... For some of these, you even have more than a version in use.
While this leads to reuse of code and can save space, and it is in general a good thing, it can also leave a cluttered disk when uninstalling programs.
I recently installed, for example, America's Army on a relatively new Kubuntu system. It installed smoothly, only not to run because he missed libstdc++5. So I installed it, which in turn required gcc-3.3-base to be installed (actual dependencies might be the reverse, not sure). Fine.

Now suppose I need disk space, and I uninstall AA. The two other packages remain. This is trash, in my opinion.
I know I can use deborphan, and I did, but I'm not satisfied on its work: first of all, it didn't recognize libstdc++ to be an orphan. Which can't be, because I didn't add anything between AA install and unistall. Maybe it has gcc depending on it, but that is waste to me!
Deborphan won't recognize orphan packages which aren't libraries. So gcc-base (which is not), won't be gathered by it.
If you use -a option it will collect ALL packages that haven't anything "appended", true... but that includes A LOT of applications which are of everyday use (for example, StarOffice, Synaptic, etc.), and distinguishing which you use and which not can be difficult and exposes you to errors.

This long message is not to complain about Linux, only to say that there is gunking to some degree, even if it does not slow the system.
However, I believe this is true with each and every operating system, and is in its very nature. That's what SysOperators are for. ;)

---

