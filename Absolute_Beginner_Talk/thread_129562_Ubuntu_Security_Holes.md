---
title: "Ubuntu Security Holes"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Mdups on 2006-02-14
Hello everyone :)

Brand new Linux user here. I searched the forums for an answer to my question but I could not find a thread that completly answered my question.

I installed a fresh copy of Ubuntu and like every OS out there I am certain there must be a few security issues that need to be manually addressed.  For example with Windows XP I would at least always enable its firewall and then install sp2.  I installed all the latest updates for Ubuntu upon installing it.


My question is... For Ubuntu are there a few ports I should plug? or should I enable certain options that would prevent common exploits from being executed?

Either an answer or a link to a guide would be greatly appreciated. Thanks.

---

### Post by pinoyskull on 2006-02-14
install firestarter for some basic linux security

```

sudo apt-get install firestarter
```
other security options can be found here [http://doc.gwos.org/index.php/SecurityAnalysis](http://doc.gwos.org/index.php/SecurityAnalysis)

---

### Post by codejunkie on 2006-02-14
head over to [www.grc.com](www.grc.com) and run sheilds up if there are any open ports that you don't wan't open if you have a router just forward the ports to an unused ip in your router you can also install firestarter a software firewall for linux. don't know for sure if it matters but i've heard that if you don't use ssh it's a good idea to disable it, you can do that by running```
sudo update-rc.d -f ssh remove
```in a terminal and you can install rkhunter and chkrootkit and a virus scanner if you get worried.

---

