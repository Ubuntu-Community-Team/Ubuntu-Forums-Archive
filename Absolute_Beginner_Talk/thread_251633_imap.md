---
title: "imap"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by damonlab on 2006-09-05
I installed Ubuntu 6.06 as a LAMP server and am running PHP version 5.1.2.  I set up the Eventum 1.7.0 helpdesk trouble ticket software on it.  Eventum has been working great, but now I want it to talk with my Exchange2003 server so I can get it to make new trouble tickets via email.  One of the prereqs for that is to get imap working.  I installed imap via the terminal command "apt-get install courier-imap".  After installation, Eventum does not recognize that imap is installed.  My phpinfo() page makes no mention of imap.  If I run "apt-get install courier-imap" again, I get the message "courier-imap is already the latest version".  

Do I need to configure something with courier-imap to get PHP or Eventum to recognize it?  Do I need to install imap in some other way?

---

