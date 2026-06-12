---
title: "very quick web server question 8080 to 80"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by larrybrazos on 2007-03-16
i have a quick web server question . . .

i have port 8080 open and forwarded to my server and /etc/apache2/ports.conf listening to 8080.
i can access my server at WANIP:8080
i have a registered domain pointing to my WANIP.

i want to access my server from my domain name.

how do i get port 80 internet requests to pull up my server.

what do i need to edit?
apache2.conf?
router configuration?
ports.conf?

thanks!  i have been wrestling with this monster for weeks, and i am soooooo close!

---

### Post by stuartindigo on 2007-03-16
Its more a case of either your router configuration, or what your provider permits.

If you are now running on 8080, this is normally done because yr ISP doesn't permit you to run a server on port 80 (and all his up-line routers block this traffic).

You will need to set yr router to forward port80 to yr server (assuming this is open at yr ISP)

You will probably need to change yr .conf files as well (i'm not a linux expert, so I don't know the details).

Stuart

---

### Post by larrybrazos on 2007-03-19
i don't think there is any free way to do this.  from what i could find, you have to use a premium service from somewhere like dyndns or no-ip.  i tried to find somewhere in my godaddy control panel to forward port 80 requests to WANIP:8080, but couldn't find anything like that.  dyndns has some type of "my webhop" service, but it is not free.

if anyone discovers a free way to do this, let me know.

---

