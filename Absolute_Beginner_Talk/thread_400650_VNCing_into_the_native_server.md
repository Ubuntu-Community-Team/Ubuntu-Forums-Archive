---
title: "VNCing into the native server"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by anoneironaut on 2007-04-03
Hey all,

    I just recently set up my KDE to allow me to VNC into my native x:0 display.  I just followed the guide on wikipedia ([http://gentoo-wiki.com/HOWTO_Use_TightVNC_W/_JPEG_Compression_to_connect_to_existing_X_Sessions](http://gentoo-wiki.com/HOWTO_Use_TightVNC_W/_JPEG_Compression_to_connect_to_existing_X_Sessions)) to make this happen.  However for some reason I just can not get the password portion of this guide to work.  I have tried everything including making my own password file in the etc/X11 directory, moving the option configs around, and changing the passwords.  After struggling with this for a bit I checked out the log file and noticed this:

(WW) NVIDIA(0): Option "SecurityTypes" is not used
(WW) NVIDIA(0): Option "UserPasswdVerifier" is not used
(WW) NVIDIA(0): Option "PasswordFile" is not used 

Why is this happening?  And where should I put the options so that they will be recognized as VNC options??

---

