---
title: "n00b help, trying to install a package"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Fnar on 2006-07-06
Not sure this is the right place to put this topic or not, but anyway.

  The situation comes down to this, I'm trying to get .wav files to play when I go to a web site, it keeps telling me I'm missing a plugin.  I looked for some information about it, and found a package I need (I think).  I'm trying to install it, but it doesn't seem to be working.

  I tried using 'apt-get install mozilla-plugin-vlc_0.8.5.debian-2_i386.deb', and got the following results:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-plugin-vlc_0.8.5.debian-2_i386.deb

  I tried the #ubuntu IRC channel, and someone suggested using dpkg instead, so I tried 'dpkg -i mozilla-plugin-vlc_0.8.5.debian-2_i386.deb' and I got the following results:

(Reading database ... 80170 files and directories currently installed.)
Preparing to replace mozilla-plugin-vlc 0.8.5.debian-2 (using mozilla-plugin-vlc_0.8.5.debian-2_i386.deb) ...
Unpacking replacement mozilla-plugin-vlc ...
dpkg: dependency problems prevent configuration of mozilla-plugin-vlc:
 mozilla-plugin-vlc depends on vlc (= 0.8.5.debian-2); however:
  Package vlc is not installed.
 mozilla-plugin-vlc depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 mozilla-plugin-vlc depends on libdbus-1-2 (>= 0.61); however:
  Version of libdbus-1-2 on system is 0.60-6ubuntu8.
 mozilla-plugin-vlc depends on libdvbpsi4; however:
  Package libdvbpsi4 is not installed.
 mozilla-plugin-vlc depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 mozilla-plugin-vlc depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing mozilla-plugin-vlc (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mozilla-plugin-vlc

If anybody has any idea what I"m doing wrong, or any better ideas of what to try, I'd really appreciate the help.  I'm very new to Ubuntu, and I have VERY limited experience with Linux otherwise, so I would appreciate any help, thanks.

---

### Post by tseliot on 2006-07-07
Moved the thread to a more appropriate Section

---

### Post by crystal on 2006-07-07
Have you checked out the [RestrictedFormats wiki page](https://help.ubuntu.com/community/RestrictedFormats)? Also, several of the experienced users here have suggested that aptitude be used instead of apt-get. You could read [Installing Software in Ubuntu](http://psychocats.net/ubuntu/installingsoftware.php).

---

### Post by richbarna on 2006-07-07
Or, just use synaptic.
If you want to use apt-get (I prefer aptitude, it's better at removing things), make sure that you have all the necessary repos enabled, and update apt-get/aptitude before searching/installing.

---

