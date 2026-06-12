---
title: "Writing a startup script for enabling trackpad tap"
date: 2008-06-10
forum: Apple Hardware Users
---

### Post by mfox on 2008-06-10
Since I can't seem to enable the trackpad tap in xorg.conf, I think the next best way to enable the tap is to write a simple script to do the Terminal equivalent of:

$ sudo trackpad tap 

and place it in the appropriate startup folder so that trackpad tap is enabled at bootup.  I'd like to know how to do this; more specifically:
(1) how do I write this script so that it will function without asking me for a password? (or allow me to supply the password within the script)
(2) what program do I write it in so that it will be read as a script or will any text editor do?
(3) in what folder do I put it in so it will run automatically at bootup?

---

### Post by stream303 on 2008-06-10
#1 is the biggest problem.  AFAIK, you can write a bash script to do this (any text-editor will do) and have it supply the password, but now you have a plaintext password on your system.  Not good.

I haven't seen any really good answer to this over the years, but if anyone knows, tell us! :)

---

### Post by mfox on 2008-06-11
Might there be a way to do this as a root script without the "sudo"?  If so, where would it be placed?

---

### Post by pharmakon on 2008-06-11
I was stumped by this problem too until I found that kugn had posted the solution here:

[http://ubuntuforums.org/showthread.php?t=488853](http://ubuntuforums.org/showthread.php?t=488853)

It's very simple, you just need to edit the /etc/pbbuttonsd.conf script and change the 'notap' to 'drag'. Works fine on my old ibook!

regards, ph.

---

### Post by eraker on 2008-12-10
I just put the three commands in the gdm start-up script (which is probably a terrible solution).

---

