---
title: "How to create repositories cd??"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by kooolrock on 2008-02-22
when i'm installing ubuntu in my college systems, i hv to setup and dwnld codecs for lot of time. i want to know How to create repositories cd?? ( which will contain mp3, mpeg, avi codecs and vlc). this will also be useful for my friends who don't hv net ?

---

### Post by OffAxis on 2008-02-22
If you're just using a few codecs you can download the .deb packages onto a known location (CD, USB, network folder, etc) and then install with
```
sudo dpkg -iR /path/to/folder
```

-i = install
R = Recursive. Any .deb file in that folder or sub-folder will be installed.

If you're looking for something more substantial (like a mirrored repository) try this out:

[http://www.howtoforge.com/local_debian_ubuntu_mirror]("http://www.howtoforge.com/local_debian_ubuntu_mirror")

---

### Post by bodhi.zazen on 2008-02-22
There is also AptOnCd

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by kooolrock on 2008-02-22
> **OffAxis said:**
> If you're just using a few codecs you can download the .deb packages onto a known location (CD, USB, network folder, etc) and then install with
```
sudo dpkg -iR /path/to/folder
```

-i = install
R = Recursive. Any .deb file in that folder or sub-folder will be installed.

If you're looking for something more substantial (like a mirrored repository) try this out:

[http://www.howtoforge.com/local_debian_ubuntu_mirror]("http://www.howtoforge.com/local_debian_ubuntu_mirror")
i appreciate ur concern, but this outrageously difficult for a beginner like me.

>"the main, restricted, and universe sections of Ubuntu Edgy Eft which took about >[COLOR="Red"]25GB [/COLOR]of hard disk space and about [COLOR="Red"]6 hours of download[/COLOR] time on a [COLOR="Red"]16MBit DSL line[/COLOR]."
No way. that's tooo much.

>all needed packages can be downloaded over the fast LAN connection
i don't how to setup LAN connection

What about offline users???

---

### Post by kooolrock on 2008-02-22
> **bodhi.zazen said:**
> There is also AptOnCd

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
thx. u hv solve my problem!!! bodhi.zazen ROCKSSS!!

---

