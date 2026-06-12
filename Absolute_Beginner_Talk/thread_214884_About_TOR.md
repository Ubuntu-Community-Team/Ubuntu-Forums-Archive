---
title: "About TOR"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-07-13
Hi.
I've installed the TOR extension in FF. I've run again the browser and got the tor button enabled. But at this point I've got this message from FF: :confused: 
the proxy server is refusing connections.
Check the proxy settings to make sure that they are correct.
Contact your network administrator to make sure the proxy server is
    working.

](*,) 
What can I do? Any hint?
I've checked it out in the forum, but nothing was useful.

Thanks in advance

---

### Post by orb9220 on 2006-07-13
That sounds to me like Privoxy isn't running. 
In Terminal, try running "ps ax|grep privoxy" and see if it shows privoxy as running. You can do "sudo /Library/StartupItems/Privoxy/Privoxy start" to start it.

[http://en.wikipedia.org/wiki/HTTP_proxy](http://en.wikipedia.org/wiki/HTTP_proxy)

---

### Post by doancm2003 on 2006-07-13
try this link

[http://ubuntuforums.org/showthread.php?t=95527&highlight=tor+privoxy](http://ubuntuforums.org/showthread.php?t=95527&highlight=tor+privoxy)

---

### Post by helphope on 2006-07-14
:) Thanks a lot for answering

> That sounds to me like Privoxy isn't running. 

yeah. That's right. I didn't know of the existence of Privoxy

> try this link

[http://ubuntuforums.org/showthread.php?t=95527&highlight=tor+privoxy](http://ubuntuforums.org/showthread.php?t=95527&highlight=tor+privoxy)

I checked it out, but I don't know where to add the following line: " forward-socks4a / localhost:9050 . " (with the dot at the end)  in the file. Maybe at the end? :confused: :confused: 

thanks in advance

---

### Post by j-strap2 on 2006-07-18
> **helphope said:**
> :) Thanks a lot for answering



yeah. That's right. I didn't know of the existence of Privoxy



I checked it out, but I don't know where to add the following line: " forward-socks4a / localhost:9050 . " (with the dot at the end)  in the file. Maybe at the end? :confused: :confused: 

thanks in advance

You can add the line anywhere in the config file - I just add it to the top.

---

