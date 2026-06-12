---
title: "[SOLVED] Noob Question: Why cant we download folders?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by TidusBlade on 2007-12-03
Well I tried to find the answer but to no avail o.0 
Does anybody know why it is impossible to download folders, and only files? 
And if it's possible, how can you download entire folders from a remote server using SSH :)
Thanks! :)

---

### Post by lamalex on 2007-12-03
use scp.
```
scp -rv <directory to move> <target location>
```
and rtfm! man scp
lots of tips and tricks in there.

---

### Post by hyper_ch on 2007-12-03
> **Iamalex said:**
> and rtfm!

> 
**Answers like "STFU", "RTFM" or "Google it"** [COLOR="Red"]ARE NOT ACCEPTABLE UNDER ANY CIRCUMSTANCES[/COLOR] (II:8 ). Those answers will incur warnings, infractions or bans if a staff member feels it is appropriate. This is a cardinal rule of our community.
Taken from  ***Beginner Talk Rules*** --> [http://ubuntuforums.org/showthread.php?t=65842](http://ubuntuforums.org/showthread.php?t=65842)

---

### Post by TidusBlade on 2007-12-03
I was scp to do it, but I did it one file by one :P 
Thanks for the advice :) Downloading wont be a pain anymore :p
But seriously, take it easy, it's the **absolute beginner** talk section.

---

### Post by sethvath on 2007-12-03
To copy everything from a remote server you can use wget too. 

[http://wiki.dreamhost.com/Wget](http://wiki.dreamhost.com/Wget)

Look under the advanced usage. 
wget -r  [ftp://username:password@yourdomain.com/folder/*](ftp://username:password@yourdomain.com/folder/*)

---

### Post by TidusBlade on 2007-12-03
Thanks sethvath, Ill try using wget if scp dosen't work, since I got more experience with scp :)

---

### Post by sethvath on 2007-12-03
If you're planning on copying over secure files use scp, if not wget will do the job much faster. Personally I use wget to create a mirror of my media files hosted remotely.

---

### Post by TidusBlade on 2007-12-03
I dont mind speed, the server is very fast compared to my connection, and scp always went up to my max speed, I dont mind security, since the files arent very important.

---

### Post by The Cog on 2007-12-03
I find it easiest to use nautilus when using ssh to transfer files. Just type ssh://1.2.3.4 (or whatever the address is) into the address bar of nautilus. Then you can drag whole folders to another nautilus window.

---

