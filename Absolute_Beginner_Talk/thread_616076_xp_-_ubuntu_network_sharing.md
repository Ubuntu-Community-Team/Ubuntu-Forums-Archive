---
title: "xp - ubuntu network sharing?"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by mickfitz on 2007-11-17
Hello ... I'm new (today) to Ubuntu! :-)

I've somehow managed to set up networking and sharing with some of the excellent posts and a video I found on youtube.

I have one last hurdle. When I look/browse to the shared folder on my Untubu box from an xp box I can't edit or add/move any files ... I can't do anything other than view the contents of the folder.

I'm pretty sure I've enabled all the right options for the folder and I have made quite a few adjustments to the samba conf file.

Here's hoping it's gonna be summat real easy? Thanks in advance

Mick

---

### Post by Pumalite on 2007-11-17
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html)

---

### Post by Naipes on 2007-11-17
> **mickfitz said:**
> Hello ... I'm new (today) to Ubuntu! :-)

I've somehow managed to set up networking and sharing with some of the excellent posts and a video I found on youtube.

...and I have made quite a few adjustments to the samba conf file.


Mick

"...quite a few adjustments...?"  I'm a noob too, but when I set up file sharing I think I only adjusted a couple of lines in smb.conf.
 
Check to make sure  your smb.conf. file shows  the following text:

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

Make sure writable = yes

Good luck!

---

