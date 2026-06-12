---
title: "Blocking websites"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-01-10
Is there anything in ubuntu like windows host files in wich I can block websites like these:

127.0.0.1 adwords.google.com #[Gmail ads]
127.0.0.1 pagead.googlesyndication.com
127.0.0.1 pagead2.googlesyndication.com #[Google AdWords]
127.0.0.1 adservices.google.com
127.0.0.1 ssl.google-analytics.com
127.0.0.1 [www.google-analytics.com](www.google-analytics.com) #[Google Analytics]
127.0.0.1 imageads.googleadservices.com #[TrackingCookie.Googleadservices]
127.0.0.1 imageads1.googleadservices.com
127.0.0.1 imageads2.googleadservices.com
127.0.0.1 imageads3.googleadservices.com
127.0.0.1 imageads4.googleadservices.com
127.0.0.1 imageads5.googleadservices.com
127.0.0.1 imageads6.googleadservices.com
127.0.0.1 imageads7.googleadservices.com
127.0.0.1 imageads8.googleadservices.com
127.0.0.1 imageads9.googleadservices.com
127.0.0.1 [www.googleadservices.com](www.googleadservices.com)
127.0.0.1 show.googleadsenseagent.com
127.0.0.1 [www.googlecaches.com](www.googlecaches.com)

And besides google what other websites like those should I block (the ones that track you and slow your internet down)

Even ubuntuforums has googleanalytics.

I searched the internet a bit but didn't find any concrete ways to do so.

Thanks.

---

### Post by Hospadar on 2008-01-10
If you are looking to block ads, look into the addblock plus extension for firefox, I havn't seen a flash ad in years thanks to that.  It will also allow you to add your own filters to block anything from a given url (or anything with a domain name that matches a certain pattern like *google* would block anything with "google" in the name)

Just search for addblock plus firefox addons, it'll probably be the first link.

If you are looking to speed up your browsing, you might also look into the fasterfox addon, it will pre-fetch links (if you want) and I think it also does some multi-connection page loading type stuff

---

### Post by philinux on 2008-01-10
I used adblock to block

*google-analytics*

---

### Post by HermanAB on 2008-01-10
/etc/hosts

---

### Post by PeterJS on 2008-01-10
Adblock + NoScript + Allowing cookies on a per domain basis is the way to go for keeping junk off your machine. That said the hosts file on linux machines is located at /etc/hosts

---

### Post by billgoldberg on 2008-01-10
Thanks guys.

I knew about adblock but since I use other browsers most of the time I needed to be pointed to etc/hosts

---

### Post by Linuxratty on 2008-01-10
You can also go into your browser's preferences and uncheck Java and java script.
 Just remember to re check java script when you go to places like yahoo mail.

---

