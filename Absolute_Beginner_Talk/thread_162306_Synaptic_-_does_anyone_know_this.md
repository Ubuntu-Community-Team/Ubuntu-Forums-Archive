---
title: "Synaptic - does anyone know this?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-18
Back again with the same problem.
Installation of 'avidemux' went awry
Synaptic will not load and shows this:
[COLOR="Blue"]E: The package avidemux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/COLOR]
Have tried to uninstall/reinstall and manually remove all avidemux files to no avail.
(using automatix/dpkg/apt-get etc)

Question: Can I edit some file that Synaptic uses so it ignores this botched install and loads the cache etc ?
I did try (from the Synatic help page) apt-get install -f to no avail.
I searched for files containing the word 'avidemux' and found these and my question is **can I just edit out the avidemux reference in one or more to get back my Synaptic ?**

var/lib/dpkg/info/automatix.list
/var/lib/dpkg/status
/var/lib/dpkg/available
/var/lib/dpkg/available-old
/var/lib/gstreamer/0.8
/var/cache/apt/pkgcache.bin
/usr/lib/gstreamer0.8/libgstavi.so
/usr/loca/automatix/autoscript

signed "getting frustrated"

---

### Post by user1397 on 2006-04-18
[quote=cliff0108]Back again with the same problem.
Installation of 'avidemux' went awry
Synaptic will not load and shows this:
[COLOR=Blue]E: The package avidemux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/COLOR]
Have tried to uninstall/reinstall and manually remove all avidemux files to no avail.
(using automatix/dpkg/apt-get etc)

Question: Can I edit some file that Synaptic uses so it ignores this botched install and loads the cache etc ?
I did try (from the Synatic help page) apt-get install -f to no avail.
I searched for files containing the word 'avidemux' and found these and my question is **can I just edit out the avidemux reference in one or more to get back my Synaptic ?**

var/lib/dpkg/info/automatix.list
/var/lib/dpkg/status
/var/lib/dpkg/available
/var/lib/dpkg/available-old
/var/lib/gstreamer/0.8
/var/cache/apt/pkgcache.bin
/usr/lib/gstreamer0.8/libgstavi.so
/usr/loca/automatix/autoscript

signed "getting frustrated"[/quote] Did you ever click the reload button on synaptic? _**Or**_ type in terminal: "sudo apt-get update"  Then try to reinstall.

---

### Post by cliff0108 on 2006-04-18
Yes - Repeatedly !

When I try to re-install I get this message :

E: The package avidemux needs to be reinstalled, but I can't find an archive for it.

I have downloaded the file avidemux-2.1.0-1_i386.deb - but I don't know how synaptic "finds" the archive.

I'm about ready to pack in in and go back to XP.

---

### Post by wolfee on 2006-04-18
try uninstalling it from synaptics then reboot then reinstall it through synaptics. This is what I did and it worked for me.

---

### Post by cliff0108 on 2006-04-18
I'd love to but Synaptic doesn't load any thing - just the error message as shown above.
Evidently it can't access the archive and I haven't a clue why.
Thanks for the suggestion tho :)

---

### Post by towsonu2003 on 2006-04-18
I don't see avidemux as a package in the repositories. [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=avidemux&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=avidemux&searchon=names&subword=1&version=breezy&release=all)

why do you think it is in the repos? did you add a custom repo for it? (I wouldn't know if it is in backports)

if you want to install the .deb file, do
```

dpkg -i /path/to/yourfile.deb

```

but beware that if this package's dependencies are not met, you'll risk damage to your installation. I'm not sure how well dpkg handles dependencies. 

I'm confused that you wanna go back to windows for a package. if avidemux is for playing videos, try mplayer or other available video players.

---

### Post by cliff0108 on 2006-04-18
Thanks - but this is what my terminal says when I do as suggested :

cliff@ubuntu:~/Desktop/Avidemux$ sudo dpkg -i avidemux-2.1.0-1_i386.deb
(Reading database ...
dpkg: serious warning: files list file for package `avidemux' missing, assuming package has no files currently installed.
108981 files and directories currently installed.)
Preparing to replace avidemux-2.1.0 2.1.0-1 (using avidemux-2.1.0-1_i386.deb) ...
Unpacking replacement avidemux-2.1.0 ...
Setting up avidemux-2.1.0 (2.1.0-1) ...

I'm not sure what this means.

I then run Synaptic and get the same error message - as above - the avidemux needs to be re-installed.

I am quite disenchanted with Avidemux - I only want Synaptic back :o)

---

### Post by cliff0108 on 2006-04-18
I tried dpkg with -r and -P options with this result:

liff@ubuntu:~/Desktop/Avidemux$ sudo dpkg -P avidemux
dpkg: error processing avidemux (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 avidemux
cliff@ubuntu:~/Desktop/Avidemux$ sudo dpkg -i avidemux
dpkg: error processing avidemux (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 avidemux
cliff@ubuntu:~/Desktop/Avidemux$ sudo dpkg -r avidemux
dpkg: error processing avidemux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 avidemux

It will not - of course - reinstall - see above.
Any suggestions?

---

### Post by htinn on 2006-04-18
[QUOTE=cliff0108]cliff@ubuntu:~/Desktop/Avidemux$ sudo dpkg -i avidemux
dpkg: error processing avidemux (--install):
 cannot access archive: **No such file or directory**
Errors were encountered while processing:
 avidemux[/QUOTE]

Try finding an actual deb file to install before trying that.

---

### Post by towsonu2003 on 2006-04-18
[QUOTE=htinn]Try finding an actual deb file to install before trying that.[/QUOTE]
s/he did, which didn't work :(
> cliff@ubuntu:~/Desktop/Avidemux$ sudo dpkg -i avidemux-2.1.0-1_i386.deb
(Reading database ...
dpkg: serious warning: files list file for package `avidemux' missing, assuming package has no files currently installed.
108981 files and directories currently installed.)
Preparing to replace avidemux-2.1.0 2.1.0-1 (using avidemux-2.1.0-1_i386.deb) ...
Unpacking replacement avidemux-2.1.0 ...
Setting up avidemux-2.1.0 (2.1.0-1) ...


check out these:
[http://lists.debian.org/debian-user/2005/02/msg00201.html](http://lists.debian.org/debian-user/2005/02/msg00201.html)
[http://www.tersesystems.com/post/23.jhtml](http://www.tersesystems.com/post/23.jhtml)
[http://ubuntuforums.org/showthread.php?t=111991](http://ubuntuforums.org/showthread.php?t=111991)
[http://forum.libranet.com/viewtopic.php?p=61173&](http://forum.libranet.com/viewtopic.php?p=61173&)

these were the links where I think a solution may be given to your situation. They are repetitious, but they also give new ideas (such as tweaking package's script -last one). 

copy paste errors that those suggestions give you. One of them might work. also, file a critical bug report to where ever you got this package, or contact its creator: it broke your debian-based system. 

there is also the possibility for you to compile this from source and install your own .deb instead of the .deb you got.

---

### Post by cliff0108 on 2006-04-19
Thanks towsonu2003 - I'll give these a look and see what might work !

---

### Post by cliff0108 on 2006-04-19
THIS WORKED !!!!!! :) 
sudo dpkg -r --force-remove-reinstreq avidemux 

Yahoo !!!

---

### Post by cliff0108 on 2006-04-19
**Thank you Towsonu2003 !!**

There was good info in the second link that worked:

**sudo dpkg -r --force-remove-reinstreq avidemux**

This forced the removal of the damaged file which was marked for reinstallation. Once it was gone  - with the final terminal message  "Removing avidemux..." I was able to load Synaptic normally. 
In retrospect I will be more careful about the application and method of install. There is likely nothing wrong with avidemux - just my method of install perhaps (?)

Thanks also to everyone else who looked at my issue and gave suggestions. What a terrifc forum this is !

Cliff

---

### Post by jonnyfive on 2006-04-26
I had the exact same problem and the same solution fixed it. This whole stupid thing started out from automatix, it installed that avidemux and caused me a whole lot of hassle. I as well just switched from XP and stupid problems like this frustrate me and want to go back.

---

### Post by towsonu2003 on 2006-04-26
[QUOTE=jonnyfive]I had the exact same problem and the same solution fixed it. This whole stupid thing started out from automatix, it installed that avidemux and caused me a whole lot of hassle. I as well just switched from XP and stupid problems like this frustrate me and want to go back.[/QUOTE]
when you get software bugs like this, always let the developer of that software know (in this case, see the Automatix forum section). Of course, doing so kindly and providing the steps you tooks, the errors you got, and the work around ou found. 

Sometimes they just won't fix it, at which point you have to decide whether you should continue to use it or not. I abandoned a program (R for statistics) when the devel insulted me after I suggested a feature, which was crucial for me. But a feature I requested from openoffice got rejected, but I'm still using it (not so crucial feature, devel's point ok for me, etc). 

It sometimes gets frustrating, so distance yourself from the issue bf you post the bug report. ;)

---

### Post by cliff0108 on 2006-04-26
You are quite right.
I just took it that I was at fault here - not the developer - and I couldn't recall precisely what the installation form was. I gather though that a similar problem was manifest using Automatix. I'm glad to hear - because I was going to try that next.

---

