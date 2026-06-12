---
title: "Crunchbang Eee PC questions..."
date: 2011-07-02
forum: Any Other OS
---

### Post by BigSilly on 2011-07-02
Finally managed to download Crunchbang Statler and install it onto our beloved Eee 701. It's absolutely brilliant. I'm thrilled to bits with how fast and swish everything is, and how in one fell swoop it's refreshed our Eee. Fantastic!

However, I don't know much about #!, and the forum hasn't turned up any answers, so I wonder if you can help here. I notice that it comes with Chromium as its browser, which is fantastic, but it's a slightly older version (V9). It looks like this is the one it has because this is the main stable Debian Squeeze version of Chromium. I'm fine with that, it works great with no problems at all, but hasn't the browser had quite a few updates recently for security reasons? What would you recommend; adding a third party repo and installing a newer version, or waiting until the main Squeeze repository hopefully updates the browser? Ditto Flash Player. Again it's a slightly older version. Bearing in mind the Eee 701 only has a paltry 4Gb of disk space (the install is currently at the 2Gb mark), so I don't want to be adding too much extra software. What would you recommend people? :-k

Many thanks in advance. :)

---

### Post by wolfen69 on 2011-07-02
I had one of those netbooks and wound up doing a cli of ubuntu. That way, it was extremely lean and I had ubuntu's vast repos at my fingertips.

---

### Post by BigSilly on 2011-07-03
I'll look into that. Thanks. :)

I do really like Crunchbang however, and am going to stick with it for a while. I might just add the newer Chrome manually, but if it's in Debian Stable then it must be fine. I'll wait.

---

### Post by snowpine on 2011-07-04
Hi there, I'm a long-time Crunchbang user!

```
$ apt-cache policy chromium-browser
chromium-browser:
  Installed: 9.0.597.45~r70550-1
  Candidate: 9.0.597.45~r70550-1
  Version table:
 *** 9.0.597.45~r70550-1 0
        990 http://packages.crunchbanglinux.org/statler/ statler/main i386 Packages
        100 /var/lib/dpkg/status
     6.0.472.63~r59945-5+squeeze5 0
        100 http://ftp.us.debian.org/debian/ squeeze/main i386 Packages
        100 http://security.debian.org/ squeeze/updates/main i386 Packages

```

In other words, Debian Stable/Squeeze provides Chromium 6.0... Corenominal (the CrunchBang developer) has provided an *updated* 9.0 version for our browsing pleasure... and of course if you prefer a newer version, you are perfectly free to do so! I believe that if you install the .deb from the Google site, it will automagically add the Google repo to your software sources so you are always up-to-date. :)

---

### Post by BigSilly on 2011-07-04
Ah I never thought to look. I just presumed it was Debian bringing the Chromium package in. Still, it's an older one either way. But that said, I'm not too fussed as it's working fine and doesn't really matter on the netbook. There's nothing locally stored on it, and it's not used for much other than FB and general browsing. I'll only update to Chrome if someone especially recommends it for security.

Thanks for your replies. :)  Loving #!

---

### Post by sidzen on 2011-07-05
Statler, being Debian-based, can use the award-winning script [**smxi,**]("http://smxi.org/") in which is offered the browser Swift Fox -- uses much less memory than Firefox.  Check out all the options, but  be conservative, would be my recommendation.

---

