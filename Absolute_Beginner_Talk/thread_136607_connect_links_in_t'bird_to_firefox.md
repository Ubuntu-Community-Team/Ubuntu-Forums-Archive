---
title: "connect links in t'bird to firefox?"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-02-26
i can't seem to figure it out. i have both in 1.5 versions. also, when i click on 'check to see if firefox is default', nothing happens.

---

### Post by Pragmatist on 2006-02-26
What are you trying to do?  Have the bookmarks in one show up in the other automatically?  Because, if you you want to do it manually you can just go into the bookmark manager and choose Export.  Then switch to $HOME/.mozilla  (I'm not sure what t'bird is, but it might have a directory like $HOME/.tbird  or whatever.  The key is that it is a hidden directory under your home directory that contains all of the preferences/configurations.  Backup whatever bookmarks.html file is there (mine is at $HOME/.mozilla/firefox/default.qwo/bookmarks.html)  and then copy the one you exported in the same location as the old one.

If it were me, I would "TRY":

1. locate bookmarks.html
2. pick the two files that I need (one corresponding to firefox, the other to t'bird)
3. back both files up
4. link the files using  ln -s  path/to/firefox/bookmarks.html bookmarks.html  In this case I would type that in t'bird's directory.  Obviously you could just reverse the names throughout if you want the link inside firefox's directory and the actual inside t'bird.

Hope it works.

---

### Post by aysiu on 2006-02-26
[This](http://www.ubuntuforums.org/showthread.php?t=60427) may help.

---

### Post by Coelocanth on 2006-02-26
[QUOTE=Pragmatist]What are you trying to do?  Have the bookmarks in one show up in the other automatically?  Because, if you you want to do it manually you can just go into the bookmark manager and choose Export.  Then switch to $HOME/.mozilla  (I'm not sure what t'bird is, but it might have a directory like $HOME/.tbird  or whatever.  The key is that it is a hidden directory under your home directory that contains all of the preferences/configurations.  Backup whatever bookmarks.html file is there (mine is at $HOME/.mozilla/firefox/default.qwo/bookmarks.html)  and then copy the one you exported in the same location as the old one.

If it were me, I would "TRY":

1. locate bookmarks.html
2. pick the two files that I need (one corresponding to firefox, the other to t'bird)
3. back both files up
4. link the files using  ln -s  path/to/firefox/bookmarks.html bookmarks.html  In this case I would type that in t'bird's directory.  Obviously you could just reverse the names throughout if you want the link inside firefox's directory and the actual inside t'bird.

Hope it works.[/QUOTE]

T'bird is (I assume) the Thunderbird e-mail client.

---

### Post by fuscia on 2006-02-26
so far, adding the following to my thunderbird pref.js hasn't worked for me...

```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```

i did check to see if */usr/bin/firefox* opens firefox and it does.

---

### Post by pebs on 2006-02-28
[QUOTE=fuscia]so far, adding the following to my thunderbird pref.js hasn't worked for me...

```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```

i did check to see if */usr/bin/firefox* opens firefox and it does.[/QUOTE]

I tried that same thing but simply writing "firefox" in both http and https handlers and it worked, good luck! :)

---

### Post by fuscia on 2006-03-02
this is the error message i get "run-mozilla.sh: Cannot execute /opt/firefox/mozilla-firefox-bin", even if i set links up to open in dillo.

---

### Post by Pragmatist on 2006-03-02
Could it have to do with permissions?

---

### Post by fuscia on 2006-03-02
[QUOTE=Pragmatist]Could it have to do with permissions?[/QUOTE]

i doubt it. i'm guessing it has more to do with upgrading to 1.5 versions of both and the name changes that went along with the upgrades, but i really don't know.

---

