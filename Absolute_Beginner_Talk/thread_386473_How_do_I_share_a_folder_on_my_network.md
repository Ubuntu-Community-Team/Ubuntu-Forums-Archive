---
title: "How do I share a folder on my network?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2007-03-17
It's been a while since I've had to set this up, so I forget... how do I share an Ubuntu folder on my Windows network?  I've set it to share in "properties", but when I try to access it from a Windows computer, it asks for a username and password.  My Ubuntu username and password do not work.

Do I just need the password (and if so how do I know what it is?), or am I about to get into some serious sudo gediting?

Thanks!

-Mark

---

### Post by Fataltragedy2 on 2007-03-17
Have you setup samba completely?

This may help.

[http://ubuntuforums.org/showthread.php?t=2389](http://ubuntuforums.org/showthread.php?t=2389)

---

### Post by glenndavy on 2007-03-17
hey there mark...
six things come to mind...
1) IRC there is a simple gui way to share a folder that doesn't involve samba.. I use kubuntu, but couldnt tell you where to get to it in regular gnome based ubuntu
2) have you set up a password for your user... i.e. from a terminal:
```

  sudo smbpasswd -a myusername

```
3) make sure "encrypted password" is set to yes in /etc/samba/smb.conf (as xp will by default use encrpyted passwords) - btw i think it is encrypted by default in ubuntu - but check
4) There was once a time where you had to a a regsitry key "RequireSignOrSeal" =1 IRC... but i dont know if that applies now - you might have to google, or install samba-doc to find out
5) i'll put this as a question... when it asks for the password is it asking the the user $RPC, or for you?
6) other samba settings like allowed/denied users/hosts etc etc are over riding - this is very unlikely unless you have been fidling

lemme know if any of this is helpful

glenn

---

### Post by mjpatey on 2007-03-17
Thanks, both of you!  As it turned out, all that was missing was my username and password.  I sudoed the line that glenndavy suggested, entered my info, and blammo! Not sure what that was, maybe someone fired a shotgun.  But then Samba worked!

Thank you thank you thank you!

-Mark

---

### Post by glenndavy on 2007-03-17
gets me e_v_e_r_y s_i_n_g_l_e time -  i never remember till i panic and have a WTF moment

---

