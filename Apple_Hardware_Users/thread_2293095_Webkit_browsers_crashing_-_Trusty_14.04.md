---
title: "Webkit browsers crashing - Trusty 14.04"
date: 2015-09-02
forum: Apple Hardware Users
---

### Post by asmodeus3 on 2015-09-02
I am sure that other PPC users have stumbled upon this problem.
Web browsers using Webkit and its ports are unusable in 14.04.


  Midori : produces internal error, doesn't show up at all
Qupzilla : crashes on launch ( Qtwebkit problem ? see [here]("https://lists.debian.org/debian-qt-kde/2015/06/msg00146.html") )
Epiphany: crashes on launch


There is a reported bug [here]("https://bugs.launchpad.net/ubuntu/+source/qtwebkit-source/+bug/1274167") and [here]("https://bugs.launchpad.net/ubuntu/+source/webkitgtk/+bug/1432965") :
The known issues page says the bug has to do with* libjavascriptcoregtk-1.0.0*  and  *libjavascriptcoregtk-3.0.0 * and for Qupzilla it should be with* libqtwebkit4(?)*
Someone has uploaded a patched webkit for Trusty [here]("https://onedrive.live.com/?id=78C0847849FED8F1%21112&cid=78C0847849FED8F1&group=0&parId=root&authkey=%21AIxjisKGRA8_YNU&action=locate") but I'm not sure how to apply it. Any insight?

---

### Post by rican-linux on 2015-09-02
unzip the fold go into the directory and run this command

```
sudo dpkg *.deb
```

---

