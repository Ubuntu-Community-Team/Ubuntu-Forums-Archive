---
title: "How do I install firefox?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by chapmc on 2006-11-04
I'm a complete newbie.  I have downloaded firefox 2 and get a box firefox-2.0.tar.gz..   What is it wanting me to do and how do I install it?  I'm sure there are instructions somewhere but I haven't found them.

Thanks.

---

### Post by bsussman on 2006-11-04
You are installing a version not integrated with pre-6.10 so the usual use of the automatic tools is not going to work.

[http://www.mozilla.org/support/firefox/faq](http://www.mozilla.org/support/firefox/faq) has instructions

---

### Post by DOD1951 on 2006-11-04
Try this [http://www.ubuntuforums.org/showthre...ight=firefox+2]("http://www.ubuntuforums.org/showthre...ight=firefox+2")

---

### Post by quux on 2006-11-04
You can just extract the archive by e.g.

(1) opening a console window
(2) do a "tar xvzf firefox-2.0.tar.gz"
(2*) maybe you want to move the firefox directory to another location, e.g. "/opt" by doing a "mv firefox /opt"
(3) "cd" into the firefox directory and start firefox by
(4) "./firefox"

Alternatively you could use the archive utility of your desktop environment ("ark" in KDE, "file-roller" in GNOME, and "xarchiver" in XFCE) to extract the archive.

---

### Post by taurus on 2006-11-04
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by chapmc on 2006-11-04
Thanks for the replys.  Since I don't understand what I would be doing I am going to wait until ubuntu releases the new version in an update.

Thanks....

---

### Post by whiterabbit on 2006-11-04
Which version of Ubuntu are you running, chapmc?

---

### Post by bsussman on 2006-11-04
> **chapmc said:**
> Thanks for the replys.  Since I don't understand what I would be doing I am going to wait until ubuntu releases the new version in an update.

Thanks....
Since the repository versions are supposedly reliable with the app mix in the repository, that is usually a good idea.

But someday you will want to install something outside of the standard,  The commands in this install are all very standard and worth  learning.

in a terminal, 'man <command> will often give you standard documentation and you can ask questions about details.

tar unpacks the standard unix 'files packed into one' file.
mv moves files.

---

### Post by PapaWiskas on 2006-11-04
> **taurus said:**
> [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Dang....worked like a charm...

---

### Post by esaym on 2006-11-04
hehe: [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm)


if you want the desktop icon you will have to copy it from the default install location of /usr/share/applications/swiftfox.desktop and copy it over to /home/user/desktop


:-D

---

