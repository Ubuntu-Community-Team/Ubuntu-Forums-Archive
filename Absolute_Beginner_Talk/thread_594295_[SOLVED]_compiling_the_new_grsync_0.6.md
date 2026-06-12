---
title: "[SOLVED] compiling the new grsync 0.6"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by joshzam on 2007-10-27
Howdy all,

I've currently got the grsync 0.5.2 version from the repositories installed on my system. I see that the new version 0.6 has a major fix allowing "a Windows compatibility option (which enables a workaround for the 2-seconds time resolution of FAT)". Problem is: the new version is not in the repos.

I've downloaded the new source (grsync-0.6.tar.gz) from the web ([http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)) and tried to follow the included INSTALL file but it's a bit convoluted and outdated and I'm not getting the results that are described in the instructions. Can anyone who has compiled/installed this new version maybe walk me through the proper steps?

Thanks in advance.

---

### Post by taurus on 2007-10-27
It's probably a good idea to remove the old version from your machine _before_ you decide to compile and install the latest version.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf grsync-0.6.tar.gz
cd grsync-0.6
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure
make
sudo make checkinstall
```

---

### Post by joshzam on 2007-10-27
Thanks, taurus! That's exactly the hand holding I was looking for.

But...

I made it up to the "./configure" step without problems. I noticed there was an error thrown up here:
> checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found

I pretended not to see that and went ahead and entered "make" and got this:
> make: *** No targets specified and no makefile found.  Stop.

Looks like I'm missing gtk+-2.0. OK. I went to the Synaptic Package Manager and searched for "gtk" and then "gtk+" and then "gtk+-2.0" and had no idea which packages I was missing.

There was another message in the Terminal that said:
> Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
but I don't think ignoring the problem is the answer. Or is it?

Any ideas?

---

### Post by taurus on 2007-10-27
Search for libgtk and libgtk-dev with synaptic.  You probably need both packages to compile it.

p.s.  No need to run other commands once there are error messages.  You need to fix those first before you can move to the next command.

---

### Post by joshzam on 2007-10-27
It's people like you, taurus, that make this community great.

But...

I found that I had the libgtk package already installed but not the dev, so I installed it. This allowed me to successfully complete "./configure" and "make". I think. No errors were thrown back but when I tried to "sudo make checkinstall" I got:
> make: *** No rule to make target `checkinstall'.  Stop.
I feel like I'm so close. The obvious question I have now is, where do I go from here?

Other questions I anticipate are:
Once successfully installed, where will grsync be installed?
Will an icon automatically appear in the Applications list?
And for my own education, what did these commands do:
sudo aptitude update
sudo aptitude install build-essential checkinstall

Thanks again

---

### Post by taurus on 2007-10-27
In that case, just do it the old fashion way.

```
sudo make install
```

It should be in /usr/local/bin so if it's in your path, you can just run it anywhere you want.

---

### Post by joshzam on 2007-10-28
Sometimes the old fashioned ways are the best. Worked like a charm. And I was happy to find the app icon in the Applications list.

Thanks again for all your help. I'm learning more everyday.

---

