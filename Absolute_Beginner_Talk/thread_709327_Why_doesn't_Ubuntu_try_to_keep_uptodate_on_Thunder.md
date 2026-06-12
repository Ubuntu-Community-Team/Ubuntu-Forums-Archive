---
title: "Why doesn't Ubuntu try to keep uptodate on Thunderbird releases?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by erm4gh on 2008-02-27
I am using Thunderbird version 2.0.0.6 (20071022) . Synaptic reports thats 2.0.0.8~pre071022+nobinonly0ubuntu07.10. 

Mozilla has released 2.0.0.9 and 2.0.0.12. Both of those releases were low priority security fixes plus normal bug fixes. The Lightning add-on is at 0.5 while the Mozilla build is at 0.7 and they're going to release 0.8 soon. 

Looking at launchpad I see that 2.0.0.12+nobinonly-0ubuntu1 is not planned until Hardy, which I think is scheduled for the end of April. 

Why is Ubuntu always behind on Thunderbird releases? It seems to try to keep current with Firefox releases. If they're low on resources why not just provide the latest released Mozilla build and add-ons as is rather than modifying it to install in a different location, disable "check for updates" etc.?

---

### Post by Martje_001 on 2008-02-27
Ubuntu will only provide security updates. This is important for companies, who don't want things to change. If you want newer versions of programs, upgrade to a developers release.

---

### Post by erm4gh on 2008-02-27
The two versions it skipped ARE security updates according to the Mozilla release notes. They don't even mention the existence of any other bug fixes, though you know (based on looking at [http://weblogs.mozillazine.org/rumblingedge/](http://weblogs.mozillazine.org/rumblingedge/) ) that they're included too. 

By developers releases, I think you're referring to nightly builds. Those aren't aren't meant for typical users - they're meant for testers.

---

### Post by philinux on 2008-02-27
If you want the latest from mozilla then this is the easiest way without borking synaptic.

[http://ubuntuzilla.wiki.sourceforge.net/?token=c5e8e3e7090b4354d9df1a3f71450201](http://ubuntuzilla.wiki.sourceforge.net/?token=c5e8e3e7090b4354d9df1a3f71450201)

---

### Post by FrozenFox on 2008-02-27
EDIT: Curses. As I was typing this, the above poster beat me to it. ;P

You may want to look into Ubuntuzilla. It supposedly will do this stuff for you, provide notices when updates are available and such. That stuff isn't updated normally in ubuntu because it hasn't been overlooked and judged 'stable' enough yet to be put into the repositories. You have to keep in mind, the interest of the current branch of ubuntu is always to keep things stable -first-, then up-to-date second. -Most- updates of programs include 'security updates', whether in large or small portions. How important they are and how thoroughly they have been tested and determined to be stable enough for public use are what judge which packages come through, from what i've seen. 

In short: if you want ultra new stuff, move to Hardy. If you want a stable system, stick with what you have and install the very new packages you want from the developers of said programs yourself or wait until the update is determined stable and important to be updated in the official repositories.

---

### Post by Kilz on 2008-02-27
There is another option. [Swiftdove]("http://swiftweasel.tuxfamily.org/") is an optimized build of the thunderbird code. It is released within days of a Thunderbird release and has a repository for automatic updates.

---

### Post by erm4gh on 2008-02-27
Thanks for the pointer to Ubuntuzilla. One reason why I don't want to use it is that in the past when I tried it I missed its notification of new updates because I wasn't at the computer then. However, I'm not asking for workarounds, *I'm trying to understand why Ubuntu does what they do.*

I have completely removed Thunderbird with Synaptic and downloaded and installed the latest released Mozilla build. That works fine, and supports "check for updates".

---

### Post by erm4gh on 2008-02-27
I had heard of Swiftdove before but wasn't aware that it gets released so quickly. Thanks, I'll check it out.

---

### Post by stchman on 2008-02-27
> **erm4gh said:**
> I am using Thunderbird version 2.0.0.6 (20071022) . Synaptic reports thats 2.0.0.8~pre071022+nobinonly0ubuntu07.10. 

Mozilla has released 2.0.0.9 and 2.0.0.12. Both of those releases were low priority security fixes plus normal bug fixes. The Lightning add-on is at 0.5 while the Mozilla build is at 0.7 and they're going to release 0.8 soon. 

Looking at launchpad I see that 2.0.0.12+nobinonly-0ubuntu1 is not planned until Hardy, which I think is scheduled for the end of April. 

Why is Ubuntu always behind on Thunderbird releases? It seems to try to keep current with Firefox releases. If they're low on resources why not just provide the latest released Mozilla build and add-ons as is rather than modifying it to install in a different location, disable "check for updates" etc.?

If you want the latest Thunderbird, then you can download the .tar.gz from Mozilla and run it.  It is not the source but a pre-compiled binary.  If you want the source you need to go to the developers section.

---

### Post by PeterJS on 2008-02-27
This is done because of the freeze segments of the release process. Every 6 months the developers grab a release of Debian Sid and start work on stablizing that, the first few months they work in paralell with the rolling Sid package set untill the Debian Import Freeze, at which point they branch there efforts in to will be the final ubuntu package, at this point the version number is more or less frozen. The next big freeze comes between alpah 4 and 5 when the freeze the API/ABI to allow a consistent interface and build environment for all packages and libraries. The user interface gets frozen between alpha 5 and 6. And after alpha 6, they freeze pretty much everything and work on shaking down bugs for the beta builds.

[https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)

---

### Post by erm4gh on 2008-02-27
I had assumed the development cycle for the next version of Ubuntu and maintenance fixes for the existing version of Ubuntu were done in parallel, and released independently.  Thats what I'm used to. My mistake.

Firefox hasn't been an issue so far but it sounds like I should switch to always using the Mozilla build for both Firefox and Thunderbird. I have no problem with using their pre-complied binaries.

---

### Post by HammerheadNC on 2008-02-28
> **philinux said:**
> If you want the latest from mozilla then this is the easiest way without borking synaptic.

[http://ubuntuzilla.wiki.sourceforge.net/?token=c5e8e3e7090b4354d9df1a3f71450201](http://ubuntuzilla.wiki.sourceforge.net/?token=c5e8e3e7090b4354d9df1a3f71450201)

This is an awesome solution. THANKS!!!

---

### Post by nanotube on 2008-02-28
> **erm4gh said:**
> Thanks for the pointer to Ubuntuzilla. One reason why I don't want to use it is that in the past when I tried it I missed its notification of new updates because I wasn't at the computer then. However, I'm not asking for workarounds, *I'm trying to understand why Ubuntu does what they do.*

I have completely removed Thunderbird with Synaptic and downloaded and installed the latest released Mozilla build. That works fine, and supports "check for updates".

hm, i have been tinkering around with making ubuntuzilla update notifications appear as an icon in the notification area, instead of the very transient notification we have now... 
unfortunately it looks like the tray functionality was not built into pygtk until rather recently, so dapper users would not be able to use that... if someone is familiar with how to code that up, feel free to comment on the ubuntuzilla subforum.  otherwise, just wait and eventually i will get it right. :)

---

