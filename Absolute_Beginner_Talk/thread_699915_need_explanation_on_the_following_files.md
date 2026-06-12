---
title: "need explanation on the following files"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by enoughsaid05 on 2008-02-17
Hi

I would like to ask what these files are:

/etc/
/bin/
/lib/
/src/
/sbin/

Please add on if I have missed out anything

and so on.

I know that / means root and /home/user is which I would be using most of the time.

Last week I tried installing virtualbox-ose and thought it crashed my system. I foolishly went on to reinstall only to find out that by rebooting ubuntu into recovery mode, type in "nano /etc/group/" and add in my user name can the problem be resolved.

So how do I know when can I use the following files?

---

### Post by icechen1 on 2008-02-17
First they are folders.
see [http://geek2live.blogspot.com/2007/09/linux-file-structure.html](http://geek2live.blogspot.com/2007/09/linux-file-structure.html) and [http://slashmedia.wordpress.com/2007/12/23/linux-directory-structure/](http://slashmedia.wordpress.com/2007/12/23/linux-directory-structure/)

---

### Post by iansane on 2008-02-17
I think this explains them pretty good
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

 I think the simple expaination for bin is that it holds most executables (programs) and scripts. It's not the only place that holds those but for the most part it is.

etc/fstab is a good example for config files that are in etc. (needed for certain drive mounting tasks.) open the various config files in it to get a good idea. Just don't edit them till your sure what you are editing. 

The others are on that page. I would like an explaination of what the letters stand for and where names come from like etc.

---

