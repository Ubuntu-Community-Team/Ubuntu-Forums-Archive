---
title: "what are the free VNC server for MS Windows that work with Ubuntu"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by linuxcity on 2006-04-30
I'm wondering of where I can download a version of free VNC Server for Windows that is comparable with the "Terminal Client Server" that comes with Ubuntu Dapper?

---

### Post by cilynx on 2006-04-30
[http://www.realvnc.com/]("http://www.realvnc.com/")

Does everything I need

---

### Post by linuxcity on 2006-04-30
I got this error " VNC viewer version 3.3.7- built feb 20...VNC connection failed: server license key is missing, invalid or has expired. Visit [http://www.realvnc.com](http://www.realvnc.com) to purchase a license."

I downloaded a Free version, do I need a license for this?

---

### Post by cilynx on 2006-04-30
You installed from here?
[http://www.realvnc.com/products/free/4.1/download.html]("http://www.realvnc.com/products/free/4.1/download.html")

Run the VNC server on the XP box.  The free version is GPL, no reason you should have to pay for it.  I've never had it ask me for a license.

Which machine / what program threw your error?

---

### Post by linuxcity on 2006-04-30
I got that version, and installed on the XP box, when I tried to connect from Dapper using VNC protocol, I got that message.

I checked the Firewall on XP, and it allows VNC server. However, I can't ping from the Linux box to its ip, but the XP can ping my Linux box.  XP w/ SP2  firewall may block pinging.

---

### Post by cilynx on 2006-04-30
From your previous post, you're using the "Terminal Client" thing.  Try using xvnc4viewer.  It's in the repositories and works well for me.

---

### Post by linuxcity on 2006-04-30
@ubuntu:~$ xvnc4viewer

VNC viewer for X version 4.0 - built Apr 19 2005 04:20:29
Copyright (C) 2002-2004 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Sun Apr 30 02:11:32 2006
 CConn:       connected to host 192.168.10.3 port 5900
 CConnection: Server supports RFB protocol version 3.3
 CConnection: Using RFB protocol version 3.3
 main:        Server license key is missing, invalid or has expired.
Visit
              [http://www.realvnc.com](http://www.realvnc.com) to purchase a licence.

---

### Post by linuxcity on 2006-04-30
I'm sorry, I downloaded the Enterprise edition. It works fine after I reinstalled with the right version. Thanks for all the help.

---

