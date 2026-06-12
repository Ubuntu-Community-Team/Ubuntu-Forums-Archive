---
title: "&quot;Enabling Multimedia ... STICKY&quot; directions give error"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by aamir9 on 2007-05-25
Hi all!  

I'm trying to DVD playback set up with menus, subtitles options, etc.

I'm trying to follow directions from here:
The "Sticky Thread Sticky: Enabling Multimedia in Feisty (HOW-TO)"
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

In Applications Bar --->  Add/Remove ---> Other, i can find "Ubuntu restricted extras", but when I try to enable it, i receive the following error:

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

any help will be much appreciated!  (first time linux/ubuntu user!  enjoying and learning slowly... this is my first ubuntu post, since all previous troubles were solved by previous posters...)

---

### Post by Bachstelze on 2007-05-25
Try to do it from the command-line. At least, it will output more helpful error messages...

---

### Post by aamir9 on 2007-05-26
please hold my hand.

what should i type in terminal?  

...perhaps i'll try to learn to do that myself in the meantime...

---

### Post by aamir9 on 2007-05-26
when this is entered into command line:
sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

i get another error: "Segmentation fault (core dumped)"

---

### Post by Bachstelze on 2007-05-26
That's bad and there's nothing I can do about it, sorry. A segfault is roughly equivalent to a BSOD in Win.

---

