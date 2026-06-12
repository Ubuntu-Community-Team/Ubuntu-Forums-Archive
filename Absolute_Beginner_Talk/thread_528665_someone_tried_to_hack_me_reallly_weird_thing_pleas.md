---
title: "someone tried to hack me? reallly weird thing please read.."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by threeonethree on 2007-08-18
i was just browsing some sites then i got a dialog box that said "ip  blah blah is trying to view your desktop would u allow?" somethin like that .. i clicked no . went into remote sharing thingy and turned it off.. i just turned it on yesterday to check something then mayb forgot to turn it off..wtf .. that ip was from my own country . i dont have any friends who know my ip . my ip changes everytime i reconnect to the internet so wtf happned? somebody is doing port scans on port 0 or something? please im worried.. can it be a trojan? i uninstalled firestarter yesterday because it would block some ports .. please hlep

---

### Post by guguma on 2007-08-18
It must be a fake message from the website you were on. The warning message was on the browser window right?

Do not worry about trojan horses, I do not know any who can execute under linux.

If it is about remote access, I do not know if there is a warning message but it would be a warning message from the system via a GUI dialog box, not from a browser window.

---

### Post by steve.horsley on 2007-08-18
Well, I guess you left "Allow other users to view your desktop" enabled, and a bot somewhere found the open port and tried it. I also guess that had you allowed it to connect, it would have made a note of your address for more detailed examination by a real live hacker somewhere. It's best not to leave these services open unless you want them , just in case there's a vulnerability that allows them to bypass the security.

---

### Post by threeonethree on 2007-08-18
thanks for replies.. it was not inside the browser window , but a dialog box popped up.. also the dialog box had the ip same as my ISP . my isp has ip starting from 59.94 something and it had same.. :confused:

---

### Post by finer recliner on 2007-08-18
possible theory:

whatever client you used to remote desktop to you personal computer from last time remembered the previous session's settings (including your IP). so whoever opened up the remote destkop client after you, saw your IP filled in and decided to try to connect to you for some fun.

---

### Post by threeonethree on 2007-08-18
i did not connect from anywhere to my computer using the default ubuntu client. any my ip changes like 5 times a day..   it was definately a scan , or a trojan or virus installed on my computer. i dont think someone having my isp connection will have ubuntu and also be trying to hack ubuntu people

---

### Post by guguma on 2007-08-19
I was totally wrong. There are some trojans working in linux. My mistake, sorry :(

[http://www.symantec.com/security_response/writeup.jsp?docid=2003-062018-4739-99](http://www.symantec.com/security_response/writeup.jsp?docid=2003-062018-4739-99)
[http://www.symantec.com/security_response/writeup.jsp?docid=2003-011412-3316-99](http://www.symantec.com/security_response/writeup.jsp?docid=2003-011412-3316-99)
[http://www.theregister.co.uk/2001/09/07/linux_trojan_spotted/](http://www.theregister.co.uk/2001/09/07/linux_trojan_spotted/)

It may be the trojan.linux.typo

Do you have an 'r 'file or an 'a' somewhere.

i do not think it is .jbellz (but that is dangerous) did you download a suspicious mp3 file?

Anyway it is weird.

---

