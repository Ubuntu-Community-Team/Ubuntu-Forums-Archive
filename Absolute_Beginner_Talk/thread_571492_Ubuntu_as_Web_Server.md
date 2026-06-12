---
title: "Ubuntu as Web Server"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by dfatovic on 2007-10-09
I have our company web server running on Ubuntu 7.04 that was setup by a former employee.  I am able to do the very basic administration to it, and upload new web pages, but have a few questions.

1.  Where are the website files located on the server, and how does Ubuntu take the external request to view the website and display?

2.  Can the same server host multiple websites and distinguish between requests for each?  ie, when the request is made to view one, it doesn't show the wrong one?

I think that is it for now, if there are some usefull links or information, I would greatly appreciate it.

Thanks.

---

### Post by arbulus on 2007-10-09
1. The website files are found in /var/www.  In order for the webserver to receive requests, your router/gateway must be configured to forward requests on Port 80 to the IP address of the webserver machine.  

If this web server machine is on a LAN with private servers and workstations, it's always recommended that the webserver machine be in a "Demilitarized Zone" so that if it is compromized, your other machines will still be safe.   The DMZ would be configured at the router.  

2. Yes, it is possible.  Here's a link that has some pretty good information: 
[http://www.heritage-tech.net/336/setting-up-multiple-apache-local-web-sites-on-your-computer/](http://www.heritage-tech.net/336/setting-up-multiple-apache-local-web-sites-on-your-computer/)

---

### Post by dfatovic on 2007-10-09
Thanks, that is some good information.  Yes, we have port 80 forwarded to the Ubuntu Box.  It is on a LAN, but not part of the domain.

Thanks again.

---

### Post by arbulus on 2007-10-09
You're quite welcome.

I'm glad I could help.

---

### Post by hyper_ch on 2007-10-09
well, for hosting multiple websites I can recommend using ISPConfig... have a look over at [www.howtoforge.com](www.howtoforge.com)   --> it has simple step-by-step copy'n'paste tutorials where you end up having a ISP-style setup of your server with working email, ftp, websites, administration and so on

---

