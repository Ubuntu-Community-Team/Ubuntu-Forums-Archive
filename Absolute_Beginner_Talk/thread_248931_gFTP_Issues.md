---
title: "gFTP Issues"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Panic36 on 2006-09-01
Well I used the package manager to install gFTP, and I'm guessing from what I've searched with google for Gnome FTP clients for Ubuntu, gFTP seems to be a standard... Well I've come from using windows a week ago, and I do a lot of FTP work to my server i get from ipower... Basically I've been having issues where connection stops, and I've never had isseus before with FTP'ing and ipower support says they don't know the issue so this has been very difficult... they just tell me everything is fine for them, and they can dl perfectly via FTP from the server... Here are the FTP logs bellow, I was hoping someone could help me figure out the issue.. I'm running a Router, which I have ports 20-21 open, TCP/UDP, I run a IRCD server, with ports, 6667, and a HTTPD server on this PC with port 80, everything else works PERFECTLY, however soem reason I can't figure this out... I have however, removed the router and connected the modem directly to the PC and still get the same issue...I thank everyone for their support, I'm sorry I'm new to LInux, and I switched because Microsofts constant lock ups, and crashes were getting on my nerves..

me to Pure-FTPd [TLS] ----------
220-You are user number 3 of 50 allowed.
220-Local time is now 17:20. Server port: 21.
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
USER aliandad

331 User aliandad OK. Password required
PASS xxxx
230-User aliandad has group access to:  aliandad
230 OK. Current restricted directory is /
SYST

215 UNIX Type: L8
TYPE I

200 TYPE is now 8-bit binary
CWD /public_html

250 OK. Current directory is /public_html
PORT 192,168,0,2,231,62

200 PORT command successful
REST 220896

350 Restarting at 220896
RETR /public_html/resized.mp4

150-Connecting to port 59198
150 1668.9 kbytes to download
Connection to aliandadele.com timed out
Disconnecting from site aliandadele.com
Could not download /public_html/resized.mp4 from aliandadele.com
Error: Remote site aliandadele.com disconnected. Will reconnect in 30 seconds
Looking up aliandadele.com
Trying aliandadele.com:21
Connected to aliandadele.com:21
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 5 of 50 allowed.
220-Local time is now 17:23. Server port: 21.
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
USER aliandad

331 User aliandad OK. Password required
PASS xxxx
230-User aliandad has group access to:  aliandad
230 OK. Current restricted directory is /
SYST

215 UNIX Type: L8
TYPE I

200 TYPE is now 8-bit binary
CWD /public_html

250 OK. Current directory is /public_html
PORT 192,168,0,2,209,143

200 PORT command successful
REST 429336

350 Restarting at 429336
RETR /public_html/resized.mp4

150-Connecting to port 53647
150 1465.3 kbytes to download
Connection to aliandadele.com timed out
Disconnecting from site aliandadele.com
Could not download /public_html/resized.mp4 from aliandadele.com
Error: Remote site aliandadele.com disconnected. Will reconnect in 30 seconds
Looking up aliandadele.com
Trying aliandadele.com:21
Connected to aliandadele.com:21
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 5 of 50 allowed.
220-Local time is now 17:25. Server port: 21.
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
USER aliandad

331 User aliandad OK. Password required
PASS xxxx
230-User aliandad has group access to:  aliandad
230 OK. Current restricted directory is /
SYST

215 UNIX Type: L8
TYPE I

200 TYPE is now 8-bit binary
CWD /public_html

250 OK. Current directory is /public_html
PORT 192,168,0,2,176,126

200 PORT command successful
REST 642480

350 Restarting at 642480
RETR /public_html/resized.mp4

150-Connecting to port 45182
150 1257.2 kbytes to download
Connection to aliandadele.com timed out
Disconnecting from site aliandadele.com
Could not download /public_html/resized.mp4 from aliandadele.com
Error: Remote site aliandadele.com disconnected. Will reconnect in 30 seconds
Looking up aliandadele.com
Trying aliandadele.com:21
Connected to aliandadele.com:21
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 4 of 50 allowed.
220-Local time is now 17:28. Server port: 21.
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
USER aliandad

331 User aliandad OK. Password required
PASS xxxx
230-User aliandad has group access to:  aliandad
230 OK. Current restricted directory is /
SYST

215 UNIX Type: L8
TYPE I

200 TYPE is now 8-bit binary
CWD /public_html

250 OK. Current directory is /public_html
PORT 192,168,0,2,219,107

200 PORT command successful
REST 892288

350 Restarting at 892288
RETR /public_html/resized.mp4

150-Connecting to port 56171
150 1013.2 kbytes to download
Connection to aliandadele.com timed out
Disconnecting from site aliandadele.com
Could not download /public_html/resized.mp4 from aliandadele.com
Error: Remote site aliandadele.com disconnected. Will reconnect in 30 seconds
Looking up aliandadele.com
Trying aliandadele.com:21
Connected to aliandadele.com:21
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 4 of 50 allowed.
220-Local time is now 17:31. Server port: 21.
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
USER aliandad

331 User aliandad OK. Password required
PASS xxxx
230-User aliandad has group access to:  aliandad
230 OK. Current restricted directory is /
SYST

215 UNIX Type: L8
TYPE I

200 TYPE is now 8-bit binary
CWD /public_html

250 OK. Current directory is /public_html
PORT 192,168,0,2,162,69

200 PORT command successful
REST 1215776

350 Restarting at 1215776
RETR /public_html/resized.mp4

150-Connecting to port 41541
150 697.3 kbytes to download
Connection to aliandadele.com timed out
Disconnecting from site aliandadele.com
Could not download /public_html/resized.mp4 from aliandadele.com
Error: Remote site aliandadele.com disconnected. Will reconnect in 30 seconds

---

### Post by sitedesign on 2006-10-01
I would suggest disabling IPV6 on your system see this link for instructions:
[http://www.ubuntuforums.org/showthread.php?t=87798&](http://www.ubuntuforums.org/showthread.php?t=87798&)

Let me know if this helps.

Short of that if the server is a Linux server then can you access the server via SSH. If so then you can mount the server via SSH in your fstab file so that the server is always available and you will be able to edit the files online. You need some extra packages to mount SSH file shares.

---

