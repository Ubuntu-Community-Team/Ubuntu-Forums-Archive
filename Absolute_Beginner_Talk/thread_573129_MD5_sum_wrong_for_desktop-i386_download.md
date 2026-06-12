---
title: "MD5 sum wrong for desktop-i386 download"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by quincyjones on 2007-10-11
Hi, I've used 2 different md5 checksum programs ("winMd5Sum" and "md5") to check the md5 sum of the "ubuntu-7.04-desktop-i386" download that I got lastnight from:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
from the _South Africa Tenet mirror _option.
They give:
3b7d5b6de4eeb4a5cc54b43af4e6734e
which is apparently incorrect according to: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Should I redownload Ubuntu from a different server (don't really want to)? And if so then can someone please fix the one on the SA server!?

Thanks in advance

---

### Post by hyper_ch on 2007-10-11
I'd use torrent to download the ISOs... it's fast and I haven't had an md5 issue with those yet.

---

### Post by tszanon on 2007-10-11
> **quincyjones said:**
> Hi, I've used 2 different md5 checksum programs ("winMd5Sum" and "md5") to check the md5 sum of the "ubuntu-7.04-desktop-i386" download that I got lastnight from:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
from the _South Africa Tenet mirror _option.
They give:
3b7d5b6de4eeb4a5cc54b43af4e6734e
which is apparently incorrect according to: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Should I redownload Ubuntu from a different server (don't really want to)? And if so then can someone please fix the one on the SA server!?

Thanks in advance

Should you redownload it? Surely. From a different server? It's a good idea, since the file in that server may be corrupted. If it's the first time you downloaded it from that server, then probably just the download itself got corrupted. In this case, a new download from the same server should be fine.

But I second that suggestion above: use torrents, if you can.

---

### Post by SuperDuck on 2007-10-11
It probably wasn't the server - sometimes files just get goobered up in the download.  That's been my experience, at least.  I've downloaded an .iso and gotten a wrong checksum, and then downloaded it again from the same server and gotten one that checks out fine.  

Definitely don't burn it though, unless you want a coaster for your desk!

---

### Post by asmoore82 on 2007-10-11
I've _never_ been able to get a valid MD5sum calculation on M$ Windoze;
but when i move the same file to GNU/Linux and check it, it is fine.

copying and md5sum-ing the disc is one of the first things on every fresh Linux install;
it's a shiny new OS sanity check and makes sure my disc isnt' scratched yet...
```
$ dd if=/dev/cdrom | tee install-disk.iso | md5sum | tee install-disk.iso.md5
```

---

### Post by quincyjones on 2007-10-11
Thanks, I'll try download it again and see what happens...

---

### Post by maybeway36 on 2007-10-11
Nice use of pipes. :)

---

