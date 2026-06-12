---
title: "xchat fserve help"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by tgpo on 2006-04-15
I've used xchat through x11 on the osx side of my computer, but recently have tried to work with Ubuntu.  I run the obsidian+ fserve script, which I have set to work on port 6200 - 6300.  I have those ports forwarding to me on the router, and have confirmed it works correctly on the os x side.

My problem is it seems that xchat on Ubuntu does not respond to those ports.  I've looked around on how to open those ports, but have found nothing of use.  I'm unsure if I did indeed open those ports and that wasn't the problem, or if those ports are still closed.

Has anyone else configured Ubuntu to work with xchat and obsidian?  What am I missing?  It seems that this would have been so much easier than it was under x11 in OS X.

---

### Post by tgpo on 2006-04-18
It seems the people on the xchat forums don't know much about Ubuntu.  Any help?

---

### Post by htinn on 2006-04-18
Settings/Preferences/Network/File transfers "First DCC send port" and "Last DCC send port" is what you're looking for.

---

### Post by tgpo on 2006-04-18
Are you refering to xchat there?  Because that's not what I'm refering to.  I have those ports already set in xchat and on the router, but it seems that Ubuntu itself is blocking the use of those ports.

---

### Post by htinn on 2006-04-18
So, set a policy to listen on those ports using Firestarter.

---

### Post by tgpo on 2006-04-18
[QUOTE=htinn]So, set a policy to listen on those ports using Firestarter.[/QUOTE]

Firestarter.  I'll give it a try when I get home.  Thanks htinn.

---

### Post by tgpo on 2006-04-18
That did it!  Thanks again!

---

### Post by SA6 on 2008-04-04
Hi..I am trying the same thing. I don't know what service to enable on firestarter.

---

