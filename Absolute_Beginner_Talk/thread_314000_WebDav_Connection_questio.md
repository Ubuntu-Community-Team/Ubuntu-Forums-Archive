---
title: "WebDav Connection questio"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by l.j. on 2006-12-06
Hi all i made a webDav connection to my web server mounted the web folder fine but when i double click it. it opens firefox and says no program associated with Dav any ideas would be great thnx

---

### Post by Terry of Astoria on 2006-12-17
I have the same problem.

---

### Post by heatpumpcontrol on 2007-07-28
bump

---

### Post by Jargon64 on 2007-08-17
same problem here :( having trouble finding a solution too

---

### Post by euler_fan on 2007-08-17
Running Gnome I use the the "Connect to Server" interface under the "places" menu. Then select WebDAV from the drop down menu and fill in the details. 

One note: don't include "http://" or "https://"

For example:

If I have a webDAV which I would get to as a webfolder at [http://mywebdav.com/myfolder/](http://mywebdav.com/myfolder/)

I would put that into the server dialogue one of two ways:

1) server: mywebdav.com/myfolder/

or) server: mywebdav.com/
      folder: myfolder

Anything I didn't specify, leave blank (unless the port is a special one, then it's probably a good idea to set that).

Hope that helps.

---

