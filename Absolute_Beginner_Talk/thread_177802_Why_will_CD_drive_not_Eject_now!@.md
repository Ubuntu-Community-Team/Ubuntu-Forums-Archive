---
title: "Why will CD drive not Eject now!@"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2006-05-16
Alright went to start playing with music.

 MP3s....nope wont play.....(im learning about that now.......)

But in the mean time, I decided to pop in a burned disc(burned from nero on my windows machine).

Pop that in, nothing...says blank disc.

Now i go to eject, and nothing! The cd drive will not open. With the software 'eject' or the actual open/close on the drive itself.

What the hell happened? Is this something i did? Do i have really bad luck and happened to have my cd die?

What the heck!

---

### Post by xXx 0wn3d xXx on 2006-05-16
[QUOTE=CloudyHaze]Alright went to start playing with music.

 MP3s....nope wont play.....(im learning about that now.......)

But in the mean time, I decided to pop in a burned disc(burned from nero on my windows machine).

Pop that in, nothing...says blank disc.

Now i go to eject, and nothing! The cd drive will not open. With the software 'eject' or the actual open/close on the drive itself.

What the hell happened? Is this something i did? Do i have really bad luck and happened to have my cd die?

What the heck![/QUOTE]
Try running the eject option in [ Automatix ](http://ubuntuforums.org/showthread.php?t=138405) That should fix the problem. After installing, Automatix can be launched by going under Applications > System Tools > Automatix.

---

### Post by bluevoodoo1 on 2006-05-16
[QUOTE=CloudyHaze]Alright went to start playing with music.

 MP3s....nope wont play.....(im learning about that now.......)

[/QUOTE]


Check out this post about MP3 help...
[http://ubuntuforums.org/showthread.php?t=177801](http://ubuntuforums.org/showthread.php?t=177801)

---

### Post by CloudyHaze on 2006-05-16
ok..... used Automatix.  Pretty nifty,...ended up adding a bunch of stuff :)

Plus MP3 now plays.

Now im starting to think maybe something is wrong with cd drive.

When i double click on it(under file browser) I get this error:

     unable to mount volume. there is probably no media in the device.:
  Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is             ignored 
mount: No medium found
Error: could not execute pmount


any other ideas???? im about to just pry the damn thing open !!

---

### Post by bluevoodoo1 on 2006-05-16
Don't pry it open!!

Open a terminal and type...

```
umount /dev/cdrom
```

(or it might also be... umount /dev/cdrom0)

This should unmount your drive so that you can open it.

---

### Post by CloudyHaze on 2006-05-16
Ok..... got it to eject after another restart.


Ok, now a question about the things i added with Automatix.

What if i accidently loaded things twice? 

As in, i chose the debian menu. It has alot of what i already had under various applications sub menus.  Are things really on my system twice? or just icons for the same program in different places? can i just get rid of duplicate icons under the app>debian menu?

Also, a burned music CD still is not recognized for some reason. MP3 is.

hehe thanks for all the help people....i'll get this yet

---

### Post by bluevoodoo1 on 2006-05-17
you can edit your menus with...

```
smeg
```

There you can uncheck programs that might have been listed twice.

---

