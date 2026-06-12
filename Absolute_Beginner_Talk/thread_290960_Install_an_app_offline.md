---
title: "Install an app offline?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by sjf on 2006-11-01
Being a long time windows user, but have 4 years unix experience at University as a normal student user, and using setting up and running a few Solaris 10 boxes at work for the past 3 months, I am interested in building Kubuntu box at home for personal use. Since the internet is lightening fast at work and when I was at university I have had no need for the internet at home.

So sorry upfront for the newbie question: Will I be able to download a package/file/collection of files at work and then come home and install it my home kubuntu box?

Let's take Firefox 2.0 as an example. If go here: [http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html) and download for the Linux i686, will I be able to go home and install this on my kubuntu box?

And before you say "Why do you need Firefox, if you don't have an internet connection?", I like to do offline web programming at home etc...

Thanks for understanding in advance.

---

### Post by aysiu on 2006-11-01
Firefox is easy, but if you're installing something from the repositories, it'll be a real pain to install without an internet connection.

[http://help.ubuntu.com/community/FirefoxNewVersion](http://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by jpeddicord on 2006-11-01
The best way, if a site offers it, is to download the .deb. You can then directly run this to install while offline.

For example: [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Ff%2Ffrozen-bubble%2Ffrozen-bubble_1.0.0-6ubuntu1_i386.deb&md5sum=2bf5285d89bccab223bdd8a0ae6310ac&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Ff%2Ffrozen-bubble%2Ffrozen-bubble_1.0.0-6ubuntu1_i386.deb&md5sum=2bf5285d89bccab223bdd8a0ae6310ac&arch=i386&type=main)
would be frozen-bubble for i386.

If the application depends on others, however, you will need an internet connection.

---

### Post by IYY on 2006-11-01
As long as you make sure you get all the packages in the requirements for your package, it's all good. Just grab the debs.

---

### Post by sjf on 2006-11-01
Thanks for the quick replies! This community is awesome!

---

### Post by JustBrowsing on 2006-11-01
*Just learned this earlier this evening*

If you have downloaded the programs via the repositories and have the programs on disk.

Like the posts said above: the .deb file will have all the information necessary to install the file from scratch.

However, if you've downloaded the file from the repositories, then the .debs for those downloads are located in: (default location)

"/var/cache/apt/archives"

from there you should be able to copy the files to a USB, CD, whatever and it should install as long as you have admin access.

Thanks to this great community for letting me know you can still get programs if you don't have a internet connection; and can install as long as the .debs are downloaded.:-D

---

