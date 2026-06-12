---
title: "Firefox 2.0.0.1 won't install flash player plugin"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-02-13
I switched from 6.10 to 6.06 on one of my computers because I was having problems with 6.10.  I seem to have solved some problems, but I'm having some new problems now.  When I go to YouTube in Firefox, I get an "Additional plugins are required to display all the media on this page," message at the top of the screen, and when I click the button to search for plugins, it just searches forever and never installs.  How do I solve this problem?

---

### Post by taurus on 2007-02-13
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
or
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by Brunellus on 2007-02-13
for help with Flash, visit

[http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

EDIT:  Taurus, you beat me to the draw this time.

---

### Post by taurus on 2007-02-13
> **Brunellus said:**
> 
EDIT:  Taurus, you beat me to the draw this time.

So we meet again, Brunellus.  ):P

---

### Post by Brunellus on 2007-02-13
> **taurus said:**
> So we meet again, Brunellus.  ):P
support-forum kung-fu.

---

### Post by SuperCool4678 on 2007-02-13
I followed the instructions on the first link, and YouTube works now, but other pages still give me the message that I need plugins that it won't install.


> **taurus said:**
> [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
or
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

The link to this site doesn't work:

[http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Brunellus on 2007-02-13
> **SuperCool4678 said:**
> I followed the instructions on the first link, and YouTube works now, but other pages still give me the message that I need plugins that it won't install.




The link to this site doesn't work:

[http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)
you might need Flash 9 (not sure if that's covered in the howtos yet) or Java (which is in RestrictedFormats)

---

### Post by igknighted on 2007-02-13
Do you have java installed?  First enable all repos, then install these pacakges:
```
sudo apt-get update
sudo apt-get install sun-java5-jre sun-java5-plugin
```

---

### Post by SuperCool4678 on 2007-02-15
> **igknighted said:**
> First enable all reposjre sun-java5-plugin[/CODE]

How do I do that?  What are repos?

---

### Post by Brunellus on 2007-02-15
> **SuperCool4678 said:**
> How do I do that?  What are repos?
have a look at

[http://help.ubuntu.com/community/InstallingSoftware](http://help.ubuntu.com/community/InstallingSoftware)

---

### Post by SuperCool4678 on 2007-02-16
> **igknighted said:**
> Do you have java installed?  First enable all repos, then install these pacakges:
```
sudo apt-get update
sudo apt-get install sun-java5-jre sun-java5-plugin
```

That didn't fix my problem.

Is this the right set of repos to have?

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main


The "enable Java" and "Enable Javascript" boxes in my Firefox preferences are both checked BTW

---

### Post by jmmbishop on 2007-03-05
I´m having the same problem.  I tried everything that was mentioned already in this forum.  All repos enabled, java enabled, followed the instructions on that first link.  I´m not the most computer-savvy guy around, but the problem seems to be with the ftp server from which we´re attempting to d/l the flash plug-in itself.  Most of the time it tries to start downloading and never starts.  Other times, it starts in fits--it´ll download maybe 5% of the file and then stop dead in its tracks.

I have tried getting it through apt-get & Automatix.  Both stall at the exact same point--when it tries to get the plugin from the ftp server.  

I just installed ubuntu today and have never used linux before.  I´m kinda lost.

Any suggestions?

---

### Post by jmmbishop on 2007-03-06
It appears to have just been a problem with the server.  Downloaded it this morning and all is well.

---

