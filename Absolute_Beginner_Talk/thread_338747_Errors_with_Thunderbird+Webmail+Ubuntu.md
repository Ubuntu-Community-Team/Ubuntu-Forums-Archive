---
title: "Errors with Thunderbird+Webmail+Ubuntu"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by theicyj on 2007-01-14
I am running Ubuntu 6.10 on two different computers.  I have [Thunderbird]("http://www.mozilla.com/en-US/thunderbird/") installed on both, along with the [Webmail]("http://webmail.mozdev.org") extension.  For some reason I cannot get the webmail extension to work on either computer.  When I go to Tools -> Extensions -> Webmail -> Preferences -> Status,  the status for both pop and smtp is "error", with no further explaination.  I have tried other ports to no avail.  Has anyone else had this problem and been able to fix it?

---

### Post by theicyj on 2007-01-14
Well I found the answer at [http://www.linuxquestions.org/questions/showthread.php?p=2563998]("http://www.linuxquestions.org/questions/showthread.php?p=2563998") for anyone else who runs into this problem.   It seems ports below 1024 are blocked, setting the ports to a number above 1024 fixes the problem.

---

### Post by mdsmedia on 2007-01-14
What does the webmail extension do in Thunderbird? (now that you've got it working). Is it to read things like gmail and hotmail in Thunderbird?

---

### Post by theicyj on 2007-01-22
Yeah, it is used to get messages from Hotmail, Yahoo, Gmail, and other web mail services.

---

### Post by AmandaKerik on 2007-02-01
I had the error issue with webmail when I first did it - mainly because I didn't really read the instructions ... once I set the pop3 port to 1111 and the smtp to 1112, it worked fine.

Just be aware that it'll only download what's in your inbox unless you add the names of your folders to it. It also downloads hundreds at a time (I'm amazed I didn't get a 999 error from yahoo - too many connections in a short amount of time).

All in all, read the simple instructions and it works really well!

---

