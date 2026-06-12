---
title: "sources.list: is there a simple explanation?"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by tiris on 2006-01-17
I have been looking at the sources.list file and don't understand it. I have used
```
man sources.list
```
to find out information on it, but I don't think that I understand what the things at the end are for. Could someone tell me if I understand this right?
```

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates restricted
```

The two lines above are different repositories.
```

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy main multiverse
```
The two lines above have a duplicate which is main.

And finally.
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy multiverse
```
The two lines above can be replaced with the line below.
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted multiverse
```

Is this right? Or am I still not getting this stuff?

---

### Post by matthew on 2006-01-17
So far you are understanding things correctly.

Here are a couple of links to help you further...I'll look and see if I can find something else as well.

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
[https://wiki.ubuntu.com/SourcesList](https://wiki.ubuntu.com/SourcesList)
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by matthew on 2006-01-17
Okay, I'm back. Ubuntu is still pretty new and so we don't have as much full documentation as some older linux distros. The cool thing is that since Ubuntu is based on Debian we can use their vast wealth of documentation and it will generally apply. You just need to remember that the Ubuntu repositories and the Debian ones are not really compatible so don't use the Debian repos listed--use the ones in the psychocats link above. Anyway, here are some links to a Debian site that you will find helpful:

specific to sources.list
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-sources.list]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-sources.list")

the how-to apt page the above link is part of
[http://www.debian.org/doc/manuals/apt-howto/index.en.html]("http://www.debian.org/doc/manuals/apt-howto/index.en.html")

---

### Post by tiris on 2006-01-19
Thank you for the links...That clears things up a bit.

---

