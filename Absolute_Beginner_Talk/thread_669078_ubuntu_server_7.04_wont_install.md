---
title: "ubuntu server 7.04 wont install"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Malegnis on 2008-01-16
ok, sorry if this has been answered i couldn't find anything before while searching.  i had ubuntu desktop installed for a while, and was using it like a server.   but i decided that i wanted less ram usage and i also wanted to try the ubuntu server edition, so i burn the cd pop it in the computer, and it brings up the screen where i would select "install to hard disc" but when i select it. it goes to "loading linux kernal" then after that it restarts my computer and brings me back to the same screen. 

my hardware specs are that of an old windows 2000 machine, but it ran the desktop (though slowly) so i really dont see why it wouldn't run the server version.

and if this has already been answered i truly am apologetic.

thanks.

---

### Post by hyper_ch on 2008-01-16
did you check the cd for defects?

---

### Post by Malegnis on 2008-01-16
tried checking cd for defects, but it wont load the linux kernel without kicking me out and rebooting. so i tried re burning the cd onto a regular disc as apposed to the CD-rw i had before.

after i post this, i will be trying to install on my laptop, to rule out the fact that it may be my cd.

---

### Post by Malegnis on 2008-01-22
i have confirmed that it is in face not my cd, but a problem somewhere in my computer.

---

### Post by hyper_ch on 2008-01-22
how about trying ubuntu server 7.10?

---

### Post by ddrplayer512 on 2008-01-22
Try using the alternate CD. I heard you can install a text mode system. The server cd I heard uses a different kernel optimized for servers, not a problem on most computers, but some can have problems.

---

### Post by scorp123 on 2008-01-22
> **Malegnis said:**
>  my hardware specs are that of an old windows 2000 machine, but it ran the desktop (though slowly) so i really dont see why it wouldn't run the server version. The server version uses a different kernel compiled with different options (e.g. with server hardware in mind). What's your CPU type? The server edition makes use of various options which are per default turned off in the desktop edition. So it could very well be that the desktop edition will work on an old machine and the server edition won't.

---

### Post by Malegnis on 2008-01-23
well i just tried installing off the regular desktop cd. and i have the same. issue, yet its the same CD i used to originally install it.

---

### Post by Rhubarb on 2008-01-23
I know from experience that ubuntu server does not support old CPUs.
However, it can be installed on a machine with an old CPU.
If you can, you need to install linux-generic, and change the default /boot/grub/menu.lst to use the generic kernel.

To install linux-generic, you may have to boot up ubuntu server on newer hardware (pull the hard disk out, install it from a newer PC).
```
sudo aptitude install linux-generic
```

Here's a thread that may help you out:
[http://ubuntuforums.org/showthread.php?t=635532](http://ubuntuforums.org/showthread.php?t=635532)

---

