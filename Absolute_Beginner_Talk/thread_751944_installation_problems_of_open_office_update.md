---
title: "installation problems of open office update"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by scientist1971 on 2008-04-11
newbie problem - trouble adjusting to differences between ubuntu and windows :(
installing new software on windows was something I always found very straight forwards but am unfortunately finding this process in ubuntu very unintuitive
tried today to update OO from 2.3 provided in ubuntu 7.1.0 to 2.4 which I have on my girlfriend windows PC
Followed procedure on the net i.e.
uninstalled OO2.3
downloaded OO2.4
then problems started
could no open/ extract the software on anywhere in ubuntu using terminal or package manager
I feel that I am overlooking something straight forwards but what.....?
any advice appreciated

---

### Post by Tatty on 2008-04-11
How have you downloaded OpenOffice?  did you download the .tar.gz file from the offical website?

It would be better if you downloaded a .deb - this is the packaging format used by ubuntu.  Go to the official website, click "Download" then "Get more platforms and languages".  This will take you to a page where you can download a .deb.

Once you have it, double click on it.  Gdebi will then load which will install it onto your system, make sure all dependencies are satisfied and it should also add an entry to synaptic so you can easily remove it later.


However, consider whether you really need the latest version.  You wont receive any security updates for it via the repos, so you will have to keep it up to date yourself.  I usually tend to just stick with what is offered in the repos - unless there is something i really need that simply isnt available in the repos.

---

### Post by scientist1971 on 2008-04-11
thanks a lot for your help
very informative
cheers:)

---

