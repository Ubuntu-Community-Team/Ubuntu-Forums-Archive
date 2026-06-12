---
title: "Rebuilding?"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by IanWright on 2006-04-08
I'm trying to use something called Netem, within the iproute2 utilities. I've discovered there were a few bugs within the release I'm using (2004) and was told to "Rebuild iproute2 utilities from source".

I have no idea how to do this though, and would appreciate any help? eg:

- Where do I find the source?
- How do I rebuild (I've been shown how to use Make, but that doesn't install the netem functions, I still have the same old release. Also Make-Install doesn't appear to do anything).

Thanks very much!

Ian

---

### Post by IanWright on 2006-04-09
Anyone? Am I posting in the wrong section?

---

### Post by mlind on 2006-04-09
These instruction produce rebuilt debian packaged of current iproute available for
your distribution. If you're going to build it from other than debian sources, you
should follow instuctions at [http://linux-net.osdl.org/index.php/Iproute2](http://linux-net.osdl.org/index.php/Iproute2).



You're going to build iproute package, so create temporary directory for iproute2
build-time packages and go into that directory

```

mkdir -p ~/tmp/iproute
cd ~/tmp/iproute

```

Next, you must download build-time dependencies for iproute. 
```

sudo apt-get build-dep iproute

```

If you get errors about not finding the source package, you must enable src
repositories from /etc/apt/sources.list. just remove comment marker '#' from the
front of any deb-src definition. Remember to do *sudo apt-get update* if you
modify sources.list file.

Then download the actual source package and build it 
```

sudo apt-get source -b iproute

```

---

### Post by IanWright on 2006-04-10
Thanks for the help so far, just 2 things I need to ask about.

1) How do I actually build it? Is that using the Make command?

2) The files doing it that way, have the date 19/10/2004 which are a bit out of date, I need to get the latest files which are much newer than this... How do I go about getting those?

---

### Post by IanWright on 2006-04-10
Ok, I've looked at apt-get and realised the first question was rather silly, and that it builds it already using the command, so I'll aplogise now for being dumb! 

I do however get these lines, which if I'm not mistaken means it can't build it:

dpkg-deb: building package `iproute' in `../iproute_20041019-3ubuntu2_i386.deb'.
dpkg-deb: building package `iproute-dev' in `../iproute-dev_20041019-3ubuntu2_i386.deb'.
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)

---

### Post by mlind on 2006-04-10
[QUOTE=IanWright]Ok, I've looked at apt-get and realised the first question was rather silly, and that it builds it already using the command, so I'll aplogise now for being dumb! 

I do however get these lines, which if I'm not mistaken means it can't build it:

dpkg-deb: building package `iproute' in `../iproute_20041019-3ubuntu2_i386.deb'.
dpkg-deb: building package `iproute-dev' in `../iproute-dev_20041019-3ubuntu2_i386.deb'.
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)[/QUOTE]

You need to enable source repositories from /etc/apt/sources.list. I just tried
to build iproute and it worked out fine. Problem is that this version is marked
as iproute-20041019, so is it too old aswell?

---

### Post by IanWright on 2006-04-10
Hey mlind, thanks for the help.

I've managed to get something working with a little help from a friend, I've downloaded and compiled the 2006 source I needed within iproute2 and I'm just not installing it, so running it directly from the folder :)

Thanks for your help though, it got me most of the way

---

