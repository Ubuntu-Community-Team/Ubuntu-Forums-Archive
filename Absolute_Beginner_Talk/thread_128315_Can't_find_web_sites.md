---
title: "Can't find web sites"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by fredtal on 2006-02-11
The Alert I get in Firefox is "www.google.com could not be found.  Please check the name and try again."  I'm guessing I have some kind of DNS problem but I don't know how to fix it.  

I'm a 2 day old Ubuntu user, so be gentle.  
Thanks, Fred

---

### Post by heimo on 2006-02-11
Do you know your DNS servers? If you're dual booting (Windows), you can check these by going to command line and running ```
ipconfig /all
``` (or /a - can't remember), and then comparing the results (DNS server ip addresses) to what you have on System->Administration->Networking->DNS tab.

---

### Post by Lord Illidan on 2006-02-11
Can you ping sites like

```
ping google.com
``` 
Also, try disabling ipv6 in firefox. Just type ```
about:config
``` in the URL bar and search for ipv6.

---

### Post by fredtal on 2006-02-11
Thanks all, it was my DNS server.  btw I was able to ping google.com and ipv6 is set to false.  That was pretty easy to fix, maybe I can get the hang of Linux, and kiss Win good bye.

---

