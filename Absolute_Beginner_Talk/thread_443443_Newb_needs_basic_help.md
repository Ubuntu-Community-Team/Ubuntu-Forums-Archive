---
title: "Newb needs basic help"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2007-05-14
I am three weeks into ubuntu now and I have yet to have ANY success with tarballs and compiling might yet be the distant future for me.  I'm trying to get listen 0.5 installed.  Can someone please help?

Downloaded listen-0.5.tar.bz2 to desktop.

```

cd Desktop

tar zxvpf listen-0.5.tar.bz2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

```

One thread suggested this error means bad tarball. is it so?

---

### Post by taurus on 2007-05-14
```
tar xvjf listen-0.5.tar.bz2
```

---

### Post by TheRingmaster on 2007-05-14
listen music player is in the repos. Just go to the applications menu --> and hit add/remove. Then search for Listen. It is in there.

---

### Post by cbs30954 on 2007-05-14
Perhaps I'm confused. I'm new to Xubuntu (as of a couple of days ago), so forgive me if I'm wrong. But that .bz2 on the end tells me that the file is zipped, and you need something to unzip it before you use it.

---

### Post by heimo on 2007-05-14
Listen is available using Synaptic Package Manager (System->Administration->Synaptic Package Manager). But it's in Universe part of repository, so you'll need to add it first:
[https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)

---

### Post by il-luzhin on 2007-05-14
got it from the repos.  Thanks.

---

### Post by Skrynesaver on 2007-05-14
There are several different zipping algorithms, from PKzip,(winzip) stuffit(Mac) and in the unix world the two most common are .gz (gnuzip) and .bz2 (The Burrows Wheelock algotihm)
The tar command can unzip these before extracting from the archive thus
```
tar -x**z**f file.tar.gz
tar -xjz file.tar.bz2
```

---

### Post by il-luzhin on 2007-05-14
If anyone is familiar with Listen...

I'm using a media enabled router so my media files are connected directly to my router via USB-HDD (router has USB connection, I've never had problems with XP SP2 using this method).  I can't navigate to my files; though if I go to the web radio option and enter

```

ftp://192.168.1.1/NTFS_1/Music/song info

```

I can play single songs.

Any chance someone can help me build a library from music on a 'server' of this type using listen?

---

