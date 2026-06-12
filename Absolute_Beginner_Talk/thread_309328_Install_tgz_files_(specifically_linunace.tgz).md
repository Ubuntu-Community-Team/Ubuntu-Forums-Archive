---
title: "Install tgz files (specifically linunace.tgz)"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Quicky on 2006-11-29
I've just downloaded the latest version of [unace for linux]("http://www.winace.com/") (linunace.tgz), an archiving tool for decompressing .ace files, but realised I have no idea how to install it. Can anybody point me in the right direction?

Also realised that I've been linux native for eight months now, and probably should know how to do this by now.

Thanks

---

### Post by KingBahamut on 2006-11-29
This guide adequately explains everything youll need to know. 

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by dwblas on 2006-11-29
untar it with tar -xvzf ./unace.tgz (assuming you are already in the dir that has unace).  Look at the output to find the dir name that it was extracted to, probably unace-something.  In that dir ther should be a README and/or INSTALL file that will give you specific directions.  How it is installed is language specific and depends on whether you have something that can be executed or not.

---

### Post by Quicky on 2006-11-29
Thanks for the replies - the installation link should help me in the future.

FYI, in this instance the tgz file only contained a licence text file and an executable entitled 'unace'. I simply copied that to the /usr/bin/ folder (which is where the older version in the repositories was installed to), tried to unace my .ace file, and it extracted it without issue.

Since it works OK, I take it that I have 'installed' the file correctly?

---

### Post by John.Michael.Kane on 2006-11-29
This may be of use as well [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by steve.horsley on 2006-11-29
There's an unace package in the Ubuntu Universe repo.

---

### Post by dwblas on 2006-11-29
Next time, move the original to somewhere like /home.  A new version does not always install and/or work.

---

