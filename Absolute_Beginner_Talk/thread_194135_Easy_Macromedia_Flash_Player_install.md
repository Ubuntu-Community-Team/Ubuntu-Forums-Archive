---
title: "Easy Macromedia Flash Player install ??"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-11
Ubuntu 6.0.6 Dapper, without having to execute 50 lines in the command line !
Java too.  Thanks ](*,)

---

### Post by taurus on 2006-06-11
Then use Automatix for all that and more!!!

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

---

### Post by aysiu on 2006-06-11
You want [Automatix](http://www.ubuntuforums.org/showthread.php?t=177646), then.

For the record, it's probably only about 5 or 6 lines of commands you'd have had to enter.

---

### Post by Drakkor on 2006-06-11
Thanks,hey aysiu, glad to see you back here, I had some problems installing,but got them worked out, after I found out that the burned cd was bad, 1 checksum error,
the md5 sums were right but just a bad burn,then I had it installed and first I got the Grub loader,but after booting to XP , I got an error 17 on Grub, so........ I decided to just put Ubuntu on my drive 2, so anyways it worked out !!    Cheers  :D

---

### Post by mdsmedia on 2006-06-11
I used the script promoted by aysiu (can't remember whose script) to upgrade Firefox yesterday. I ran Automatix (can't remember whether it was before or after) but Flash plugin for Firefox still isn't installed.

I went back to Automatix and chose just Firefox plugins (Flash included) and ran it....3 times...but Flash still doesn't work.

Is there something I'm missing?

---

### Post by aysiu on 2006-06-11
Well, let's find out.

Can you type these terminal commands? ```
cd /usr/lib/firefox/plugins
ls
``` You should see two files there... flashplayer.xpt and libflashplayer.so.

---

