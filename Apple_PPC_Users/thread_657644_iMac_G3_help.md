---
title: "iMac G3 help"
date: 2008-01-03
forum: Apple PPC Users
---

### Post by thespottedelf on 2008-01-03
Ok i'm planning on going tfor this ubuntu install (downloading it right now).

What i'm shooting for is dual boating 9.2 and ubuntu.  Now i'm a total nub when it comes to linux, but i'm a total geek and i'm going balls to the walls on this :guitar:


So what would you guys suggest?  I plan on following the one tutorial about this.  ([http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)) Just can't wait to say i r 1337 w00t :D

---

### Post by thespottedelf on 2008-01-03
[img]http://img.skitch.com/20080104-ctrxeg6isq6m7qqmbjs5eutr6m.jpg[/img]

that is the one i d/led is that the right one? and if so what am i supposted to do to make it a bootable disc?

---

### Post by thespottedelf on 2008-01-03
ok, first attempt to boot of disc has failed.... ok consaulting guide once again...

---

### Post by thespottedelf on 2008-01-03
seem to be having an odd issue.... it doesn't want to boot off the disc.  I boot up holding down c and it spits back out at me.


btw the link above is wrong

This is what i am following [http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)

---

### Post by thespottedelf on 2008-01-04
ok... some updates... i'm going to leave this on osx 10.2.8  and try to install ubuntu on a different partition.  I found out that my orignal install disc was burned improporly.  I might go to bed now and work on this tomorrow. Idk it depends when my new burn is done

---

### Post by thespottedelf on 2008-01-04
disc burning done checking now to see if it works

---

### Post by thespottedelf on 2008-01-04
it works... i'm in the command line now. 

but i'm stuck at "Look in the file for the "Modules" Section in there you should have one that says

Load "dri""

can't find the modules section

---

### Post by samden on 2008-01-04
Have you typed the command ```
sudo nano /etc/X11/xorg.conf
``` correctly?

If you have typed it correctly, you should have opened a file that has lots of writing in it. Somewhere in this file, if you scroll down (by using the arrow keys) there will be a line saying 
```
Load "dri"
```

If you have typed it incorrectly, you may have opened a new blank file with no writing in it, in which case you won't have much luck finding the modules section!

Please clarify what you actually see on your screen.

---

### Post by thespottedelf on 2008-01-04
well i typed it in wrong then.  I got a blank screen.  I'll try again later, its school time :(

---

### Post by thespottedelf on 2008-01-04
just thought of something

Would it be better to partition in osx or ubuntu?

---

### Post by thespottedelf on 2008-01-04
i did the read file /etc/x11/xorg.conf and it said file not found.

i tried it as x.org.conf just to see but that didn't work either


so how do i do this??

---

### Post by thespottedelf on 2008-01-04
ok just typed it in again and it came up idk what i did lol

---

### Post by thespottedelf on 2008-01-04
i've run into another snag.....

i want to keep my osx install (since it is running fine) but i'm having a hard time disableing journaling... (following [http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960))

any ideas?

---

### Post by thespottedelf on 2008-01-04
ok i decided just to go with linux... i can always put osx back on

---

### Post by thespottedelf on 2008-01-04
its installing now gonna do homework until its done

---

### Post by thespottedelf on 2008-01-04
wow.... 1337 ubuntu 7.04 running perfectly on the imac... this is amazing... i'm waiting for the updates.

Thank you so much to those who wrote tutorials on how to install this it has helped so much.


Long live the Penguin!!!!

---

### Post by thespottedelf on 2008-01-05
are other people having problems updateing to 7.0.10?  i had 7.0.04 running fine, tried to update to 7.0.10 and now it just hangs... any ideas?

I think i might just set it to reinstall and go to bed... i havn't done too much other then install a couple apps...

---

