---
title: "Firefox: where is the about:config file stored?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-05-21
I want to backup my about:config settings, where is the file that stores it?

---

### Post by henriquemaia on 2006-05-21
[quote=tux101]I want to backup my about:config settings, where is the file that stores it?[/quote]

I think you mean this file:

prefs.js

Look for it in 
 
/home/**your_user**/.mozilla/firefox/**orws2gsm**.default

The second bold it's just highlight that the name can be something different from that, but look for the folder with the **default** name on it.

---

### Post by macdo on 2006-05-21
Have a look in your .mozilla/firefox folder in your home directory. It should be in your default account (a folder with a random name, soemthing like kjdhf12d.default. The file you are looking for is called prefs.js. (The .mozilla varies depending on your installation - it could be.firefox, .mozilla-firefox, .mozilla-ubuntu)

I suggest you read this page: [http://www.mozilla.org/unix/customizing.html#prefs](http://www.mozilla.org/unix/customizing.html#prefs)

---

