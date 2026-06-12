---
title: "Plone package not available"
date: 2006-11-20
forum: Apple PPC Users
---

### Post by amklinux on 2006-11-20
Hi.

I want to install Plone in my old Mac G4, but its package is not available in Edgy. Anyone knows how I could get it?

Thanks.

Adrovane.

---

### Post by stmiller on 2006-11-21
You could try fetching and installing these Debian .deb packages for Plone:

[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=plone&searchon=names&subword=1&version=unstable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=plone&searchon=names&subword=1&version=unstable&release=all)


Or easier perhaps add this line to your /etc/apt/sources.list

deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) unstable main contrib non-free

making sure to only apt-get install plone

and nothing else. Then comment out that line.

---

### Post by amklinux on 2006-11-21
Thanks, but no luck. There is only "plone-site" and a lot of zope* packages. Plone package is not available there.

Edit: I installed it by hand. Thanks, anyway.

---

