---
title: "[SOLVED] Multiple Linux question..."
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-26
If I made /home a different partition and I want to install more than one Linux OS, could both of them use that /home partition?

---

### Post by dasunst3r on 2007-12-26
/home stores user preferences and data, so there should not be too radical differences between the distros.  You should give it a shot and let us know what happens. :)

---

### Post by icheyne on 2007-12-26
Yes it should work fine. Back it up first though.

---

### Post by forestpixie on 2007-12-26
from what I've read it would be sensible to make sure that you have different user names for each - then the configs should be kept separately

---

### Post by bodhi.zazen on 2007-12-26
No, it does not always "work fine", it depends on the distros.

Assuming you are intending to share the user name ....

Linux does not recognize the user name directly, but rather the uid, or user id

The first user on Ubuntu is assigned a uid of 1000

BUT the first user on Fedora is assigned a uid of 500

So, even if they have the same name, they would have a different uid (1000 on Ubuntu and 500 on Fedora) and unless $HOME is world readable (permissions 777) you will have permissions problems, with both config files and data files/directories.

Second, you can run into problems with the .config files or . (dot) files.

IMO, Best to use a shared data partition across distros rather then a shared /home

---

### Post by dasunst3r on 2007-12-26
Oh, dang... that's right -- the UIDs could vary from distro to distro, and the EXT3 filesystem stores the UID, not the string of the user!  I think a shared data partition would be a better idea also -- I put mine at /mnt/cmnstor :)

---

### Post by meindian523 on 2007-12-26
It will work,provided you have separate usernames,I have done that once....had no problem accessing my Ubuntu files from openSUSE......

---

### Post by eldepeche on 2007-12-26
I recommend against it. Since your home directory stores your configuration files, it's possible that the two distros will have different versions of some programs, and the config files won't work, and will possibly crash the program.

However, if you're going to use different usernames/UIDs, then this doesn't apply.

---

### Post by Pogeymanz on 2007-12-27
How sad. Oh well, I'll just use different names for each.

---

