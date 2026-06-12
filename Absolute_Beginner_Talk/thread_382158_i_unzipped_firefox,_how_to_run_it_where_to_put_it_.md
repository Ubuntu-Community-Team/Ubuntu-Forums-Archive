---
title: "i unzipped firefox, how to run it? where to put it? like in what dir?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-03-11
Currently, I have FireFox 1.5.0.10 and I just went to firefox.com to download the last file. I got this file on my desktop.
firefox-2.0.0.2.tar.gz
on cmd line, i ran gzip then tar and suddenly i got a folder "firefox"

so i cd and ls the contents and i see this:

cloud@cloud:~/Desktop/firefox$ ls
browserconfig.properties  libfreebl3.chk   libsoftokn3.so                   removed-files
chrome                    libfreebl3.so    libssl3.so                       res
components                libmozjs.so      libxpcom_compat.so               run-mozilla.sh
defaults                  libnspr4.so      libxpcom_core.so                 searchplugins
dictionaries              libnss3.so       libxpcom.so                      updater
extensions                libnssckbi.so    libxpistub.so                    updater.ini
firefox                   libplc4.so       mozilla-xremote-client           xpicleanup
firefox-bin               libplds4.so      old-homepage-default.properties
greprefs                  libsmime3.so     plugins
icons                     libsoftokn3.chk  readme.txt

**** well anyways what am i supposed to do with this 'firefox' folder?

i see this on 'etc' folder
cloud@cloud:/etc/mozilla-firefox$ ls
mozilla-firefoxrc  pref  profile

please help me.

---

### Post by Native Dialect on 2007-03-11
Firefox should automatically update from the taskbar up top, but if not, have you tried using the Synaptic Manager to search for Firefox updates?

---

### Post by gotquestions on 2007-03-11
it didnt update my taskbar. i did not use Synaptic Manager (not sure how to). but i was thinking how to do this from cmd line :(

---

### Post by auraithx on 2007-03-11
must easier just going to System --> Administration --> Synaptic Package Manager.

---

### Post by gotquestions on 2007-03-11
> **auraithx said:**
> must easier just going to System --> Administration --> Synaptic Package Manager.

ok so i went there and sort by 'firefox'. i re-installed package firefox and clicked on that nice icon on my taskbar. it still shows the same version.

~still stuck

---

### Post by Bachstelze on 2007-03-11
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

