---
title: "install attempt: missing compiler??"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by wog on 2006-06-20
I'm trying to install freedroid. It's apparently not in Synaptic, at least not with the repositories I have.

So I download it from sourceforge and open it up. And I get this...
 ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking how to create a ustar tar archive... gnutar
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH

The weird part is, I went into Synaptic to see what's installed, and I find gcc base for version 3.3 and 4.0 are both installed. So what does the configure file actually want and where do I put it?

---

### Post by underdog on 2006-06-20
try
```

sudo apt-get install build-essential

```

---

### Post by x64Jimbo on 2006-06-20
I ran sudo apt-get install gcc g++ but both are probably acceptable

---

### Post by wog on 2006-06-21
[QUOTE=underdog]try
```

sudo apt-get install build-essential

```[/QUOTE]

Oh now that's bright. :)

Thank you! :)

Oh wait. Now it's complaining about missing SDL libraries. What are SDL libraries? I guess whatever they are, they aren't build-essentials, are they?

---

### Post by wog on 2006-06-21
[QUOTE=x64Jimbo]I ran sudo apt-get install gcc g++ but both are probably acceptable[/QUOTE]

So you're saying that just because Synaptic thinks I have gcc doesn't neccessarily mean I have either enough of gcc or at least the right parts for this configure script?

---

### Post by sas on 2006-06-21
Freedroid is in the Universe repository

sdl libraries are programs to ease games programming they abstract away some of the sound/graphics/networking libraries. There are a few of them so I don't know which you need, you may want to try searching in synaptic for "libsdl" and installing what it gives you.

---

### Post by underdog on 2006-06-21
Package managers blow. Use aptitude or apt-get.

---

### Post by wog on 2006-06-21
[QUOTE=underdog]Package managers blow. Use aptitude or apt-get.[/QUOTE]

Where can I find a list of available files if I go the aptitude or apt-get approach? That's precisely the reason I tend to use the package managers.

---

### Post by %hMa@?b&lt;C on 2006-06-21
sudo apt-cache search *name or description*

---

### Post by wog on 2006-06-21
[QUOTE=jeffc313]sudo apt-cache search *name or description*[/QUOTE]

Oooo! Thank you! :)

---

### Post by wog on 2006-06-21
[QUOTE=sas]Freedroid is in the Universe repository

sdl libraries are programs to ease games programming they abstract away some of the sound/graphics/networking libraries. There are a few of them so I don't know which you need, you may want to try searching in synaptic for "libsdl" and installing what it gives you.[/QUOTE]

I checked, and I was wrong. It wasn't freedroid. It was freedroidRPG, which is apparently not in the repositories anywhere. 

I installed libsdl1.2-dev and that seems to have fixed its little red wagon, but now it's asking for libjpeg, and according to apt-get I already have libjpeg62 installed. Do I just go down the line and try the configure file after each one until I find what it wants, or is there a better way?

---

### Post by sas on 2006-06-22
I'm afraid there's not really a better way, this is why package management exists. If you're lucky you'll find a 3rd party .deb package, or a .rpm which you can convert to .deb with alien. 

In this case you may not have the right libjpeg* package (try libjpeg62-dev) installed or the configure script may be specifically looking for an older or newer version.

[QUOTE=underdog]Package managers blow. Use aptitude or apt-get.[/QUOTE]
From the first line of the APT how to: "This document intends to provide the user with a good understanding of the workings of the Debian package management utility, APT."

Just because something isn't a graphical utility, doesn't mean it's not a package manager.

---

### Post by wog on 2006-06-22
libjpeg62-dev seemed to work. after that it was just a neverending stream of other libs it wanted, but without announcing in advance that it wanted them. And then it finally installed with warnings, and then it installed without complaints. 

I feel like a did something, although I'm not sure what. :)

Thank you! :)

---

### Post by wog on 2006-06-22
Wait.

First it's ./configure
Then it's make
Then it's sudo make install

So how do I now put this program in the menus so I can run it from there instead of the command line?

---

