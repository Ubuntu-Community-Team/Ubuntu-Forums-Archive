---
title: "BF2142 server will not install...."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by MianoSM on 2007-11-29
I have used the search feature, and googled as well - and have only found foreign web pages (as in not in english), that have any information on this.

I have used wget to download the bf2142-linuxded-1.08.21.0-installer.sh from three different sources.

I then chmod 755 the file, and attempt to run it using ./bf2142*

It then lets me know that the MD5 checksums are different and exits out.

Okay, no biggy - I removed the MD5 check altogether and then get an error stating:

```

gaming@bhngaming1:/bf2142$ sh bf2142-linuxded-1.08.21.0-installer.sh
Verifying archive integrity...No md5 Checksums error message here. ; )
 All good.
Uncompressing Battlefield 2142 Dedicated Linux Server 1.08.21.0
gzip: stdin: not in gzip format

bf2142-linuxded-1.08.21.0-installer.sh: line 321: ./license.sh: No such file or directory

```

Any help or guidance would be greatly appreciated! : )

---

### Post by civic_si on 2007-11-29
Sounds like a corrupt download.

---

### Post by MianoSM on 2007-11-29
> **civic_si said:**
> Sounds like a corrupt download.

That was my thought too, but I can't imagine that three times the file was corrupted (I've downloaded from 3 different sites all have the same size *.sh file). 

BF2 was not a problem, BF2142 is impossible at the moment.

---

### Post by civic_si on 2007-11-29
run a md5 check on the downloaded file.

run 

md5sum "name of file" 

the site where you downloaded the installer from should have the md5 hash so you can check to make sure its good.

---

