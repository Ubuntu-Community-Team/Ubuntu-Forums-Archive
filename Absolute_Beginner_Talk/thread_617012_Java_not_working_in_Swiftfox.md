---
title: "Java not working in Swiftfox"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by RSrealo on 2007-11-18
I can run runescape (Online-game) with FireFox, java working just fine. It will not run the applet in swiftfox. It says that I need to install Java. 

Thx in advance.

---

### Post by stido on 2007-11-19
try this one maybe?
[http://onlyubuntu.blogspot.com/2007/04/install-popular-applications-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2007/04/install-popular-applications-in-ubuntu.html")

---

### Post by RSrealo on 2007-11-19
Thx for the reponse. Will this work on Gutsy?

---

### Post by mig5 on 2007-11-27
You shouldn't need to install automatix like stido suggested to do this.  Simply copying the libjavaplugin.so from /usr/lib/firefox/plugins/ to the [SwiftfoxInstallationDirectory]/plugins/ folder should be enough.

---

### Post by RSrealo on 2007-11-29
> **mig5 said:**
> You shouldn't need to install automatix like stido suggested to do this.  Simply copying the libjavaplugin.so from /usr/lib/firefox/plugins/ to the [SwiftfoxInstallationDirectory]/plugins/ folder should be enough.

Thank you MIG that work :) 

Stido, thx for directing me to automatix, this is one cool bundled package.

---

### Post by PmDematagoda on 2007-11-29
I advise you to not to use Automatix at all. It is not a very efficient method of installing applications since it can break your system instead of making it, you would do better to stick to methods like apt-get, etc.

---

