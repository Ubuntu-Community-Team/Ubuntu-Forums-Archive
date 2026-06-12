---
title: "IE4linux...how to connect to microsoft"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-10-11
when trying to install IE4linux, i kept getting this timeout message:

"resolving download.microsoft.com... 1.0.0.0
connecting to download.microsoft.com|1.0.0.0|:80...
connection timed out"


the IP adress is wrong, so do:

    sudo gedit /etc/hosts

add the following line:

    80.67.85.79 download.microsoft.com

---

### Post by oilchangeguy on 2007-10-11
why do you need internet explorer? what's wrong with firefox?

---

### Post by Bliepo32 on 2007-10-11
He might be a developper, and could want to test webpages in different browsers?

---

### Post by Pulka on 2007-10-11
simply because some web pages don't load entirely with other browsers, and because my stupid online bank doesn't support anything else

---

### Post by leg on 2007-10-11
If you just want to pretend to be IE you can get a plugin from firefox that will change the user agent string.

[user agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59")

---

