---
title: "the new tor update"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2006-09-28
todays (maybe yesterdays) update (via the little orange icon by the time/date) added TOR to my system.

as i understand TOR is an anonymous internet tool.

after the update, is tor now up and running? or do i have to set it up in order browse anonymously?

---

### Post by gborzi on 2006-09-28
You have to install and configure privoxy, see here [http://tor.eff.org/docs/tor-doc-unix.html.en](http://tor.eff.org/docs/tor-doc-unix.html.en) . Moreover you also need to configure your browser.

---

### Post by pbaehr on 2006-09-28
I'm pretty sure once Tor is installed it automatically starts running as a daemon.

In order to use it, though, you need to tell your browser to connect through it via proxy.

I believe you will want to point your proxy to 127.0.0.1:9050 which, if you're not familiar with IP addresses and such means port 9050 of your computer.

If you visit the tor website (tor.eff.org) you will find some info about testing whether or not Tor is functioning, as well as a more detailed step by step for setting it up.

EDIT: Right! I left out the privoxy step. Good thing gborzi was responding at the same time.

---

