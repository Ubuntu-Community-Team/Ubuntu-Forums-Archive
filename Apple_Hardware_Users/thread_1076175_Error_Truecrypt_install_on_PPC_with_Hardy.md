---
title: "Error Truecrypt install on PPC with Hardy"
date: 2009-02-21
forum: Apple Hardware Users
---

### Post by FaiSua on 2009-02-21
I Read this thread 
[http://ubuntuforums.org/showthread.php?p=6772341#post6772341](http://ubuntuforums.org/showthread.php?p=6772341#post6772341)
But the instructions didn't work for me and I would appreciate anyone elses insight in the problem. When I install TrueCrypt, I get an "error: Wrong Architecture i386" message.

"

---

### Post by binbash on 2009-02-21
go to [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

and select x86 if you are using 32 bit.If you are using 64 bit select x64.

then click download.Untar the downloaded file and give chmod +x filename to the file you extracted.After that run the file via ./filename .Select create a deb option.A deb will be created at /tmp . go to /tmp folder and install the deb.

---

### Post by cyberdork33 on 2009-02-21
> **binbash said:**
> go to [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

and select x86 if you are using 32 bit.If you are using 64 bit select x64.

then click download.Untar the downloaded file and give chmod +x filename to the file you extracted.After that run the file via ./filename .Select create a deb option.A deb will be created at /tmp . go to /tmp folder and install the deb.
the problem is that he has neither. He is using PowerPC.

I replied to your other post here:
[http://ubuntuforums.org/showpost.php?p=6774093&postcount=6](http://ubuntuforums.org/showpost.php?p=6774093&postcount=6)

---

### Post by FaiSua on 2009-02-21
Still can't figure this out. Hmmm. I tried to follow the directions from estranged1977's post but I was unsuccessful. Maybe it's my lack of knowledge of code but I would like get this working, I love my truecrypt volumes!I posted the error codes here:
[http://ubuntuforums.org/showthread.php?t=889214](http://ubuntuforums.org/showthread.php?t=889214)

---

