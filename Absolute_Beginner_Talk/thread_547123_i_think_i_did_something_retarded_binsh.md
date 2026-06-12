---
title: "i think i did something retarded /bin/sh"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-09-09
to install mountiso from [http://www.kde-apps.org/content/show.php?content=11577&forumpage=16]("http://www.kde-apps.org/content/show.php?content=11577&forumpage=16")

i tried doing it the way the readme said. however, ./install.sh did not work so i followed this: 

```
sudo su
rm /bin/sh
ln -s /bin/sh /bin/bash
```

hoping that it would work. however it did not work, and now everytime i open up the konsole, i get this:

```
bash: /usr/bin/lesspipe: /bin/sh: bad interpreter: Permission denied
```

can someone sort this out for me? TIA -- i am using kubuntu 7.04

---

### Post by tripokey on 2007-09-09
type in your terminal:
```
sudo chmod 777 /bin/sh
```

---

### Post by kerry_s on 2007-09-09
you linked it the wrong way, suppose to be>
**sudo ln -s /bin/bash /bin/sh**

but the proper way to do it is>
**sudo dpkg-reconfigure dash**

---

### Post by Miroku on 2007-09-09
tried that

still same problem

---

### Post by Miroku on 2007-09-09
```
sudo ln -s /bin/bash /bin/sh
``` <-- didnt do anything


output of this:

```
sudo dpkg-reconfigure dash
```

was:

```
Can't exec "/var/lib/dpkg/info/dash.prerm": Permission denied at /usr/sbin/dpkg-reconfigure line 129.
Can't exec "/var/lib/dpkg/info/dash.config": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of /var/lib/dpkg/info/dash.config reconfigure 0.5.3-5ubuntu2 failed at /usr/share/perl5/Debconf/ConfModule.pm line 58
```

---

### Post by Miroku on 2007-09-09
also, this wont damage my system will it?

i have horror stories about how i restart my comp and it gets stuck at the nvidia splash screen.

---

### Post by Miroku on 2007-09-09
ahhhhhhhhhh

i just logged out and tried to login but it said 'cannot login due to internal error'


nooo not again....stupid freaking kdeapps misguiding me like ....:( :(

and then it wasnt even able to reboot

i am now stuck in XP :( :(

---

### Post by wog on 2007-09-09
What is mountiso even supposed to accomplish? What's it for?

---

### Post by Miroku on 2007-09-09
its supposed to be similar to alcohol 120%, meaning you can mount iso/nrg/images without burning them onto a CD/DVD

but man, i REALLY do not want to reinstall kubuntu just to fix it...

---

### Post by tripokey on 2007-09-09
Hate to break it to you... but you can mount iso files with the regular mount command

---

### Post by scxtt on 2007-09-09
a LiveCD can allow you to fix it, just mount the partition w/ the "problem" and create the proper link ... the LiveCD should have bash and dash on it already ...

---

### Post by Miroku on 2007-09-09
yea, i sorta knew that tripokey, but this thing just looked cool.

and u make it sound like i do need to reinstall...damn it allllll

---

### Post by scxtt on 2007-09-09
you don't have to re-install ... just remain calm, grab Sango's  butt or something ;)

---

### Post by Miroku on 2007-09-09
> **scxtt said:**
> a LiveCD can allow you to fix it, just mount the partition w/ the "problem" and create the proper link ... the LiveCD should have bash and dash on it already ...


can you please explain in more detail what it is i need to do exactly because i really want to get it back to the way it was. and please dont mind if i do ask dumb questions.

i do have the alternate install CD for 7.04, i have to look for the liveCD

and how would i mount this partition, and how would i create the proper link exactly? thx.


haha, yea i need sango's boomerang to knock out my PC.

---

### Post by scxtt on 2007-09-09
fire up a LiveCD, open a terminal, then type:
```
sudo fdisk -l
```from that, you should be able to find out which [color=blue]<partition>[/color] (ex. sda1) is your Ubuntu install ... then do the following:
```
sudo mkdir /media/recovery
sudo mount /dev/[color=blue]<partition>[/color] /media/recovery
cd /media/recovery/bin
sudo ln -s /media/recovery/bin/bash /media/recovery/bin/sh
```for the last line, you just need to make sure sh -> /bin/bash {assuming that's really the *only* issue you're having}.
```
:> ls -l | grep sh
-rwxr-xr-x 1 root root  797208 2007-04-10 21:08 bash
-rwxr-xr-x 1 root root   99512 2007-03-05 07:40 dash
lrwxrwxrwx 1 root root      21 2007-09-03 19:51 ksh -> /etc/alternatives/ksh
lrwxrwxrwx 1 root root       4 2007-09-03 03:32 rbash -> bash
lrwxrwxrwx 1 root root      22 2007-09-03 19:51 rzsh -> /etc/alternatives/rzsh
[color=green]lrwxrwxrwx 1 root root       9 2007-09-06 02:30 sh -> /bin/bash[/color]
lrwxrwxrwx 1 root root       4 2007-09-03 03:32 sh.distrib -> bash
lrwxrwxrwx 1 root root      21 2007-09-03 19:51 zsh -> /etc/alternatives/zsh
-rwxr-xr-x 1 root root  602400 2006-12-14 16:42 zsh4
```

---

### Post by Miroku on 2007-09-09
alrite, let me print this, and i will get back to u as soon as i can.

very grateful for your help. now lets hope it makes this ok.

---

### Post by Miroku on 2007-09-09
alrite so i did all the things, however, there is a problem.

this:

```
sudo ln -s /media/recovery/bin/bash /media/recovery/bin/sh
```
leads to:
```
ln: creating symbolic link `/media/recovery/bin/sh/bash' to `/media/recovery/bin/bash': File exists
```

when i do this:

```
ls -l | grep sh
```

i get this:

```
-rwxr-xr-x 1 root root  700560 2007-04-10 23:32 bash
-rwxr-xr-x 1 root root   80500 2007-03-05 06:00 dash
lrwxrwxrwx 1 root root       4 2007-05-21 14:03 rbash -> bash
drwxrwxrwx 2 root root    4096 2007-09-09 21:12 sh
lrwxrwxrwx 1 root root       4 2007-05-21 14:03 sh.distrib -> bash
```

there is no sh -> /bin/bash

what do i do now?

im currently using the livecd, so i will wait here. thanks.

---

### Post by scxtt on 2007-09-09
if you're in the /media/recovery/bin/ directory, i'm not sure why you have a sh directory ... but if you're there, do this:

ln -s bash sh

that should give you **sh -> bash** which should have a l (link) in the 1st position and not a d (directory) ... much like **rbash -> bash** in your listing above.

---

### Post by Miroku on 2007-09-09
```
ubuntu@ubuntu:/media/recovery/bin$ ln -s bash sh
ln: creating symbolic link `sh/bash' to `bash': File exists

```

and then

```
ubuntu@ubuntu:/media/recovery/bin$ ls -l | grep sh
-rwxr-xr-x 1 root root  700560 2007-04-10 23:32 bash
-rwxr-xr-x 1 root root   80500 2007-03-05 06:00 dash
lrwxrwxrwx 1 root root       4 2007-05-21 14:03 rbash -> bash
drwxrwxrwx 2 root root    4096 2007-09-09 21:12 sh
lrwxrwxrwx 1 root root       4 2007-05-21 14:03 sh.distrib -> bash
```

i dont think it did anything.

---

### Post by scxtt on 2007-09-09
and it won't cause you have a sh directory (not sure why) - you most likely need to get rid of it: **sudo rm -rf sh** (make sure you're in /media/recovery/bin) ...

---

### Post by Miroku on 2007-09-09
```
ubuntu@ubuntu:/media/recovery/bin$ sudo rm -rf sh
ubuntu@ubuntu:/media/recovery/bin$ ls -l | grep sh
-rwxr-xr-x 1 root root  700560 2007-04-10 23:32 bash
-rwxr-xr-x 1 root root   80500 2007-03-05 06:00 dash
lrwxrwxrwx 1 root root       4 2007-05-21 14:03 rbash -> bash
lrwxrwxrwx 1 root root       4 2007-05-21 14:03 sh.distrib -> bash
```


well the sh directory seems to be gone ... now what?

lol, i hope you are not getting annoyed by my lack of knowledge of anything. =]

---

### Post by scxtt on 2007-09-09
sudo ln -s bash sh

---

### Post by wog on 2007-09-09
What would be the command line for mounting an .iso? Is it just like mounting a partition?

---

### Post by Miroku on 2007-09-09
> **scxtt said:**
> sudo ln -s bash sh

THANK U so much

im back in kubuntu. my terminal doesnt give me any errors when i start it up, and i just logged out and could log back in.

u r my new best friend. lol. thx again.

---

### Post by jordanmthomas on 2007-09-09
> **wog said:**
> What would be the command line for mounting an .iso? Is it just like mounting a partition?
```
mount -o loop -t iso9660 [COLOR="Blue"]YOURISO.iso[/COLOR][COLOR="Magenta"] /path/to/mount/at[/COLOR]
```

(assuming it's a standard, run-of-the-mill iso you have)

---

### Post by wog on 2007-09-09
thank you for the mount info! :)

---

### Post by scxtt on 2007-09-09
> **Miroku said:**
> THANK U so much

im back in kubuntu. my terminal doesnt give me any errors when i start it up, and i just logged out and could log back in.

u r my new best friend. lol. thx again.glad to hear it worked out, hopefully you're able to troubleshoot similar issues on your own w/ the new knowledge you have :)

---

### Post by Miroku on 2007-09-12
> **jordanmthomas said:**
> ```
mount -o loop -t iso9660 [COLOR="Blue"]YOURISO.iso[/COLOR][COLOR="Magenta"] /path/to/mount/at[/COLOR]
```

(assuming it's a standard, run-of-the-mill iso you have)

only root can mount?
```

[B]mount -o loop -t iso9660 video.iso /home/here/img
mount: only root can do that[/B]
```

---

### Post by jordanmthomas on 2007-09-12
Yes, only root can mount isos by default.  Just prepend a sudo and you'll be set.

---

### Post by Miroku on 2007-09-12
ok cool

nice, i learned how to mount.

but i also found out that kaffeine plays iso images. w00t

thx

---

