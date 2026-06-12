---
title: "v4l-dvb - need to link source (how?)"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by jb5 on 2007-10-08
HELP !!
I'm trying to set up my DVB tuner following this guide [Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI")

In order to build the v4l-dvb modules, apparently I need to execute the following before executing the  make command:-
```
sudo ln -s /usr/src/linux-source-2.6.22/ /lib/modules/2.6.22-13-generic/source
```

Making sure that the kernal version matches the one in use.
```
jb@eric:~$ uname -r
2.6.20-16-generic

```

So for my setup I would change the numbers to 2.6.20-16. 
OK, so far so good. 
Problem is 
```
jb@eric:/usr/src$ ls
fglrx-kernel-2.6.20-16-generic_8.41.7-1+2.6.20-16.32_amd64.deb
fglrx.tar.bz2
linux
linux-headers-2.6.20-15
linux-headers-2.6.20-15-generic
linux-headers-2.6.20-16
linux-headers-2.6.20-16-generic
modules

```
Despite my best efforts I cannot work out how I can get the "source" directory for my setup on to my PC!

Is there a kind soul who can point me in the right direction?
The simpler / more explicit the instructions the better! LOL

---

### Post by nick_h on 2007-10-08
The easiest way to get the source is to type:
```
apt-get source linux-image-2.6.20-16-generic
apt-get build-dep linux-image-2.6.20-16-generic
```
as described [here](https://help.ubuntu.com/community/Kernel/Compile).

However, I can't remember having to install the kernel source when I built the v4l-dvb modules.  Where does it tell you to make the link? - I can't see it in the instructions you linked to.

---

### Post by jb5 on 2007-10-08
Firstly - thank you so much! I've been going round in circles trying to get this working again. :KS

When I tried to make the v4l-dvb modules about 6 days ago, I didn't need the source files either! 

After re-installing Ubuntu again (Don't ask! LOL), whenever I issued the make command I got this error
```

jb@eric:~$ cd v4l-dvb/
jb@eric:~/v4l-dvb$ make
make -C /home/jb/v4l-dvb/v4l 
make[1]: Entering directory `/home/jb/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.20-16-generic/source ./.myconfig ./config-compat.h
File not found: /lib/modules/2.6.20-16-generic/source/include/linux/netdevice.h at scripts/make_config_compat.pl line 15.
make[1]: *** [config-compat.h] Error 2
make[1]: Leaving directory `/home/jb/v4l-dvb/v4l'
make: *** [all] Error 2
jb@eric:~/v4l-dvb$ 

```

So after much googling I came across this thread [v4l-dvb](http://ubuntuforums.org/showthread.php?t=566542) and another thread which I can't find anymore, which suggested linking the source files. Hence my search to try and find how to do this!

What happened in the intervening 6 days to make this extra step necessary I haven't a clue? :confused:
But I now have the dvb card working. :) \\:D/\\:D/\\:D/

Thank you again:popcorn:

(Just got to get the rest of it working again now!) :lolflag:

---

### Post by nick_h on 2007-10-08
I'm glad you got it working.

I followed instructions for a different card - [here](http://ubuntuforums.org/showthread.php?t=198423).  The only difference I can see is that your instructions don't include a *make config* line.

---

### Post by jb5 on 2007-10-09
Hmm, interesting. I followed the same instructions I linked to above to get the v4l-dvb working on every occasion, the first time it worked and on the subsequent occasions it didn't! 

I will give the ```
make config
``` a go next time, to see if that removes the need for the source files.

Thank you again.

---

### Post by dalejefferson on 2007-10-09
Hi Guys i've updated the Mythtv Wiki to sort out this issue

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

---

### Post by tobycatlin on 2007-10-09
dale 
I got the v4l drivers complied ok but they are trying to use the old version that use firmware dvb-usb-dib0700-01.fw 
If i understand correctly this version doesn't have remote support. 
I followed your instructions on a fresh install of feisty and this is the point i am stuck on. Your instructions worked fine on another machine but that has been updated since dapper, so it must be something to do with a clean feisty.


thanks for any help
toby

---

### Post by dalejefferson on 2007-10-09
I did 3 clean installs today using those instructions (I sell Nova-T 500 Mythtv systems)

It works!

Added new line to WIKI

Reboot if you have updated your kernel or you will have to recompile for the new kernel

That looks like your issue, there are lots of kernel updates on a fresh install and you proberly complied against the wrong kernel

Just re compile and you should be OK ;)

---

### Post by tobycatlin on 2007-10-09
yep you are right. a re-complie and a cold restart did the job. 
Thanks for your time. This is off topic but, do you ever use antec fusion v2 cases? (bet you can guess the next question) and have you ever got the vfd to work. I have spent the last couple of days following guides to no avail.

---

### Post by dalejefferson on 2007-10-09
> **tobycatlin said:**
> yep you are right. a re-complie and a cold restart did the job. 
Thanks for your time. This is off topic but, do you ever use antec fusion v2 cases? (bet you can guess the next question) and have you ever got the vfd to work. I have spent the last couple of days following guides to no avail.

No but I did look into it and it did seem possible but too much hard work for me.

---

### Post by tobycatlin on 2007-10-09
damn i was hoping for a magic bullet solution. I hate hard work.
Thanks again

---

