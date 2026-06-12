---
title: "Can a server discriminate against a specific OS?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by loswr86 on 2007-07-22
I am having trouble communicating with a professor, and I have a feeling it has to do with running ubuntu. His email address is associated with the school district he works for, and I cannot access any of the school district pages with firefox in ubuntu. MS firefox works fine, Mac fine. Ok, so the school district servers are blocking linux for some reason. 

The question is why can't I email the guy using my gmail account? It seems to me the school district servers shouldn't be able to determine the OS of an email coming from google? right? He doesn't receive any emails I send if I use my Ubuntu desktop. 

Any insight will be appreciated.

---

### Post by p_quarles on 2007-07-22
It's possible that your mail is getting caught in the server's spam filter. Ask him to have your e-mail address whitelisted (he'll either be able to do this himself, or ask the sysadmin to do so).

If this is the case (and I can't think of any other possibility), you may want to contact the server's administrator yourself, and ask them what kind of filtering mechanisms could be catching these e-mails. If they are filtering by an OS-related tags, they're being really dumb.

---

### Post by loswr86 on 2007-07-22
He receives my email if I am using a windows browser or a mac browser, gmail each time. The only difference is when I use ubuntu. 

Weird huh?

---

### Post by nitro_n2o on 2007-07-22
Interesting... maybe this school thinks that all linux users are crackers :) looool.. 
try turning off the javascript in firefox this will beat them if they use a javascript to determine your OS

---

### Post by buzzmandt on 2007-07-22
what about using a browser mail client?

---

### Post by p_quarles on 2007-07-22
Hmm. I just sent myself an e-mail from my gmail account, via the web interface, in Firefox, with all javascript allowed, and there were no headers clearly indicating either the OS or the browser. Either the information is encrypted/scrambled, or it's not there at all. 

One really basic troubleshooting test you might try is to send someone an e-mail from Firefox in Linux, and then see if the e-mail appears in your outbox.

---

### Post by w4ett on 2007-07-22
1 Try using the Agent Switcher Extension for Firefox...You can ID your Browser as IE7....Even works on Microsoft Sites.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

2.  Some Network managers as a matter of course, block ALL Web based Email clients to minimize the risk of Spam and Virus/Trojan infection.  don't take it personally, it just the nature of the security precautions that the .edu managers have to take using Microsoft based servers and networks.

---

### Post by p_quarles on 2007-07-22
> **w4ett said:**
> 1 Try using the Agent Switcher Extension for Firefox...You can ID your Browser as IE7....Even works on Microsoft Sites.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

2.  Some Network managers as a matter of course, block ALL Web based Email clients to minimize the risk of Spam and Virus/Trojan infection.  don't take it personally, it just the nature of the security precautions that the .edu managers have to take using Microsoft based servers and networks.
Both of those items are true, but I'm guessing neither are the problem, since the OP was able to use Firefox on both Windows and Mac OS X to send messages via gmail's web interface.

@loswr86: Seriously, I would contact the administrator(s) of the district's network, and ask them if they know of any anti-spam measures that could be blocking your Linux e-mails. I mean, if everything else is going through okay, and your Linux Firefox is working correctly, then it is very likely a problem with their server.

---

### Post by loswr86 on 2007-07-23
Thank you folks. I just successfully attempted to reach the schools district site after switching my user agent to the google bot. :) 

Now I'll try emailing with this little trickery.

---

### Post by loswr86 on 2007-07-23
And if any of you were wondering, He does receive the emails sent from gmail while I'm using windows or OS X, All of the "missing" emails are showing up in my outbox, and the offending site is forbidden from running java script on my browser. Although I gave it permission to allow java after the site wouldn't load.

---

### Post by Ripfox on 2007-07-23
wack server

---

