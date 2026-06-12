---
title: "help with festival text to speech"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Hranj on 2006-08-24
ive installed festival through the terminal with
```
sudo apt-get install festival
```

i run festival in the terminal and i was told that the command to say something is "say" without the quotes. when i type this i get this error message.

```
dhranj@dhranj-desktop:~$ festival
Festival Speech Synthesis System 1.4.3:release Jan 2003
Copyright (C) University of Edinburgh, 1996-2003. All rights reserved.
For details type `(festival_warranty)'
festival> say "talk to me already"
SIOD ERROR: unbound variable : say

```

anyone know how i can fix this or if im even doing this right.

---

### Post by meng on 2006-08-24
Might want to google for some documentation, e.g.
[http://software.newsforge.com/article.pl?sid=05/06/14/192226](http://software.newsforge.com/article.pl?sid=05/06/14/192226)

---

### Post by skalsky on 2008-01-23
Take a look at the below howto:

[https://help.ubuntu.com/community/TextToSpeech](https://help.ubuntu.com/community/TextToSpeech)

But try to start festival
```
festival
```
and then the following line at the festival console
```
(SayText "Hello")
```

hope this helps..

---

