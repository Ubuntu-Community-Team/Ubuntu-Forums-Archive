---
title: "need help"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-04-20
need to know how and where to download these files libstdc++-libc6.2-2.so.3

---

### Post by Sef on 2006-04-20
For libstdc++, open a terminal and type this:  sudo apt-get install libstdc++

You can try: sudo apt-get install libc6.2-2.so.3

---

### Post by netkid91 on 2006-04-20
[QUOTE=ice.man]need to know how and where to download these files libstdc++-libc6.2-2.so.3[/QUOTE]
Why do you need them, what are you trying to do.  A better explanation is needed, and your topic title does us no good either.

---

### Post by ice.man on 2006-04-20
it is for a game i have downloaded for linux [http://www.racer.nl/](http://www.racer.nl/)

---

### Post by krusbjorn on 2006-04-20
[QUOTE=ice.man]need to know how and where to download these files libstdc++-libc6.2-2.so.3[/QUOTE]

Your best bet is probably to search for "libstdc" in Synaptic and install whatever package that fits the version number. I looked through a couple of them, but I didnt see the file you are looking for. Worth a try anyways.

[QUOTE=netkid91]Why do you need them, what are you trying to do.  A better explanation is needed, and your topic title does us no good either.[/QUOTE]
Sorry if I'm misinterpreting you, but sounding arrogant doesnt do us any good, either.

---

### Post by netkid91 on 2006-04-20
```

sudo apt-get install libstc++6

```
Make sure the universe repo's are enabled.

---

### Post by Mustard on 2006-04-20
Using apt-cache search I found this list.  I would assume you need the version 6 -dev package, libstdc++6-dev
```
mustard@slave:~$ apt-cache search libstdc++
gccchecker - Memory access debugger for C language development
lib64stdc++6 - The GNU Standard C++ Library v3 (64bit)
lib64stdc++6-4.0-dbg - The GNU Standard C++ Library v3 (debugging files)
libg++2.8.1.3-dbg - The GNU C++ extension library - debugging files
libstdc++2.10-dbg - The GNU stdc++ library (debugging files)
libstdc++2.10-dev - The GNU stdc++ library (development files)
libstdc++2.10-glibc2.2 - The GNU stdc++ library
libstdc++5-3.3-pic - The GNU Standard C++ Library v3 (shared library subset kit)libstdc++6-4.0-pic - The GNU Standard C++ Library v3 (shared library subset kit)libgmp3-dev - Multiprecision arithmetic library developers tools
libstdc++5 - The GNU Standard C++ Library v3
libstdc++5-3.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++5-3.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++5-3.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6 - The GNU Standard C++ Library v3
libstdc++6-4.0-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.0-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.0-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-pic - The GNU Standard C++ Library v3 (shared library subset kit)

```

To install the package..

```
sudo apt-get install libstdc++6-dev
```

---

### Post by netkid91 on 2006-04-20
[quote=krusbjorn]Your best bet is probably to search for "libstdc" in Synaptic and install whatever package that fits the version number. I looked through a couple of them, but I didnt see the file you are looking for. Worth a try anyways.


Sorry if I'm misinterpreting you, but sounding arrogant doesnt do us any good, either.[/quote]
Sorry, not trying to sound like a jerk.  But I (and many others) can't help without the whole story.  I'm a stickler on this stuff, otherwise I'm pretty nice.

---

### Post by ice.man on 2006-04-20
sudo apt-get install libstc++6
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstc++6


and yes universe repo's are enabled

---

### Post by krusbjorn on 2006-04-20
[QUOTE=ice.man]sudo apt-get install libstc++6
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstc++6


and yes universe repo's are enabled[/QUOTE]

It's libstdc++6 and libstdc++6-dev. I think you forgot the d :)

---

### Post by netkid91 on 2006-04-20
You misspelled it, it's libst**d**c++6.

---

### Post by ice.man on 2006-04-20
still no go what i mean is that it is still asking for those files still

---

### Post by Mustard on 2006-04-20
[QUOTE=ice.man]still no go what i mean is that it is still asking for those files still[/QUOTE]

"Still no go" is not really giving anyone a clear idea of what is going on.  We need to see what you typed in, with regards to installing the dependency, and what the error message was if it failed.

---

### Post by ice.man on 2006-04-20
./bin/racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

---

### Post by netkid91 on 2006-04-20
I'm out of ideas....Well I got other people I'm helping so I'll leave you guys to it.

---

### Post by Mustard on 2006-04-20
[QUOTE=ice.man]./bin/racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory[/QUOTE]

This means you need to install the dependency that has been mentioned earlier in this thread.

When I asked about the error message, I was more thinking of the error you recieved when you attempted to install the dependency libstdc++6-dev. :)  

I have no idea whether you have completed this process from your above posts.  If you got errors when installing this dependency, after correcting the spelling error you made the first time around you never mentioned them.  I'd love to help, but you have to at least cooperate and reciprocate in terms of giving more information than one line answers of an ambiguous and possibly irrelevant nature.

The libstdc++6-dev package exists.  If it failed to install, then you need to work out why it won't install first, before you proceed to trying to compile this program.  You can't move forward without first solving this issue.

---

### Post by Mustard on 2006-04-20
See if this will install

```
sudo apt-get install libstdc++2.10-glibc2.2
```

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libstdc%2B%2B-libc6.2-2.so.3&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libstdc%2B%2B-libc6.2-2.so.3&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

---

### Post by haocheng on 2006-05-11
This solved my problem, 
thanks a lot  :)

---

