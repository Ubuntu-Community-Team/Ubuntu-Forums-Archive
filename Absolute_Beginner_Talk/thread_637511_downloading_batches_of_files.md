---
title: "downloading batches of files"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Condor2200 on 2007-12-11
I Installed Gutsy and ran the updater, and wget is broken. The program runs but it wont download anything from any websites. The command I tried to run was:
wget --output-file=wgetbrokelog -r -np -l1 -nd -A '*.mp3' [http://.](http://.)........

--02:17:18--  [http://www.lyrics-realm.com/mp3/t/the,cardigans/](http://www.lyrics-realm.com/mp3/t/the,cardigans/)
           => `index.html'
Resolving [www.lyrics-realm.com](www.lyrics-realm.com)... 87.230.27.40
Connecting to www.lyrics-realm.com|87.230.27.40|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.google.com/](http://www.google.com/) [following]
--02:17:19--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 64.233.167.99, 64.233.167.104, 64.233.167.147
Connecting to www.google.com|64.233.167.99|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    0K ....                                                    123.05 KB/s

02:17:19 (123.05 KB/s) - `index.html' saved [5115]

Removing index.html since it should be rejected.

FINISHED --02:17:19--
Downloaded: 5,115 bytes in 1 files

What am I doing wrong?

---

### Post by PeterJS on 2007-12-11
> **Condor2200 said:**
> 
HTTP request sent, awaiting response... **301 Moved Permanently**
Location: [http://www.google.com/](http://www.google.com/) [following]
--02:17:19--  [http://www.google.com/](http://www.google.com/)
           => `index.html'

*snip*

What am I doing wrong?


It doesn't look like you're doing anything wrong, it looks like they're intentionally redirecting all batch downloads to google.com, which clearly doesn't have what you're looking for and the wget rightly rejects the google search page as not being an mp3.

---

### Post by FuturePilot on 2007-12-11
Apparently none of those files are actually mp3s :o
Try one in the browser. Doesn't seem to work. You might want to try a different site or something.

---

