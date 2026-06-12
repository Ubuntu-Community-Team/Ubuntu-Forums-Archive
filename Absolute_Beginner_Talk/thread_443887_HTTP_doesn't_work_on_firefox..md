---
title: "HTTP doesn't work on firefox."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by JCakeC on 2007-05-14
Hello ppl,

I have this strange behaviour in Firefox. I can't load HTTP over it!. I can load HTTPS fie, but not HTTP. I can access HTTP everywhere else (lynx, update manager, etc). I have deleted and reinstalled firefox with no luck, I have also tried everything in firefox config and no luck.

Once again, My network is running smoothly, but Firefox and HTTP. Should I try using another browser that is not mozilla flavoured to try it out? if so, wich do you recomend? most of what I've found relly on mozilla engine, thus no luck on HTTP.

also... changing subjects, Every multimedia I run on my 3 fiesty installs (mp3, avis, mkvs) have skips when I play them... 

any ideas on how to fix any of those problems?

thanks in advanced.

---

### Post by oilchangeguy on 2007-05-14
> **JCakeC said:**
> Hello ppl,

I have this strange behaviour in Firefox. I can't load HTTP over it!. I can load HTTPS fie, but not HTTP. I can access HTTP everywhere else (lynx, update manager, etc). I have deleted and reinstalled firefox with no luck, I have also tried everything in firefox config and no luck.

Once again, My network is running smoothly, but Firefox and HTTP. Should I try using another browser that is not mozilla flavoured to try it out? if so, wich do you recomend? most of what I've found relly on mozilla engine, thus no luck on HTTP.

also... changing subjects, Every multimedia I run on my 3 fiesty installs (mp3, avis, mkvs) have skips when I play them... 

any ideas on how to fix any of those problems?

thanks in advanced.

this makes no sense. what are you trying to do?
i'm not sure if you know what http is. so read this:
[http://en.wikipedia.org/wiki/HTTP](http://en.wikipedia.org/wiki/HTTP)

---

### Post by JCakeC on 2007-05-15
Thanks oilchangeguy, I know what HTTP is, and it is as weird as it sounds... If you want it more explicitly, firefox cannot conenect to a server over port 80(the HTTP DEFAULT PORT), even though I can connect to port 80 on all other ways: using lynx, TELNET(yes, I can use telnet to reproduce HTTP requests), the connections to Ubuntu Update (wich connects to HTTP on port 80 )

So the idea is simple... port 80 is restricted in firefox (the HTTP DEFAULT PORT) and other ports are open... (e.g. HTTPS or 443).....

---

### Post by trak87 on 2007-05-15
Is FF configured to use a proxy? If so, turn it off, or on, whatever the case may be.

To test http you could open a terminal and run something like this to retrieve a page:

```
wget http://ubuntuforums.org
```

---

### Post by JCakeC on 2007-05-15
trak87,

i have tested all configurations with FF, and no luck. I can use wget with no problems (i forgot to add it to the list of programs that worked fine)... the only app that doesn't load HTTP (port 80) is FF.

---

### Post by trak87 on 2007-05-15
You could try this:

Close FF.

Move the prefs.js file out of the Firefox directory located at ~/.mozilla/firefox/xxxxxxxx.default/prefs.js . (Replace xxxxxxxx with whatever the directory name actually is.)

Start FF and test. If it works, redo your FF settings as needed.



If that doesn't work, you could move or delete the entire ~/.mozilla/firefox directory and retest.

---

### Post by JCakeC on 2007-05-16
Trak,

I deleted the folder, I even uninstalled and deleted Firefox from the system, deleted everything that was left (some configurations) and reinstalled and couldn't get it to work. I am on Ubuntu right now, but using Opera.

I want to solve the problem now, as it has become a "quest". It's weird I can use everything but  FF. Everytime I want load I get the Connection was Reset page now. but if I load pages over https I can load them fine. 

any other ideas?

---

### Post by Pcniatic on 2007-05-17
I have the same problem but using my laptop at college. Opera works fine, and i also download firefox directly from getfirefox.com and it works too(but it has font's problems). No idea why ubuntu's firefox is not working.

EDIT: This post solved my problem ([http://ubuntuforums.org/showthread.php?t=430855](http://ubuntuforums.org/showthread.php?t=430855)). Good luck :)

---

### Post by JCakeC on 2007-05-17
> **Pcniatic said:**
> I have the same problem but using my laptop at college. Opera works fine, and i also download firefox directly from getfirefox.com and it works too(but it has font's problems). No idea why ubuntu's firefox is not working.

EDIT: This post solved my problem ([http://ubuntuforums.org/showthread.php?t=430855](http://ubuntuforums.org/showthread.php?t=430855)). Good luck :)

TYVM. Solved my problem.

---

