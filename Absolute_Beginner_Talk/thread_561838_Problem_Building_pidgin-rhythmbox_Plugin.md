---
title: "Problem Building pidgin-rhythmbox Plugin"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by home-boi on 2007-09-28
Hi everyone,

I found this plugin, pidgin-rhythmbox-2.0 and thought it might be fun. When I try to build it, I get the following error: 

   checking pkg-config is at least version 0.9.0... yes
   checking for pidgin... configure: error: Package requirements (pidgin >= 2.0.0) were not met:

   No package 'pidgin' found

   Consider adjusting the PKG_CONFIG_PATH environment variable if you
   installed software in a non-standard prefix.

   Alternatively, you may set the environment variables pidgin_CFLAGS
   and pidgin_LIBS to avoid the need to call pkg-config.
   See the pkg-config man page for more details.

Pidgin 2.2.0 is installed on Feisty Fawn 7.0.4. I believe that I installed Pidgin from a .deb file. I tried searching, but the closet resolution that I think I found was in another language. Is there someone that can help me use the right settings?

I tried the following command.

   ./configure pidgin_LIBS =/usr/lib/pidgin (I used "find / -name pidgin" to find this directory)

Can someone help me with where pidgin-CFLAGS is? Since I'm a newbie, I've been using package installs (default settings)

---

### Post by Nano Geek on 2007-09-28
Try:```
sudo apt-get install pidgin-dev
``` and rerun ./configure.

---

### Post by home-boi on 2007-09-29
Thank you. Did the trick and I learned that I need to download the development packages. I was missing a bunch of libraries.

---

### Post by th3gh05t on 2007-10-27
How do we get this to show up in the profile once we have installed it?

---

### Post by blackdalek on 2007-11-05
> **th3gh05t said:**
> How do we get this to show up in the profile once we have installed it?

I've been trying to work that one out for months too.

Did anyone ever work it out? You're supposed to put %rb somewhere but I don't know where... other people just see that - "%rb" - instead of an actual song/artist.

---

