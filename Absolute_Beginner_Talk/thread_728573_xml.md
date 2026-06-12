---
title: "xml?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by mfederwi on 2008-03-19
I setup a ubuntu lamp server and it is running php and mysql apps and everything is working ok.  Another developer has now given me some xml, xsl and css files to put on the server.  I am completely new to xml, so please excuse my ignorance.  He showed me the files on his computer and they displayed correctly.  What do I need to do to the server to get them to display to browsers hitting the server?

---

### Post by ruy_lopez on 2008-03-19
> **mfederwi said:**
> I setup a ubuntu lamp server and it is running php and mysql apps and everything is working ok.  Another developer has now given me some xml, xsl and css files to put on the server.  I am completely new to xml, so please excuse my ignorance.  He showed me the files on his computer and they displayed correctly.  What do I need to do to the server to get them to display to browsers hitting the server?

Place the files under the webserver document root (usually /var/www/). Just copy them to "/var/www/" and point your browser at "localhost", and you should see a list of files. If any of the files is named "index", say "index.xml", the browser will not list the files, it'll just open index.xml.

To view the files from another system, give the browser the IP address of the computer running the server.

To view from a computer outside your network, you have to enable port forwarding, and setup a domain name (a dynamic domain usually does the trick). Best leave that until you are sure everything is secure.

---

### Post by mfederwi on 2008-03-19
Thanks for the reply.  I had things setup as you suggested.  The file does display, but lists xml code rather than the intended appearance.  Perhaps I am missing a css file.

---

### Post by njparton on 2008-03-19
Do you have apache up and running to serve them?

---

### Post by ruy_lopez on 2008-03-19
> **mfederwi said:**
> Thanks for the reply.  I had things setup as you suggested.  The file does display, but lists xml code rather than the intended appearance.  Perhaps I am missing a css file.

Yes, sounds like you are missing an xsl file (xsl is css for xml).

---

