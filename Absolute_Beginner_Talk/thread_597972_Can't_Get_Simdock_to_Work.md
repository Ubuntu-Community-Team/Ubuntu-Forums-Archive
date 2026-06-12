---
title: "Can't Get Simdock to Work"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-10-30
I cant get Simdock working because of the error that I get when i try to ./configure on gutsy
```

---------------SIMDOCK------------------

checking for wx-config... no
configure: error:
                wxWidgets must be installed on your system.

                Please check that wx-config is in path, the directory
                where wxWidgets libraries are installed (returned by
                'wx-config --libs' or 'wx-config --static --libs' command)
                is in LD_LIBRARY_PATH or equivalent variable and
                wxWidgets version is 2.8.0 or above.

```
i downloaded every wx package that i could find in synaptic and I am still getting an error so far I have
wx2.8-doc
wx2.8-examples
wx2.8-headers
wx2.8-il8n
wx-common
wxmaxima

those are all the packages relevant to when i search "wx" or "widgets" in synaptic but it still wont get passed this step

---

### Post by amneziac on 2007-10-31
bump...what is up with nobody ever replying to my posts anymore

---

### Post by amneziac on 2007-10-31
bump

---

### Post by overdrank on 2007-10-31
> **amneziac said:**
> bump...what is up with nobody ever replying to my posts anymore

Hi and this may not help in your compiling question but I just install the 1.1 version on my gutsy because the 1.2 deb was corrupt. If you would like to try the deb file it can be found here. 
[http://sourceforge.net/project/showfiles.php?group_id=198436](http://sourceforge.net/project/showfiles.php?group_id=198436)

---

### Post by amneziac on 2007-10-31
thank you so much for your reply but unfortunately the .deb package also doesnt work I can an error that the file may be corrupt or i dont have permission to run it

---

### Post by overdrank on 2007-10-31
> **amneziac said:**
> thank you so much for your reply but unfortunately the .deb package also doesnt work I can an error that the file may be corrupt or i dont have permission to run it

You get that error with the 1.1 deb file?

---

### Post by amneziac on 2007-10-31
yeah, before i can click INstall Package, it says that it cant open because its corrupt or i dont know permission to, when i try and ./configure the tar i get an error as stated in my very first post

---

### Post by reader4 on 2007-11-01
> **amneziac said:**
> yeah, before i can click INstall Package, it says that it cant open because its corrupt or i dont know permission to, when i try and ./configure the tar i get an error as stated in my very first post

I get that error in the deb package only if I try to click to install.  If I install from the command line, it starts up just fine.  

Unfortunately, I get an error that simdock depends on libwnck18 ... I have libwnck22.  I can't just install libwnck18 because it depends on libwnck-common, which is a later version, etc.

---

### Post by IronWolve on 2007-11-01
Same issue for me. Simdock 1.2 deb and trying to configure has issues.

---

### Post by c0mp13371331337 on 2007-11-12
Didn't see this as having been resolved, so I'll add my two-pennies-worth in hopes that I may be of some assistance.

I've got SimDock running just fine on Ubuntu Gutsy.  First thing you need to do is satisfy that wxwidgets dependancy.  I'm not sure if it's in the repos yet (or if it'll ever be) but here's a .deb file which you can download to your desktop or something, then just double-click to install:

[wxwidgets]("http://www.box.net/shared/91x5r27zyg")

If that complains about a libpango dependancy, which it did for me, you'll need to *temporarily* enable the Proposed repositories in Synaptic and do a search for libpango, and install libpango1.0-0, version 1.18.3-0ubuntu1.  Don't forget to disable the proposed repos unless you want updates for not-quite-there-yet software!

That should allow you to use gdebi package installer to install wxwidgets, then you can download and double-click the actual SimDock package:

[SimDock]("http://www.box.net/shared/ht4abfyf46")

*I* personally didn't need to satisfy any dependancies for that one at this point.  Not sure if you'll have the same experience though.  Assuming all goes well with that, just type simdock at a terminal or Alt+F2 and type simdock.

Let me know how that goes and if you run across any other issues!

---

### Post by krum303 on 2007-11-21
[B]Holy Cow, you rule, c0mp13371331337!!:KS
I've tried other Dock apps and really wanted to use Simdock and I was having the same .deb problem until I used your link for the beta! Works great! Thank you and buy yourself a pint![/B]

---

### Post by DarthPooky on 2007-11-21
> **amneziac said:**
> thank you so much for your reply but unfortunately the .deb package also doesnt work I can an error that the file may be corrupt or i dont have permission to run it

Funny it works for me.

---

