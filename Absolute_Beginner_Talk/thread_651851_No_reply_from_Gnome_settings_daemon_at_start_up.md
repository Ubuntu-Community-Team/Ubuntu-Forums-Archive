---
title: "No reply from Gnome settings daemon at start up"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-12-28
Just recently, my gutsy installation has been displaying the following error at startup from cold.

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

If I log out and back in it works fine, but that get's annoying having to do that each time I start my computer.


Can anyone tell me how to fix it?

---

### Post by The Cog on 2007-12-28
Occasionally happens to me too. Just to let you know that you're not alone.

---

### Post by ubnewbie2 on 2007-12-28
> **The Cog said:**
> Occasionally happens to me too. Just to let you know that you're not alone.

Thanks. :)

Seems to have happened every time for the last three times at least.  Maybe an update has caused it, as it never happened before on Feisty, nor on Gutsy (until recently)

Hope it settles down....

---

### Post by teasum on 2007-12-28
I have had this error recurring for weeks, and I can't tell what is causing it.  Any feedback or suggestions on how to fix it would definitely be appreciated.

---

### Post by adramalech on 2007-12-28
Same here i just started getting it when i made wireless driver permanently load instead of me every time having to* modprobe ndiswrapper* ]:confused:

try and do this put into the terminal *gnome-settings daemon *and post it in this thread:popcorn:

adramalech@adramalech:~$ gnome-settings-daemon

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)

(the only reason i get this is becuase i am running xserver maybe if i turn of the other ones and do a ctrl+alt f2 i will get a better result !!!)

---

### Post by ubnewbie2 on 2007-12-28
> **adramalech said:**
> Same here i just started getting it when i made wireless driver permanently load instead of me every time having to* modprobe ndiswrapper* ]:confused:

try and do this put into the terminal *gnome-settings daemon *and post it in this thread:popcorn:

adramalech@adramalech:~$ gnome-settings-daemon

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)

(the only reason i get this is becuase i am running xserver maybe if i turn of the other ones and do a ctrl+alt f2 i will get a better result !!!)

Mine does the same.  I am not sure what this proves though. Maybe running it manually when I get the error would avoid having to log out and back in?

---

### Post by ugm6hr on 2007-12-28
This is an intermittent problem for me too.  It doesn't seem to influence the way Ubuntu works for me though (although I use the standard theme).  Although it is annoying.  On one occasion, my desktop did not load (only panels).

I did find this:
[http://ubuntuforums.org/showpost.php?p=3776732&postcount=15](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15)

I am just about to give it a try - but it appears to have worked for others.

---

### Post by ubnewbie2 on 2007-12-28
> **ugm6hr said:**
> This is an intermittent problem for me too.  It doesn't seem to influence the way Ubuntu works for me though (although I use the standard theme).  Although it is annoying.  On one occasion, my desktop did not load (only panels).

I did find this:
[http://ubuntuforums.org/showpost.php?p=3776732&postcount=15](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15)

I am just about to give it a try - but it appears to have worked for others.


I have implemented it just now also. We will see over the coming days, how well it works.

---

### Post by adramalech on 2007-12-30
Yes I have to agree that it doesn't affect the kernel at all in functionality...it does though take forever to boot though...:(

---

### Post by ubnewbie2 on 2007-12-30
> **adramalech said:**
> Yes I have to agree that it doesn't affect the kernel at all in functionality...it does though take forever to boot though...:(

It changes the way the desktop looks, particularly, in my case, all the fonts are too small, if it doesn't start correctly.  Boot time is normal though - I would hazard a guess that if your boot time is long, then you are looking at a different problem.

---

### Post by adramalech on 2007-12-30
Well my computer once or twice did that and didn't connect right and i got like a bluish screen and have my icons on the desktop were gone....but it only happened on the normal kernel once...(2.6.22.xx-generic) on my other one...2.6.23.xx it will happen every time and will error with the message...

---

