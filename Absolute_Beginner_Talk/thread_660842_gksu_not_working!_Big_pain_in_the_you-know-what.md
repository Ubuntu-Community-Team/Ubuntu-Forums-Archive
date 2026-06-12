---
title: "gksu not working! Big pain in the you-know-what"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by lamalex on 2008-01-07
My gksudo stopped working, when I launch some sort of administrative application, I'm never prompted for my password and the application never opens. Obviously I can just launch it from the command line, but that's certainly not ideal.
This is the output from ```
gksudo -d nautilus
```
> 
alauni@acewks05:~/Desktop$ gksudo -d nautilus
No ask_pass set, using default!
xauth: /tmp/libgksu-PMSYhr/.Xauthority
STARTUP_ID: gksudo/nautilus/25425-0-acewks05_TIME1419436926
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: nautilus
buffer: --
</snip>
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.


After that it just hangs indefinitely. Does anyone have any idea how to fix this?

---

### Post by rodo-&gt;dave on 2008-01-07
found this thread.. maybe will help:
[http://www.backports.ubuntuforums.org/showthread.php?t=424937](http://www.backports.ubuntuforums.org/showthread.php?t=424937)

---

### Post by lamalex on 2008-01-07
Wish I could say that worked! Thanks for the try, anyone else have any ideas? Is there a config file or anything for gksudo?

---

### Post by rodo-&gt;dave on 2008-01-07
ok. I found another thread here:
[http://ubuntuforums.org/showthread.php?t=616290](http://ubuntuforums.org/showthread.php?t=616290)

sorry if you already looked through these

---

### Post by erginemr on 2008-01-07
I had trouble with sudo/gksu before in Edgy; Once, I could not login to Gnome after using "sudo" in a graphical program instead of "gksu". I could solve the problem by deleting the files .Xauthority and .ICEauthority in my home folder, as apparently they were corrupted.

Maybe it is irrelevant but you may try renaming those to, say .Xauthority_bak etc. (they are owned by root by the way, so you need to use "sudo mv ..." to rename them), logout and back in, and check whether you can use "gksu" again.

---

