---
title: "Missing Library file"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2006-11-24
I am trying to get freebob to work which is a driver for firewire sound devices.  I have waded through the dependencies, or at least I thought I had, but I cannot overcome this error when using ./configure.

> 
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBXML_CFLAGS
and LIBXML_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

root@chase-desktopm:/home/chase/Desktop/libfreebob-1.0.0# 


I have a few basic questions, I installed what appears to be libxml2_2.6.27, could it not be recognizing this newer version?  I searched for the older version anywhere on the web with no luck.   Also, how can I find where these library files are installed so I can check manually?  What is PKG_CONFIG_PATH?  I am really reaching my witts end about this.  I feel like maybe this tool is just beyond my user level.

---

### Post by taurus on 2006-11-24
If you build something from sources, changes are you also need to developing packages.  Therefore, use synaptic and see if you can find something like libxml-dev and install it...

---

### Post by Rush_898 on 2006-11-24
> **taurus said:**
> If you build something from sources, changes are you also need to developing packages.  Therefore, use synaptic and see if you can find something like libxml-dev and install it...


OK, I tried this but I got the same thing again.  the -dev wasn't installed but it didn't fix it either.

---

### Post by taurus on 2006-11-24
Did you or did you not install libxml-dev before you run the ./configure again?

---

### Post by po0f on 2006-11-24
[libxml-dev](http://packages.ubuntu.com/edgy/libdevel/libxml-dev) != [libxml2-dev](http://packages.ubuntu.com/edgy/libdevel/libxml2-dev)

Try installing the latter.

---

### Post by Rush_898 on 2006-11-24
> **taurus said:**
> Did you or did you not install libxml-dev before you run the ./configure again?

Sorry I wasn't clear, I did install libxml-dev and tried to run ./configure and it still gave me the same thing.

---

### Post by Rush_898 on 2006-11-24
> **po0f said:**
> [libxml-dev](http://packages.ubuntu.com/edgy/libdevel/libxml-dev) != [libxml2-dev](http://packages.ubuntu.com/edgy/libdevel/libxml2-dev)

Try installing the latter.

OK, when I try to install that through synaptic I get...

> libxml2-dev:
  Depends: libxml2 (=2.6.26.dfsg-2ubuntu4) but 2.6.27.dfsg-1 is to be installed



I am on Edgy.  Not sure what this means.

---

### Post by po0f on 2006-11-24
Rush_898,

Is this after a `sudo aptitude update && sudo aptitude install libxml2-dev`?

---

### Post by Rush_898 on 2006-11-24
> **po0f said:**
> Rush_898,

Is this after a `sudo aptitude update && sudo aptitude install libxml2-dev`?

Wow, excellent, thanks!  I know apt-get and apt-get install but what is aptitude?  Is there somewhere I can read about the various ways to get programs?  When I tried through synaptic it was stuck but this method gave me the option to downgrade on lib file version to make compatible, that seems much more useful.  Thanks again!

---

