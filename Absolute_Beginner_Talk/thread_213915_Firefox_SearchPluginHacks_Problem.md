---
title: "Firefox SearchPluginHacks Problem"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Hexx on 2006-07-11
Well I installed the SearchPluginHacks extension for Firefox, but for some reason when I try to delete a search engine from the list, it doesn't work. It asks me to confirm the deletion, and I click "OK" but nothing happens.

Do I need to do this sort of thing via a sudo command instead?

---

### Post by skull_leader on 2006-07-11
Yeah, that's exactly what you have to do. Namely:

> sudo firefox

And then remove the search engines you want out of there.

---

### Post by Hexx on 2006-07-12
> **skull_leader said:**
> Yeah, that's exactly what you have to do. Namely:



And then remove the search engines you want out of there.

Well I tried sudo firefox but it brings up what appears to be a clean install of firefox, thus no SearchPluginHacks extension is installed for use, so I can't remove any search engines...

Any other ideas?

---

### Post by wyohermit on 2006-07-12
You can do it manually by deleting the files for each search engine you want to remove. 

/usr/lib/firefox/searchplugins/"searchengine name".src

/usr/lib/firefox/searchplugins/"searchengine name".gif

Ken

---

### Post by Hexx on 2006-07-13
> **wyohermit said:**
> You can do it manually by deleting the files for each search engine you want to remove. 

/usr/lib/firefox/searchplugins/"searchengine name".src

/usr/lib/firefox/searchplugins/"searchengine name".gif

Ken

Yeah, I ended up doing it manually.

Is there any way to make it so Firefox isn't so locked down?

---

### Post by aysiu on 2006-07-13
There are two sets of searchplugins--one is the standard set in /usr/lib/firefox/searchplugins.

The other is specific to your user, and it's in /home/hexx/.mozilla/firefox/*profilename*/searchplugins

The first you need to be root to modify. The second you can modify as user because they're your plugins.

And please do not do *sudo firefox*.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Hexx on 2006-07-13
> **aysiu said:**
> There are two sets of searchplugins--one is the standard set in /usr/lib/firefox/searchplugins.

The other is specific to your user, and it's in /home/hexx/.mozilla/firefox/*profilename*/searchplugins

The first you need to be root to modify. The second you can modify as user because they're your plugins.

And please do not do *sudo firefox*.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Ah, thanks for that tip. I'll need it later.

---

