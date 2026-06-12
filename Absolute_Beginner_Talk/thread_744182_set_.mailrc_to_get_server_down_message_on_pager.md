---
title: "set .mailrc to get server down message on pager"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by opscure on 2008-04-04
.mailrc contains configuration options for your mail client, it won't allow you to create a pager service.  What you can use is kermit or the like.  An example of a script that utilizes kermit and calls the TAP protocol for paging can be found here:
[ftp://kermit.columbia.edu/kermit/f/ckepage.ksc](ftp://kermit.columbia.edu/kermit/f/ckepage.ksc)

I suppose you could use some sort of watchdog script or use a connected computer to host your script and ping your server every so often for a response.  If the ping/pong comes back with host cannot be found, etc. then run kermit script.  Follow?

Crash detection is not an easy thing to accomplish locally since your services are all shutting down and you will likely not find the time to send a message without the addition of some hardware technologies or complicated software.  

Hope this helps you.

---

