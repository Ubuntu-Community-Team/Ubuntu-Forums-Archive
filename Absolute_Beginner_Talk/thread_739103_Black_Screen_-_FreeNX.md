---
title: "Black Screen - FreeNX"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-03-29
Using NXSEVER, I get a Black Screen when I remotely log in to my Ubuntu PC.  I was able to remote in until yesterday.  I have another user account that works as it should.  The NOMACHINE website states that this is a issue with GNOME and to remove Gnome config and tmp files.

I found somewhere to rm -r -f /tmp/* to delete temporary files but that does not work for me.

I found that some said to SSH into the PC and issue ...
  $ DISPLAY=localhost:1004
  $ gnome-session
... but that did not work for me either.

I note that there are a lot of "Black Screen" posts on the web and NOMACHINE states that it is a GNOME problem.

Anyone have any insights?

Thanks

Carl

---

### Post by cwmoser on 2008-03-29
This Q/A appears on the NOMACHINE website:

My connection to my Linux desktop is fine, but I get only a blackscreen inside my NX session. What could I do?

You need to verify if there are stale sockets and temporary files left by some
GNOME or KDE applications in the /tmp directory and in your home. If there are any, you need to manually delete them to allow the X application to start.

It has been noticed that X applications, including GNOME and KDE desktop, may leave temporary files, such as gconf or DCOP files, which prevent the application from starting. Usually this occurs when the application was closed abruptly, for example due to a power outage.

The same behaviour occurs both when accessing the server machine locally and when you try to access the machine by means of NX, and can't be considered a NX specific issue.

( [http://www.nomachine.com/ar/view.php?ar_id=AR01F00501](http://www.nomachine.com/ar/view.php?ar_id=AR01F00501) )

What does it mean by "stale sockets" and gconf or DCOP files???

Carl

---

### Post by cwmoser on 2008-04-03
**When I use NOMACHINES NXClient to remote into my Ubuntu PC, I get:**

[COLOR="Navy"]Setting up the environment
Connected to xxxxx.com
Waiting authentication
Authentication complete
Downloading Session Information.

Server configuration error.  Cannot log in.
Please contact your system administrator.

Details:
NX> 203 NXSSH running with pid: 4784
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XX.XXX.XXX.XX on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.1.0-5 - LFE
NX> 105 Hello NXCLIENT - Version 3.1.0
NX> 134 Accepted protocol: 3.1.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: carlo
NX> 102 Password: ********
NX> 103 Welcome to: klaatu user: carlo
NX> 105 Listsession --user="carlo" --status="suspended\054running" --geometry="1600x1200x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: carlo
NX> 105 Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="KLAATU" --type="unix-gnome" --geometry="1600x1170" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1600x1170x32+render" 
[B]NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 42213D64. To get detailed information about
NX> 595 ERROR: the error search for the string 42213D64 in the system log[/B]NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15[/COLOR]

[B]Any ideas on why?

Thanks

Carl[/B]

---

