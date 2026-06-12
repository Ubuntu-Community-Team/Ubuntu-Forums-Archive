---
title: "Botched download"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by levigruber on 2006-07-25
I am trying to download a .deb file from [http://www.pandanet.co.jp/English/glgo/download.html](http://www.pandanet.co.jp/English/glgo/download.html)

When I click the link, and select save or open, it opens
download manager, but nothing happens. If I cancel and retry, firefox downloads 700-800 K and stops. Does anyone have a clue as to why?

Levi-:-k

---

### Post by aysiu on 2006-07-25
Have you tried *wget*? ```
wget -c http://www.pandanet.co.jp/English/glgo/downloads/glGo-1.4.deb
sudo dpkg -i glGo-1.4.deb
rm glGo-1.4.deb
```

---

### Post by levigruber on 2006-07-25
Thanks. Didn't work. Still just stopped.

---

### Post by aysiu on 2006-07-25
Then perhaps something's wrong with your internet connection (are you operating by proxy?)... I just did this a few seconds ago: ```
wget -c http://www.pandanet.co.jp/English/glgo/downloads/glGo-1.4.deb
--19:02:58--  http://www.pandanet.co.jp/English/glgo/downloads/glGo-1.4.deb
           => `glGo-1.4.deb'
Resolving www.pandanet.co.jp... 210.155.158.196
Connecting to www.pandanet.co.jp|210.155.158.196|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,638,020 (2.5M) [text/plain]

100%[====================================>] 2,638,020    145.49K/s    ETA 00:00

19:03:16 (142.06 KB/s) - `glGo-1.4.deb' saved [2638020/2638020]
```

---

