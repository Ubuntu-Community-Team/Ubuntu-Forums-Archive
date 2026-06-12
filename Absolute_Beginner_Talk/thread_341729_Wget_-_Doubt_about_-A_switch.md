---
title: "Wget - Doubt about -A switch"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by 09adi09 on 2007-01-19
I want to dowload files 5.mp3 and 6.mp3  out of somw 10 mp3 at a website.
(The files are numbered from 1 to 10)

I CANT do 
wget -r -l1 htttp://xyz/[5-6].mp3
because wget doesnt support globbing for HTTP retrievals...

So i tried,
wget -r -l1 -A "[5-6.mp3]" http:/xyz/  -ologmusic

This doesnt seem to work either.My logfile reads,

[I]Proxy request sent, awaiting response... 403 Forbidden
13:37:56 ERROR 403: Forbidden.

Removing xyz/index.html since it should be rejected.
unlink: No such file or directory

FINISHED --13:37:56--
Downloaded: 0 bytes in 0 files[/I]

I checked the index.html of that site and indeed it was giving a 404/403 error.

Q1) How do i do the download?
Q2) What is the deal with rejecting index.html? and why is index.html even coming into the picture here...

Best wishes from a learning newbie
:)

---

### Post by mikewhatever on 2007-01-19
Why don't you just download them with the web browser?

---

### Post by Ragazzo on 2007-01-19
```

wget http://xyz/{5..6}.mp3

```
is expanded by Bash to
```

wget http://xyz/5.mp3 http://xyz/6.mp3

```

The question about index.html I don't quite understand.

Edit: Sorry, now I see what index.html has to do with it. That's where wget looks for the links to download. If the files are not listed anywhere, wget cannot know about their existence.

---

### Post by 09adi09 on 2007-01-19
wget http://xyz/{5..6}.mp3

works just fine..

I guess I was doing [5-6] all along,which i a mistake..
Thanks for clarifying that :)

---

