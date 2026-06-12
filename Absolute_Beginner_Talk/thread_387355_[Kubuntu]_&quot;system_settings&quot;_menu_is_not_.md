---
title: "[Kubuntu] &quot;system settings&quot; menu is not listening to me"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Crakie on 2007-03-18
I'm running Kubuntu Edgy, fully up to date. When I go to "system settings" and change preferences, most of them are implemented just fine. A couple of them are not however. The same goes for using KControl. The changes are saved - or appear to be - but the behavior of the system is unchanged.

Examples of the ones that don't work:
- Device icons on the desktop. I don't want them, but the external HDD and what not keep showing up despite me changing the appropiate settings.
- Default browser. Clicking on a link in Thunderbird results in starting Konqueror, not Firefox. Clicking on a mail adress in Firefox results in... well... nothing. I would like thunderbird to start though. This when 'default applications' clearly show I want Thunderbird and Firefox to be the default mail app and browser, respectively.

I tried running the configuration managers as root - that doesn't make a difference.

Any ideas on how to solve this?

---

### Post by Jucato on 2007-03-18
1. I'm not sure how this works. I've tried it myself and find things not to be working as they should. Probably a bug...

2. The problem here is that the settings for the Default Browser in System Settings really only affect KDE apps, since it's a KDE setting. And since Thunderbird isn't a KDE app, it doesn't know that you set KDE to use Firefox as the default browser. You have to enter this command in Konsole so that all X (GUI) apps will use Firefox as the browser:

```
sudo update-alternatives --configure x-www-browser
```

This will give you a list of available browsers, so choose the number for Firefox.

As for Firefox using Thunderbird by default, I think Firefox has its own settings for that, somewhere in about:config most probably.

Hope that helps.

---

### Post by Crakie on 2007-03-18
Thanks, Jucato. Your solution for the default browser works, except I needed to use "--config" instead of "--configure". Still no solution for the mail client though... can't find anything in the about:config.

---

### Post by Crakie on 2007-03-18
I did some more research, and I had to add a line to about:config myself, following [this link]("http://kb.mozillazine.org/Default_mail_client").

---

