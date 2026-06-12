---
title: "clamav updating error out of date??"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by geezerone on 2007-02-22
Hi

Just tried updating clamav using 'sudo freshclam' and get the following error:

```
sudo freshclam
Password:
ClamAV update process started at Thu Feb 22 18:14:17 2007
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.88.4 Recommended version: 0.90
DON'T PANIC! Read http://www.clamav.net/faq.html
main.cvd is up to date (version: 42, sigs: 83951, f-level: 10, builder: tkojm)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 10
DON'T PANIC! Read http://www.clamav.net/faq.html
daily.cvd is up to date (version: 2629, sigs: 9682, f-level: 13, builder: trog)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 13
DON'T PANIC! Read http://www.clamav.net/faq.html
```

Any idea why? 
I checked where 'freshclam' is situtated here:

```
 whereis freshclam
freshclam: /usr/bin/freshclam /usr/bin/X11/freshclam /usr/share/man/man1/freshclam.1.gz

```

TIA :)

---

### Post by Obor on 2007-02-22
The clamav version in repos is "little bit old". Your virus definitions should by up to date though. If you want to have the latest version of clamav you will probably need to download and install it from their website.

---

### Post by geezerone on 2007-02-22
Thanks for the reply.

I have the same version on another pc and can perform freshclam ok. Strange thing is that when I try to gedit freshclam.conf there appears to be no file to edit?

---

### Post by johnnydepp74 on 2007-02-23
What I did was to go to the download folder and do a "make uninstall".

Then just download the newer clamav.tar.gz file and do a "configure", "make" followed by "make install"; and run the freshclam again.

quite straight forward actually.

Cheers.

Rgds
John

---

### Post by RomeReactor on 2007-02-23
Hi. From your terminal's output

```
sudo freshclam
Password:
ClamAV update process started at Thu Feb 22 18:14:17 2007
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.88.4 Recommended version: 0.90
DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)
**main.cvd is up to date (version: 42, sigs: 83951, f-level: 10, builder: tkojm)**
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 10
DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)
**daily.cvd is up to date (version: 2629, sigs: 9682, f-level: 13, builder: trog)**
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 13
DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)
```

it looks like your virus definitions are up-to-date.

---

### Post by shane2peru on 2007-02-24
> **johnnydepp74 said:**
> What I did was to go to the download folder and do a "make uninstall".

Then just download the newer clamav.tar.gz file and do a "configure", "make" followed by "make install"; and run the freshclam again.

quite straight forward actually.

Cheers.

Rgds
John

Hey, I did this, because I wanted the newest clamav.  And now freshclam doesn't work.  Any ideas?  Thanks

Here is the error I get:```
sudo freshclam
ERROR: Parse error at line 44: Option AllowSupplementaryGroups requires boolean argument.
ERROR: Parse error at line 76: Option FixStaleSocket requires boolean argument.
ERROR: Can't parse the config file /usr/local/etc/clamd.conf

```

Shane

---

### Post by shane2peru on 2007-02-24
Never mind.  I got it figured out.  I looked up the web site and read through the documentation.  I guess that should have been my first step.  Sorry! :oops: 

Shane

---

