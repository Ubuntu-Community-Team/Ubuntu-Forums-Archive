---
title: "NX Server connection issues.."
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by wildatsun on 2007-06-12
Hello everyone.

1st off I am new to Ubuntu and this forum is helping a lot, thank you!

I have installed nxserver as detailed here - 

[http://easylinux.info/wiki/Ubuntu_dapper#Remote_Desktop_Access_via_NX](http://easylinux.info/wiki/Ubuntu_dapper#Remote_Desktop_Access_via_NX)

But I get the following error when I connect via NX-windows-client -

NX> 203 NXSSH running with pid: 1276
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 172.16.245.31 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-22 - LFE
NX> 105 Hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: admin
NX> 102 Password: ******
NX> 103 Welcome to: NS-CRM-WEB user: admin
NX> 105 Listsession --user="admin" --status="suspended\054running" --geometry="1280x1024x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: admin
NX> 105 Start session with: --link="lan" --backingstore="1" --streaming="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="1" --mediahelper="esd" --session="NS-CRM-WEB" --type="unix-gnome" --geometry="1024x768" --client="winnt" --keyboard="pc102\057gb" --screeninfo="1024x768x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 8CE6D1F8. To get detailed information about
NX> 595 ERROR: the error search for the string 8CE6D1F8 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Ignoring EOF on the monitored channel
NX> 280 Ignoring CLOSE on the monitored channel
Killed by signal 15.

---

### Post by wildatsun on 2007-06-12
and if I look at /var/log/messages is says -

Jun 12 12:04:19 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: User 'admin' logged in from '172.16.235.25'. 'NXLogin:set'
Jun 12 12:04:22 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: Selected node host:localhost with port:22 'main:selectNode'
Jun 12 12:04:22 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: Current selected node: localhost is in status: running  'main:selectNode'
Jun 12 12:04:25 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: nxssh process exited with '255' 'NXNodeExec:exec'
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 ERROR: NXNODE Ver. 2.1.0-22  (Error id e656FFA) [e656FFA] 'main:nxnode:2725'
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 ERROR: Tue Jun 12 12:04:26 2007 running as user: 'admin' (uid: 1000) on '' [e656FFA] 'main:$
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 ERROR: in node start session: create session: run commands [e656FFA] 'main:nxnode:2725'
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 ERROR: execution of last command failed [e656FFA] 'main:nxnode:2725'
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/admin/.nx/C-NS-CRM-WEB-1002-6ADD0$
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 exit value: 1 [e656FFA] 'main:nxnode:2725'
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 stdout:  [e656FFA] 'main:nxnode:2725'
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 stderr: xauth:  error in locking authority file /home/admin/.Xauthority [e656FFA] 'main:nxn$
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 . [e656FFA] 'main:nxnode:2725'
Jun 12 12:04:26 NS-CRM-WEB NXNODE 2.1.0-22[8089]: ERROR: NX> 596 init: stdin arguments: user=admin,userip=172%2e16%2e235%2e25,uniqueid=6ADD082D0526EA77781C8$
Jun 12 12:04:27 NS-CRM-WEB NXNODE 2.1.0-22[8089]: INFO: getting agent pid: cannot read pid file '/home/admin/.nx/C-NS-CRM-WEB-1002-6ADD082D0526EA77781C8663E$
Jun 12 12:04:27 NS-CRM-WEB NXNODE 2.1.0-22[8089]: INFO: directory '/home/admin/.nx/C-NS-CRM-WEB-1002-6ADD082D0526EA77781C8663E52390E7' moved into '/home/adm$
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NX> 596 ERROR: NXNODE Ver. 2.1.0-22  (Error id e656FFA)
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NX> 596 ERROR: Tue Jun 12 12:04:26 2007 running as user: 'admin' (uid: 10$
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NX> 596 ERROR: in node start session: create session: run commands
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NX> 596 ERROR: execution of last command failed
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/admin/.$
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NX> 596 exit value: 1
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NX> 596 stdout:
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NX> 596 stderr: xauth:  error in locking authority file /home/admin/.Xaut$
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NX> 596 init: stdin arguments: user=admin,userip=172%2e16%2e235%2e25,uniq$
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NXNodeExec:exec('startsession', 'user=admin&userip=172%2e16%2e235%2e25&u$
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NXShell:handler_session_start('--link="lan" --backingstore="1" --streami$
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NXShell:handle_command('startsession', '--link="lan" --backingstore="1" $
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) NXShell:run() called at nxserver.pl line 4534
Jun 12 12:04:27 NS-CRM-WEB NXSERVER 2.1.0-22[8071]: ERROR: (exception id C724D404) eval {...} called at nxserver.pl line 4493
Jun 12 12:05:11 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: User 'admin' logged in from '172.16.235.25'. 'NXLogin:set'
Jun 12 12:05:14 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: Selected node host:localhost with port:22 'main:selectNode'
Jun 12 12:05:14 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: Current selected node: localhost is in status: running  'main:selectNode'

and...

---

### Post by wildatsun on 2007-06-12
Jun 12 12:05:17 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: nxssh process exited with '255' 'NXNodeExec:exec'
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 ERROR: NXNODE Ver. 2.1.0-22  (Error id e61C23E) [e61C23E] 'main:nxnode:2725'
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 ERROR: Tue Jun 12 12:05:18 2007 running as user: 'admin' (uid: 1000) on '' [e61C23E] 'main:$
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 ERROR: in node start session: create session: run commands [e61C23E] 'main:nxnode:2725'
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 ERROR: execution of last command failed [e61C23E] 'main:nxnode:2725'
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/admin/.nx/C-NS-CRM-WEB-1003-7C20C$
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 exit value: 1 [e61C23E] 'main:nxnode:2725'
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 stdout:  [e61C23E] 'main:nxnode:2725'
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 stderr: xauth:  error in locking authority file /home/admin/.Xauthority [e61C23E] 'main:nxn$
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 . [e61C23E] 'main:nxnode:2725'
Jun 12 12:05:18 NS-CRM-WEB NXNODE 2.1.0-22[8143]: ERROR: NX> 596 init: stdin arguments: user=admin,userip=172%2e16%2e235%2e25,uniqueid=7C20C897CB6C764B190AA$

---

### Post by wildatsun on 2007-06-12
and...

Jun 12 12:05:19 NS-CRM-WEB NXNODE 2.1.0-22[8143]: INFO: getting agent pid: cannot read pid file '/home/admin/.nx/C-NS-CRM-WEB-1003-7C20C897CB6C764B190AA6E45$
Jun 12 12:05:19 NS-CRM-WEB NXNODE 2.1.0-22[8143]: INFO: directory '/home/admin/.nx/C-NS-CRM-WEB-1003-7C20C897CB6C764B190AA6E45D0C5E61' moved into '/home/adm$
Jun 12 12:05:19 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: (exception id 8CE6D1F8) NX> 596 ERROR: NXNODE Ver. 2.1.0-22  (Error id e61C23E)
Jun 12 12:05:19 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: (exception id 8CE6D1F8) NX> 596 ERROR: Tue Jun 12 12:05:18 2007 running as user: 'admin' (uid: 10$
Jun 12 12:05:19 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: (exception id 8CE6D1F8) NX> 596 ERROR: in node start session: create session: run commands

---

### Post by wildatsun on 2007-06-12
Jun 12 12:05:19 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: (exception id 8CE6D1F8) NX> 596 ERROR: execution of last command failed
Jun 12 12:05:19 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: (exception id 8CE6D1F8) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/admin/.$
Jun 12 12:05:19 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: (exception id 8CE6D1F8) NX> 596 exit value: 1
Jun 12 12:05:19 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: (exception id 8CE6D1F8) NX> 596 stdout:
Jun 12 12:05:19 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: (exception id 8CE6D1F8) NX> 596 stderr: xauth:  error in locking authority file /home/admin/.Xaut$
Jun 12 12:05:19 NS-CRM-WEB NXSERVER 2.1.0-22[8125]: ERROR: (exception id 8CE6D1F8) NX> 596 init: stdin arguments: user=admin,userip=172%2e16%2e235%2e25,uniq$

*[COLOR="DarkGreen"](sorry I had to split the log but the system would not let me paste as one as it saw it as images !?!?!)[/COLOR]*

[B].. I am so close I think as it says authenticated and connecting but then fails?

Any help is SO needed, thank you.[/B]

---

### Post by lazyart on 2007-06-12
[http://www.bananus.dk/2006/09/30/xauth-error-in-locking-authority-file/](http://www.bananus.dk/2006/09/30/xauth-error-in-locking-authority-file/)

Use sudo.

---

### Post by wildatsun on 2007-06-12
Thank you but that did not work "**xauth -b quit**", now I get -

Jun 12 15:25:24 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: User 'admin' logged in from '172.16.235.25'. 'NXLogin::set'
Jun 12 15:25:27 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: Selected node host:localhost with port:22 'main::selectNode'
Jun 12 15:25:27 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: Current selected node: localhost is in status: running  'main::selectNode'
Jun 12 15:25:30 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 ERROR: NXNODE Ver. 2.1.0-22  (Error id eA5D186) [eA5D186] 'main:nxnode:27$
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 ERROR: Tue Jun 12 15:25:31 2007 running as user: 'admin' (uid: 1000) on '$
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 ERROR: in node start session: create session: run commands [eA5D186] 'mai$
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 ERROR: execution of last command failed [eA5D186] 'main:nxnode:2725'
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/admin/.nx/C-NS-$
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 exit value: 1 [eA5D186] 'main:nxnode:2725'
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 stdout:  [eA5D186] 'main:nxnode:2725'
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 stderr: xauth:  /home/admin/.Xauthority not writable, changes will be ign$
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 . [eA5D186] 'main:nxnode:2725'
Jun 12 15:25:31 NS-CRM-WEB NXNODE 2.1.0-22[5322]: ERROR: NX> 596 init: stdin arguments: user=admin,userip=172%2e16%2e235%2e25,uniqueid=B84$
Jun 12 15:25:32 NS-CRM-WEB NXNODE 2.1.0-22[5322]: INFO: getting agent pid: cannot read pid file '/home/admin/.nx/C-NS-CRM-WEB-1006-B846DA4$
Jun 12 15:25:32 NS-CRM-WEB NXNODE 2.1.0-22[5322]: INFO: directory '/home/admin/.nx/C-NS-CRM-WEB-1006-B846DA44C8F8B9D970F3759E28D3A5DE' mov$
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NX> 596 ERROR: NXNODE Ver. 2.1.0-22  (Error id eA5D186)
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NX> 596 ERROR: Tue Jun 12 15:25:31 2007 running as user$
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NX> 596 ERROR: in node start session: create session: r$
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NX> 596 ERROR: execution of last command failed
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NX> 596 last command: /bin/bash --login -c 'xauth -v so$
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NX> 596 exit value: 1
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NX> 596 stdout:
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NX> 596 stderr: xauth:  /home/admin/.Xauthority not wri$
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NX> 596 init: stdin arguments: user=admin,userip=172%2e$
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NXNodeExec::exec('startsession', 'user=admin&userip=172$
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NXShell::handler_session_start('--link="lan" --backings$
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NXShell::handle_command('startsession', '--link="lan" -$
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) NXShell::run() called at nxserver.pl line 4534
Jun 12 15:25:32 NS-CRM-WEB NXSERVER 2.1.0-22[5304]: ERROR: (exception id 1B902AC2) eval {...} called at nxserver.pl line 4493

As I said it says -
[LIST]
[*]Connected to xx.xx.xx.xx
[*]Authentication Completed
[*]*Then it says* Server configuration error... (but I still don't know why it is failing).
[/LIST]

Thank you!!!

---

### Post by wildatsun on 2007-06-12
when I run **sudo xauth** i am now shown -

"**xauth:  error in locking authority file /home/admin/.Xauthority**"

Now when I ran "sudo startx" I am shown errors -

[B]xauth:  creating new authority file /home/admin/.serverauth.6102

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  Server error.[/B]

Thank you.

---

### Post by wildatsun on 2007-06-13
Hello now "sudo xauth" does not give an error, but still when I connect it looks ok and then if fails, the messages log shows -

Jun 13 13:09:52 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: User 'admin' logged in from '172.16.235.25'. 'NXLogin::set'
Jun 13 13:09:54 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: Selected node host:localhost with port:22 'main::selectNode'
Jun 13 13:09:54 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: Current selected node: localhost is in status: running  'main::selectNode'
Jun 13 13:09:56 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 ERROR: NXNODE Ver. 2.1.0-22  (Error id eFB734C) [eFB734C] 'main:nxnode:2725'
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 ERROR: Wed Jun 13 13:09:58 2007 running as user: 'admin' (uid: 1000) on '' [eFB734C] 'main:$
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 ERROR: in node start session: create session: run commands [eFB734C] 'main:nxnode:2725'
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 ERROR: execution of last command failed [eFB734C] 'main:nxnode:2725'
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/admin/.nx/C-NS-CRM-WEB-1018-6F08A$
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 exit value: 1 [eFB734C] 'main:nxnode:2725'
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 stdout:  [eFB734C] 'main:nxnode:2725'
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 stderr: xauth:  /home/admin/.Xauthority not writable, changes will be ignored [eFB734C] 'ma$
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 . [eFB734C] 'main:nxnode:2725'
Jun 13 13:09:58 NS-CRM-WEB NXNODE 2.1.0-22[4379]: ERROR: NX> 596 init: stdin arguments: user=admin,userip=172%2e16%2e235%2e25,uniqueid=6F08A0BADD017D3A29DF3$
Jun 13 13:09:59 NS-CRM-WEB NXNODE 2.1.0-22[4379]: INFO: getting agent pid: cannot read pid file '/home/admin/.nx/C-NS-CRM-WEB-1018-6F08A0BADD017D3A29DF39F6D$
Jun 13 13:09:59 NS-CRM-WEB NXNODE 2.1.0-22[4379]: INFO: directory '/home/admin/.nx/C-NS-CRM-WEB-1018-6F08A0BADD017D3A29DF39F6D7706B82' moved into '/home/adm$
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NX> 596 ERROR: NXNODE Ver. 2.1.0-22  (Error id eFB734C)
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NX> 596 ERROR: Wed Jun 13 13:09:58 2007 running as user: 'admin' (uid: 10$
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NX> 596 ERROR: in node start session: create session: run commands
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NX> 596 ERROR: execution of last command failed
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/admin/.$
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NX> 596 exit value: 1
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NX> 596 stdout:
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NX> 596 stderr: xauth:  /home/admin/.Xauthority not writable, changes wil$
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NX> 596 init: stdin arguments: user=admin,userip=172%2e16%2e235%2e25,uniq$
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NXNodeExec::exec('startsession', 'user=admin&userip=172%2e16%2e235%2e25&u$
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NXShell::handler_session_start('--link="lan" --backingstore="1" --streami$
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NXShell::handle_command('startsession', '--link="lan" --backingstore="1" $
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) NXShell::run() called at nxserver.pl line 4534
Jun 13 13:09:59 NS-CRM-WEB NXSERVER 2.1.0-22[4361]: ERROR: (exception id F6D6894E) eval {...} called at nxserver.pl line 4493

anyone any ideas?

---

### Post by wildatsun on 2007-06-13
Found the problem -

xauth:  /home/admin/.Xauthority not writable, changes will be ignored

so I amended the folder security with -

sudo chmod -R 0777 /home/admin/.Xauthority

and now I connect ok :p

---

