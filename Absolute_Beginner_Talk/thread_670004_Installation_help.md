---
title: "Installation help?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-01-17
I'm trying to install something called Cinelerra for video editing.

Here's the website where I've found the packages I need:
[http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=428973](http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=428973)

Will someone please explain how I'm supposed to install this? I tried to follow a page called "How to Install Anything in Ubuntu," but apparently when they say "anything," they actually mean, "nothing."

I have downloaded "cinelerra-2.1-src.tar.bz2" and extracted it into a file on my HD. That's as far as I can get.

Installation is the one giant, glowing, throbbing deficit with Ubuntu (and I do mean one - I love this OS otherwise). I am SO tired of finding a program I want, discovering that it's impossible to install, and throwing up my hands and deciding to live without it. I so badly wish this process was easier!

---

### Post by mikewhatever on 2008-01-17
Take a look here --> [http://ubuntuforums.org/showthread.php?t=285199](http://ubuntuforums.org/showthread.php?t=285199).

If you must install from source, the web is full of guides. All you need to do is type 'ubuntu install from source' in the search field. 
Here's one --> [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
Here are all of them --> [http://www.google.co.il/search?q=ubuntu+install+from+source&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+install+from+source&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by sumguy231 on 2008-01-17
The Cinelerra website has Ubuntu Gutsy packages for 2.1svn versions. You might find that quite easier than compiling it yourself:
[http://cv.cinelerra.org/getting_cinelerra.php#gutsy](http://cv.cinelerra.org/getting_cinelerra.php#gutsy)

---

### Post by Casual Fan on 2008-01-17
It's not an Ubuntu thing, it's a Linux thing. Ubuntu really does a great job with adding software. Anyway, that's a separate rant. Do this:

Open system>administration>software sources.
Click on Third-party software tab.
Click on add.
Enter this into the box:

```
deb http://giss.tv/~vale/ubuntu32 ./
```

(This is a repository listed in the link by the previous poster.)

Click on add source. Click close.
Synaptic will want to refresh the software sources; click ok and let it.

Then go to system>administration>Syanaptic Package Manager. Search for Cinelerra. It should come up. Right click on it, select mark for installation, click on apply, and go from there.

---

