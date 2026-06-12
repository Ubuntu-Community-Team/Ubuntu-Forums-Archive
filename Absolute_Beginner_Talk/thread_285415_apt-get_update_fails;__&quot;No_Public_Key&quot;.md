---
title: "apt-get update fails;  &quot;No Public Key&quot;"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by brn on 2006-10-26
Running Dapper on a Dell laptop I get this from apt-get:

:~$ sudo apt-get update
Get:1 [http://http.us.debian.org](http://http.us.debian.org) stable Release.gpg [189B]
Hit [http://http.us.debian.org](http://http.us.debian.org) stable Release
Err [http://http.us.debian.org](http://http.us.debian.org) stable Release

Get:2 [http://http.us.debian.org](http://http.us.debian.org) stable Release [34.6kB]
Ign [http://http.us.debian.org](http://http.us.debian.org) stable Release
Ign [http://http.us.debian.org](http://http.us.debian.org) stable/main Packages
Ign [http://http.us.debian.org](http://http.us.debian.org) stable/contrib Packages
Ign [http://http.us.debian.org](http://http.us.debian.org) stable/non-free Packages
Hit [http://http.us.debian.org](http://http.us.debian.org) stable/main Packages
Hit [http://http.us.debian.org](http://http.us.debian.org) stable/contrib Packages
Hit [http://http.us.debian.org](http://http.us.debian.org) stable/non-free Packages
Fetched 34.8kB in 6s (5168B/s)
Reading package lists... Done
W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
W: You may want to run apt-get update to correct these problems

I figure the "PUBKEY" is something that should be on my computer someplace but don't know where or how to retrieve/restore it.  

What I'm eventually after is to install the optional KDE desktop.  I first tried aptitude update and had exactly the same problem. 

I tried both aptitude and apt-get several times with identical results in the same place so I'm pretty sure it isn't a glitch in my dialup connection.   What don't I know?

---

### Post by Rackerz on 2006-10-26
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -

That should fix it.

---

### Post by brn on 2006-10-26
Thanks Rackerz.  I tried the first command and got this:
```
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```
No suprise then that the second command produced this:
```
gpg: WARNING: nothing exported
```

As far as I can tell, my system is all in order and my network connection is solid.  Does the message "...receive failed..." suggest a problem on the other end?  I've only been running this configuration for a week so I haven't yet had a chance to mess it up.

---

### Post by aktiwers on 2006-10-26
This post will fix your problem.
[http://www.ubuntuforums.org/showthread.php?t=279758](http://www.ubuntuforums.org/showthread.php?t=279758)

---

### Post by wieman01 on 2006-10-26
The key server "subkeys.pgp.net" is on line. But can you ping it on your end? Or have you configured IP tables? Perhaps the firewall is keeping you from connecting...

---

### Post by brn on 2006-10-26
Well, I've discovered something but I'm not sure what it means.  I tried issuing the gpg command as root (sudo gpg...etc.) and got this
```
gpg: WARNING: unsafe ownership on configuration file `/home/brn/.gnupg/gpg.conf'gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
```
So I looked at .gnupg/gpg.conf and found that every single line was commented out.  I'm not sure what this means but it doesn't look good.  the gpg man page directed me to the *Gnu Privacy Handbook* which looks a lot like Zimmermans original PGP document which I haven't seen for many years.  But it doesn't seem to explain what gpg.conf does nor which of the commented lines might resolve the problem nor -most intriguing- why the package files are encrypted at all.

---

### Post by wieman01 on 2006-10-26
What the user permissions... Can you do a:
> ls -l
Perhaps you have to change the owership to your user.

---

### Post by brn on 2006-10-27
My thanks to aktiwer.  I found the solution to the PUBKEY problem here:

> Re: apt-get update fails; "No Public Key"
This post will fix your problem.
[http://www.ubuntuforums.org/showthread.php?t=279758](http://www.ubuntuforums.org/showthread.php?t=279758)

Next I learned that my sources list had only a dozen or so debian links, none from ubuntu.  After reloading this everything seems in order. Now back to trying to get the KDE desktop option working. 

Thanks everyone.

---

