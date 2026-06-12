---
title: "Tor searches only in German"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-11-02
With Tor enabled in Firefox, I can't do:

[www.google.com](www.google.com)

instead, I get:

[www.google.de](www.google.de)

the German "version" of Google. 

Anybody know how to "fix" this?

---

### Post by EdThaSlayer on 2006-11-02
Change the proxy server you use for the tor network. The proxy server you are using is located in Germany,thus you get the german version of google.If you use Foxyproxy or Privoxy you should be able to change proxy servers easily.

---

### Post by pbaehr on 2006-11-02
Also, it will be different from time to time depending on what country your exit node is located in. Google is automatically redirecting you to their German page because they see you as located in Germany. You can also just go into the preferences for Google and select English if it comes up in a foreign language. I'm not sure if it will save that preference in a cookie or not, though.

---

### Post by Mark_in_Hollywood on 2006-11-07
OK

I've looked all over the Applications/sub-menus, including Debian/Apps/System/ for my

Privoxy

and can't find a program to invoke. 

Opening a terminal and sudo privoxy returns nothing to configure or change.

Please tell me where the secret privoxy control panel is.

---

