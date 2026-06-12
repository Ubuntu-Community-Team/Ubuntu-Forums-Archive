---
title: "Help! DVD playback not working on Feisty!"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by abyrne10 on 2007-05-25
I have just installed Ubuntu 7.04 (it's an as-yet untouched copy, except that I ran update manager and enabled desktop effects), but can't get it to play DVDs. When I put the disk in for the first time, Totem player popped up and told me it had to install the Gstreamer codecs, which I did. However, now when I try to play the DVD I get the error message "Could not read from resource." (I get the same error message on multiple, undamaged DVDs).

Can anyone help me sort this out?
Thanks

---

### Post by BHelts on 2007-05-25
try installing ubuntu restricted extras.  make sure you have all repositories enabled and
 ```
sudo aptitude install ubuntu-restricted-extras
```
see if that helps

---

### Post by abyrne10 on 2007-05-25
Thanks for your reply! I tried the restricted extras, but I don't know if all the repositories are activated...anyway I tried the DVD again and I get a new error message: "Could not open location; You may not have permission to open the file."

Any ideas?
Thanks

---

### Post by abyrne10 on 2007-05-25
Hang on I've fixed it; here's what I did: (taken from ubuntuguide.org)

sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install totem-xine

sudo aptitude install libdvdcss2

Thanks for your help anyway!

---

### Post by BHelts on 2007-05-25
good job!

---

