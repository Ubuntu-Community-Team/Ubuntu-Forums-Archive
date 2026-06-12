---
title: "Could not download all repository indexes..."
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Jareth on 2006-09-15
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)


Thats what I'm getting when I reload my synaptic package manager, any ideas anyone? I've done alot of searching but I can't find this specific prob.

Realy appreciate all your help btw.

---

### Post by Anduu on 2006-09-15
Could just be their server is down or busy...

---

### Post by Najand on 2006-09-15
> **Jareth said:**
> [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)

Thats what I'm getting when I reload my synaptic package manager, any ideas anyone? I've done alot of searching but I can't find this specific prob.

Realy appreciate all your help btw.


They don't work; edit your sources.list to comment them (put # sign before lines with above URLs to stop errors.

---

### Post by Jareth on 2006-09-15
Could you tell me where to begin with that?
I've searched for the file and it seems there are two 'menu.lst' on my system. Which one do I edit and how?

---

### Post by Anduu on 2006-09-15
Ummm that would be /etc/apt/sources.list...

I would wait a while before resorting to commenting them out.Give it a day or two and see if they come back up.

---

### Post by Najand on 2006-09-15
Oh, Sorry... It is souces.list
It is located at:
/etc/apt/sources.list

If you are using gnome you can also edit it using:
System -> Administration -> Software Properties
and unchecking the "http://antesis.freecontrib.org/mirro...y/Release.gpg" repositories.

---

### Post by Jareth on 2006-09-15
So thats not affecting any other new stuff in my package manager then, just stuff from those indexes. Any other stuff will still come through I mean.

(Sorry if I'm getting technical with all that 'stuff' talk:rolleyes: )

---

### Post by Najand on 2006-09-15
If you just edit the part about that particular repository, it will just effect that particular repository.

---

### Post by Jareth on 2006-09-15
Thats great stuff btw, I think I'll leave it for a day or two and if there's no change, I'll unselect it. I think I saw something which refered to easy ubuntu, so think it might have been that.

Ta for all your help as usual and the lightning fast responses.=D>

---

### Post by Anduu on 2006-09-16
I am assuming you did not add those repos yourself.It is quite possible they are left over from EasyUbuntu.In which case you would be safe to remove/comment them.

---

### Post by Najand on 2006-09-16
EasyUbutnu is what all troubles starts from...

---

### Post by Jareth on 2006-09-17
Yeah, I think I'm quickly wanting to learn how to do everything manualy rather than these package instaler things.

---

### Post by DOD1951 on 2006-10-20
On hitting check in Update Manager I get this message below and have had this for a week now. It is followed by a warning message, see after the 2  http lines. Can anyones advise if I messed something up please.

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

---

