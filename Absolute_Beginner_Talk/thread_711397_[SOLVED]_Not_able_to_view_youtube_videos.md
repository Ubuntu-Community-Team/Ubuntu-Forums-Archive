---
title: "[SOLVED] Not able to view youtube videos"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2008-02-29
Having installed gutsy on another PC I cannot seem to get youtube to play any videos. I have installed Flash a number of times to no avail. I use Opera browser. I have followed a number of forum suggestions, but no luck. I believe I have all necessary repositories installed but I am now baffled. 
Any help to get this up and running would be appreciated.
regards

---

### Post by kellemes on 2008-02-29
Have you installed [Opera Beta]("http://www.opera.com/products/desktop/next/")?
I know the latest stable of Opera can give crap with Flash, the Beta has it fixed.
I assume you have installed the flash-plugin..

---

### Post by Mad_Dawg on 2008-02-29
Maybe Firefox will take care of  the problem.

---

### Post by forrestcupp on 2008-02-29
There may be a couple of repositories that you didn't know to enable.  Open up Synaptic and go to Settings->Repositories.  Click the 'Updates' tab.  Check the boxes that say 'Pre-released updates' and 'Unsupported updates'.  Then click the Reload button.  The flashplugin-nonfree that you have now will work with Opera and FF2.

---

### Post by Sbarton on 2008-02-29
Thanks for the input!
kellemes, it doesn't make any difference!
Mad_Dawg, I have used opera for so long, (tried firefox) prefer opera.
forrestcup, I have these installed, but I prefer opera.
Thanks guys, I know it works with epithany, but I really would like to have it working in Opera.
Thanks for taking time out to post!
Any other suggestions?
regards

---

### Post by owbizi on 2008-02-29
You can try that:

[http://ubuntuforums.org/showpost.php?p=4429891&postcount=17](http://ubuntuforums.org/showpost.php?p=4429891&postcount=17).

Has fixed the problem with one user right now... you can get the package here:

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb).

---

### Post by Sbarton on 2008-02-29
Thanks owbizi, tried that still no luck! Crazy eh!
Never had this problem on my old machine!
regards

---

### Post by Shrek X on 2008-02-29
dont know if its right, or wrong, but this fix did it for me

> **RomeReactor said:**
> Hi. This problem has been discussed many times, and it's directly related to [this bug]("http://ubuntuforums.org/showthread.php?t=636397"). To get Flash working, download one of the following packages:

* [flashplugin-nonfree for Ubuntu 7.10 32-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466")
* [flashplugin-nonfree for Ubuntu 7.10 64-bit]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466")

Close Firefox, and double-click the package to install. Make sure gnash is not installed:
```
sudo aptitude remove --purge gnash mozilla-plugin-gnash
```

---

### Post by Sbarton on 2008-03-01
> **kellemes said:**
> Have you installed [Opera Beta]("http://www.opera.com/products/desktop/next/")?
I know the latest stable of Opera can give crap with Flash, the Beta has it fixed.
I assume you have installed the flash-plugin..

Just wanted to say that the Beta did not work 1st time. Since then I have purged 'flash' checked all repos;reinstalled the Opera Beta and now it is working OK! 
Thanks to all posters for your time and suggestions. Great community eh!
eventually the problems get solved.
regards to all!:)

---

### Post by kellemes on 2008-03-01
> **Sbarton said:**
> Just wanted to say that the Beta did not work 1st time. Since then I have purged 'flash' checked all repos;reinstalled the Opera Beta and now it is working OK! 
Thanks to all posters for your time and suggestions. Great community eh!
eventually the problems get solved.
regards to all!:)

Glad it works.. Opera Beta is pretty damn cool, nothing beets Opera for me..

---

### Post by bben on 2008-03-02
> **kellemes said:**
> Have you installed [Opera Beta]("http://www.opera.com/products/desktop/next/")?
I know the latest stable of Opera can give crap with Flash, the Beta has it fixed.
I assume you have installed the flash-plugin..

I had the same problem, this fixed it for me. Thanks!

---

