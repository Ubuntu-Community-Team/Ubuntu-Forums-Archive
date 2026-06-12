---
title: "open office not loading"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-09-30
Ok, so I have just installed Dapper for the first time
and no open office apps will open at all.
Any help/advice?
Twould' Be great,
 cheers all.

---

### Post by cotcot on 2006-09-30
Try to uninstall it en reinstall it using ```
sudo apt-get install openoffice
``` in terminal. This will show errors if there are any during the install.

---

### Post by carverj on 2006-09-30
Yup, here is the command line output
```
jeremy@Ubuntu:~$ sudo aptitude remove openoffice
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "openoffice", and more than 40
packages contain "openoffice" in their name.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```
So the same output appears with an aptitude install openoffice
So I tried to fix in Synaptic and noticed that if you mark 
openoffice.org for removal, it marks ubuntu-desktop only for 
removal.
What does this mean? Does that remove your GUI?

Thanks again

---

### Post by aysiu on 2006-09-30
You shouldn't have to install OpenOffice. It's already installed.

Try running this command from the terminal. If it doesn't work, post the output back here: ```
oowriter
```

---

### Post by carverj on 2006-09-30
oowriter output:
```
jeremy@Ubuntu:~$ oowriter
/usr/lib/openoffice/program/soffice: line 233: 17878 Illegal instruction     "$sd_prog/$sd_binary" "$@"

** (process:17861): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

---

### Post by aysiu on 2006-09-30
Hm. Weird. I Googled that error and **nothing** came up in the search results.

Maybe try this? ```
sudo aptitude update
sudo aptitude reinstall openoffice.org-gnome openoffice.org
```

---

### Post by carverj on 2006-09-30
```
jeremy@Ubuntu:~$ oowriter
/usr/lib/openoffice/program/soffice: line 233: 19322 Illegal instruction     "$sd_prog/$sd_binary" "$@"

** (process:19305): WARNING **: Unknown error forking main binary / abnormal early exit ...

```
a similar error after update and reinstall

---

### Post by aysiu on 2006-09-30
Not sure if this might help, but [a Google search without the numbers turned up a few links](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=%2Fusr%2Flib%2Fopenoffice%2Fprogram%2Fsoffice%3A+line+Illegal+instruction+&btnG=Search). You may want to check them out.

---

### Post by carverj on 2006-09-30
rebooted to different i386 grub header with similar result:

```
/usr/lib/openoffice/program/soffice: line 233:  5073 Illegal instruction     "$s d_prog/$sd_binary" "$@"

** (process:5056): WARNING **: Unknown error forking main binary / abnormal earl y exit ...

```
attempted to reconfigure OOo-common as per:
> [http://lists.debian.org/debian-openoffice/2006/07/msg00192.html](http://lists.debian.org/debian-openoffice/2006/07/msg00192.html)
That hasn't worked.

Just wondering if this:
[http://lists.debian.org/debian-openoffice/2006/07/msg00199.html](http://lists.debian.org/debian-openoffice/2006/07/msg00199.html)
is the solution, and if so how would I go about implementing this?

Thanks very much for your help.

---

### Post by aysiu on 2006-09-30
I don't know. It seems it's a bug. I don't know why *you're* getting the bug, though. After all, there are thousands of Ubuntu users with no OpenOffice problems at all.

No idea what went wrong. Unless someone else has a bright idea, I'd hate to say it... but it may be a reinstall that fixes it.

---

### Post by carverj on 2006-09-30
Such is life. no worries as long as gedit,etc. works.
am trying to use mono project for a C# program in the .NET framework
at the moment. it doesn't seem to have the libraries installed by 
default. Oh well, at least everything else works and looks nicer than 
Windows by a long shot
:)

---

### Post by kfjethro on 2006-10-03
I get a similar message:

/usr/lib/openoffice2/program/soffice: line 224: 21078 Segmentation fault      "$sd_prog/$sd_binary" "$@"

I'm running a dual-core opteron with 5.10. Carverj, what's your system config ?

Thanks.

---

