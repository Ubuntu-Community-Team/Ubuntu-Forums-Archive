---
title: "Newbie Question please HELP!"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by 1972_OLDS_442 on 2007-04-18
I encountered the Xserver problem, I did do the "sudo dpkg-reconfigure xserver-xorg" I went through the prompt and at the end I got this message at the bottom of the screen "xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf. 20070518200158" after that I get the comand prompt "ubuntu@ubuntu:~$",what do I do now?

Thanks alot. This site was very helpful on my first problem.:)

---

### Post by izizzle on 2007-04-18
A little background would help netx time :wink:

Are you trying to install XGL, Beryl or some other software that you encountered this problem. If so, you can search the beryl forums to find a "sudo" command you can execute from ubuntu to solve your problem.

hope this helps,

- Imran

---

### Post by kittyhawk63 on 2007-04-18
> **1972_OLDS_442 said:**
> I encountered the Xserver problem, I did do the "sudo dpkg-reconfigure xserver-xorg" I went through the prompt and at the end I got this message at the bottom of the screen "xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf. 20070518200158" after that I get the comand prompt "ubuntu@ubuntu:~$",what do I do now?
Thanks alot. This site was very helpful on my first problem.:)

ubuntu@ubuntu suggests that you may not have "installed" Ubuntu using the liveCD.  Are you still just using the LiveCD on your CD-Rom drive?

---

### Post by 1972_OLDS_442 on 2007-04-18
I never got into the actual Ubuntu it was still loading when it done, it was after I selected "start and install" while it was loading it came up with the Xservre failed to start I done that configuration then I got to where I'm now sorry if I was a little vague in the origional post.

edit* Yes I am still on the Live CD

---

### Post by freebird54 on 2007-04-18
All you do with that information is note the name it gave you - that is the automatic backup - tagged with the date/time in the name.  NOW?  Test how it worked.  If it didn't give the right result, try again - following the guide here:  [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

Hope this helps!  :)

---

### Post by 1972_OLDS_442 on 2007-04-18
Thanks Freebird54 This should fix my problem.

One more quick question is there any way to save my changes to a floppy disk, this computer is 9 years old and does not yet have a CD burner.



[SIZE="6"]THANK YOU [/SIZE]

---

### Post by freebird54 on 2007-04-18
Not sure what you want to copy - but given a formatted disk in the drive:

```
cp */path/to/filename* fd0
```

should do the trick.  Haven't done much of that in a while!

---

### Post by 1972_OLDS_442 on 2007-04-18
Thanks all of y'all all my problems are solved. Now I just need to get a bigger HDD so I can install Ubuntu 6.10 then upgrade to Fiesty :)

---

### Post by freebird54 on 2007-04-18
It should not have to be *TOO* big - Linux is fairly comfortable on a medium sized system (mine runs fine in 10Gb alongside an XP of 30Gb).

---

