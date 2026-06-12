---
title: "Firefox 1.5.0.13 - dapper"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Green White on 2007-07-20
Hi guys,

      I am using Dapper-Drake and just updated to firefox 1.5.0.13 using Synaptic. However it shows 1.5.0.12 when I check About in Firefox. I wonder if anybody is encountering this bug. 

     I am sorry to waste your time on such a trivial matter however I can't find any mention on it in the web.


     Thanks and ubuntu-on .

---

### Post by Freddy on 2007-07-20
You have restarted Firefox, right?

---

### Post by Green White on 2007-07-20
Yes I have, Freddy.

   I am wondering if its just a typo.

---

### Post by Freddy on 2007-07-20
I don't know since I don't use Dapper.

try:
```
killall firefox-bin
```
and start it up again.

---

### Post by Green White on 2007-07-20
Followed your step, but still the same.

   Nothing to kill in process in reply, restarted but still 1.5.0.12

   Do you think its a good idea if I uninstall and re-install it again via Synaptic?

---

### Post by Freddy on 2007-07-20
Just do a reinstall (it won't mess with your your bookmarks or config files.

In a terminal.
```
sudo aptitude reinstall firefox
```
I'm sure it's just a problem within the package, I remember this has happened before with Firefox.

If you want, you could always change the version inside about:config after you have reinstalled your Fox.

Open up your Fox and write:
```
about:config
```
Inside navigation bar.

Change your version string at the general.useragent.extra.firefox line (scroll down 60% of the page) Just right click over the version number and change it.

---

### Post by Green White on 2007-07-20
Will follow your advise. Anyway thanks for your time and patience.

---

