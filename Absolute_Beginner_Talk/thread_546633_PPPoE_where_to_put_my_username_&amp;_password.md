---
title: "PPPoE: where to put my username &amp; password?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2007-09-09
My ISP here in China has given me an ADSL modem, a password & a username that looks a bit like an email address. In windows I click PPPoE, put them in & it works. So what about Mint Xfce? I can't find anything in the two networking setup kinda things that looks like it might be right. Is windows doing something automatically that this can't, so I actually have to find out something about IP addresses etc? Thanks for any help.

PS- I'm using a restricted driver for the Lan module in this Asus U5. Also, the system seems to preternaturally know what updates are needed without having any connection set up & without being able to download said updates, or load anything in firefox.

---

### Post by njknight on 2007-09-09
Don't know if this helps, but a lot of modems store the username and password within the modem itself.  Normally you would enter something like [http://192.168.1.1](http://192.168.1.1) into the Internet web browser which would 'connect' you to the modems' internal management pages, where you can edit and enter your connection details (usually under something like WAN)  It depends though what modem you have.   Good luck, and I'm sure there are others on the board with greater knowledge who can help

---

### Post by dwhitney67 on 2007-09-09
> **njknight said:**
> Don't know if this helps, but a lot of modems store the username and password within the modem itself.  Normally you would enter something like [http://192.168.1.1](http://192.168.1.1) into the Internet web browser which would 'connect' you to the modems' internal management pages, where you can edit and enter your connection details (usually under something like WAN)  It depends though what modem you have.   Good luck, and I'm sure there are others on the board with greater knowledge who can help

I was going to post something along this line, but I do not believe that this is true.  My parents have ADSL (or as it is called in the US, DSL) service.  When I connected a Linksys router, then yes, what you have stated is correct.  All one has to do is configure the router to "play ball" with the ADSL modem.

However, if there isn't a router in place, then I believe that one has to massage the /etc/ppp/chap-secrets file or something similar.  But that is only a guess.

To the OP.... google for "Linux Howto ADSL PPPoE".

---

### Post by expatCM on 2007-09-09
normally you access the router by entering the IP the browser and entering the user name and password there as part of the set up process.

Your ISP will have given you a page of setup instructions although probably in Chinese.  Are you able to upload these instructions so that we may have a look?  Also your ISP will probably be able to give you a lot of support, I guess you are in Shanghai and from my own experience I know that the support can be very good and quality English is available on the end of the phone...

---

### Post by az on 2007-09-09
[https://help.ubuntu.com/community/ADSLPPPoE?highlight=%28adsl%29](https://help.ubuntu.com/community/ADSLPPPoE?highlight=%28adsl%29)

Many adsl modems are just modems and do not have a web configuration page.

You need to run

sudo pppoeconf

---

### Post by leetrefz on 2007-09-12
Thanks, I had tried 'sudo pppoeconfig' by mistake. Anyway, using a router now, works automatically.

---

