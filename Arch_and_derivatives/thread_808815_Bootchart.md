---
title: "Bootchart?"
date: 2008-05-26
forum: Arch and derivatives
---

### Post by Dr Small on 2008-05-26
I used to have bootchart setup on Ubuntu, and it "magically worked", which is creepy if you ask me. Anyhow, I am trying to get it setup for Arch, and 'tis not working so far.

I installed bootchart with pacman, got it all downloaded. The message after setting up bootchart was:
>  Bootchart usage : 
  make sure to append init=/sbin/bootchartd to your
  kernel parameters (it is recommended that you 
  create another entry specifically for bootchart
  logging).
  Run bootchart-render to render your bootchart

So I edited my menu.lst, which now looks like this:
```
# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda3 ro vga=771 init=/sbin/bootchartd
initrd /kernel26.img
```

I rebooted, looked around in /var/log for anything pertaining to "bootchart", saw nothing. Then attempted to run:
```
bootchart-render
```
Which then spilled out:
```
/var/log/bootchart.tgz not found
```

So apparently, bootchart never started.
What am I doing wrong, or where have I made my error?

Dr Small

---

### Post by Patogen on 2008-05-27
> **Dr Small said:**
> 
So apparently, bootchart never started.
What am I doing wrong, or where have I made my error?

Dr Small

I tried to get bootchart working for a while on Arch as well, and couldn't get it to work. I read lots of documentation and couldn't get it to work, there's a new post on the arch forum:

[http://bbs.archlinux.org/viewtopic.php?id=49252](http://bbs.archlinux.org/viewtopic.php?id=49252)

Which is kinda the same as I get. So I think there's a problem with it. There's been no new bootchart release for a while, and the arch package is old:

```

Name           : bootchart
Version        : 0.9-3
URL            : http://www.bootchart.org/
Licenses       : None
Groups         : None
Provides       : None
Depends On     : j2re  acct  
Optional Deps  : None
Required By    : None
Conflicts With : None
Replaces       : None
Installed Size :  97.96 K
Packager       : Aaron Griffin (phrakture) {email removed by me}
Architecture   : i686
Build Date     : Tue 16 May 2006 06:20:55 PM CEST
Install Date   : Sun 13 Apr 2008 07:01:53 PM CEST
Install Reason : Explicitly installed
Install Script : Yes
Description    : Boot Process Performance Visualization

```

Since arch has changed a lot since 16 May 2006 when the package was built I guess the pkgbuild needs to update according to how the structure is now ... I'm not sure how to do that however ... and since I forgot to report/make a thread about it ... there wasn't one. So I also have a problem.

---

### Post by Barrucadu on 2008-05-27
Very odd, I just installed bootchart and it worked perfectly.

---

### Post by Dr Small on 2008-05-27
YES. I got it to work. Apparently the script is looking for gdm, kdm or the sorts to stop, and well, I don't have none of that. So I added xdm to line 120 of /sbin/bootchart,  and then bootchart.tgz showed up in /var/log

The problem is, I am still getting this error at bootup that says:
```
/sbin/bootchart line 124 :[ :5
5: integer expression expected
```

---

