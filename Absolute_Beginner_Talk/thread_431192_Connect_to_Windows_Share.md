---
title: "Connect to Windows Share"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-05-02
I was wondering if it is possible connect to a windows share from ubuntu that isnt available on my network, but instead on the Internet? If so, how can it be done?

---

### Post by jwbaker on 2007-05-02
Yes, you can do this.  Click on the "Places" menu.  Choose "Connect to Server".  Change the server type to "Windows share".  Type in the name or IP address of the server.  If you use the name, it can't be the fake windows name like "Joe's PC" it has to be the real, fully-qualified domain name of the computer, for example joespc.domain.com.

Good luck.

---

### Post by mevets on 2007-05-02
Awesome great little app.

How can I figure out what my "Server"(i think i know this one), "Share", and "Domain name" is?
Would the share look like: "\\nameofshare"?

---

### Post by jwbaker on 2007-05-02
Yeah, it would be "nameofshare", but without the slashes.  As far as the domain name, user, password, and all that junk, you'd have to ask the owner/operator of the computer.

Example: in Windows \\joespc.domain.net\nameofshare, in Linux server: joespc.domain.net, share: nameofshare.

My favorite GNOME trick: click on the Desktop.  Type Control-L.  For the location, type smb://joespc.domain.net/nameofshare.  It works great.

---

