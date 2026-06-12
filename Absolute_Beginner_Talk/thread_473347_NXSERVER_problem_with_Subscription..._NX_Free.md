---
title: "NXSERVER: problem with Subscription... NX Free"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by pcpete on 2007-06-13
Hello all! Ubuntu has been running wonderfully and a big thanks to this forum. I have had tons of trouble getting NX going... from dependencies to not getting v2.0 clients to work with FreeNX...

I have installed official NoMachine,com NXSERVER successfully, but I get an error when trying to connect to a local 192.168.1.117 port 22 server:


**The problem lies with NXNODE reporting a mismanaged subscrition,, I haven't seen documents anywhere. Seems like server is okay. heres the NX client log. Scroll all the way down. Auth works perfect: **

NX> 203 NXSSH running with pid: 7511
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.120 on port: 22
NX> 211 The authenticity of host '192.168.1.120 (192.168.1.120)' can't be established.
RSA key fingerprint is 8a:11:a6:3e:f9:2d:ac:47:e7:4e:51:40:58:6f:06:e1.
Are you sure you want to continue connecting (yes/no)? 
Failed to add the host to the list of known hosts (/home/pete/.ssh/known_hosts).
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 2.1.0-22 - LFE
NX> 105 Hello NXCLIENT - Version 2.1.0
NX> 134 Accepted protocol: 2.1.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: pete
NX> 102 Password: *******
NX> 103 Welcome to: allamerican user: pete
NX> 105 Listsession --user="pete" --status="suspended\054running" --geometry="1024x768x24+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: pete
NX> 105 Start session with: --link="adsl" --backingstore="1" --streaming="1" --nodelay="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="gnome" --type="unix-gnome" --geometry="800x600+112+59" --client="linux" --keyboard="pc105\057us" --screeninfo="800x600x24+render" 
NXSERVER - Version 2.1.0-22 - LFE
Wed Jun 13 23:45:33 2007 running as user: 'nx' (uid: 1001, pid: 7519) on 'allamerican'
Info: user login is pete (NXShell)
Info: user password is '******' (NXShell)
Info: using 'sshd authentication' (NXShell)
Info: selected user 'pete' is authenticated (NXNodeExec)
Info: password for selected user is in 'text' mode (NXNodeExec)
Info: preferred auth method is '' (NXNodeExec)
Info: selected NX Node with host name 'localhost', port '22' (NXNodeExec)
Info: selected publickey method to login NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l pete localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 7533 (NXNodeExec)
Info: received data in out channel from NX Node: 'NX> 204 Authentication failed.
' (NXNodeExec)
Error: received message 'Authentication Failure' from nxssh (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 1) (NXNodeExec)
Error: failed to authenticate on NX Node (NXNodeExec)
Info: trying next authentication method. (NXNodeExec)
Info: selected NX Node with host name 'localhost', port '22' (NXNodeExec)
Info: selected password method to login NX Node (NXNodeExec)
Info: now retrying to authenticate with 'password' on NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l pete localhost -p 22 -x -2 -o 'PasswordAuthentication yes' -o 'PubkeyAuthentication no' -o 'RhostsAuthentication no' -o 'RSAAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 7536 (NXNodeExec)
Info: received data in out channel from NX Node: 'NX> 205 pete@localhost's password: ' (NXNodeExec)
Info: received request for password from nxssh, user password sent (NXNodeExec)
Info: received data in out channel from NX Node: '
' (NXNodeExec)
Info: Removing not recognized buffer from stdout:[
] (NXNodeExec)
Info: received data in out channel from NX Node: 'NX> 618 Your evaluation period has expired. Please visit
NX> 618 the NoMachine Web site at [http://www.nomachine.com/](http://www.nomachine.com/)
NX> 618 to acquire a valid subscription.
' (NXNodeExec)
Info: received data in out channel from NX Node: 'NX> 690 Bye.
' (NXNodeExec)
Info: NX Node out channel was closed (NXNodeExec)
Info: Removing not recognized buffer from stdout:[] (NXNodeExec)
Info: NX Node err channel was closed (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 0) (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
Killed by signal 15.

---

### Post by pcpete on 2007-06-13
Furthermore, here is the output of server status. Everything checks out. **Anyone run into the subscription problem?** I saw a gentoo thread which stated uninstall and reinstall (tired that with .DEBs with no avail)
[B]
pete@allamerican:~$ sudo /usr/NX/bin/nxserver --status[/B]
NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.
**pete@allamerican:~$ sudo /usr/NX/bin/nxnode --status**
NX> 618 Your evaluation period has expired. Please visit
NX> 618 the NoMachine Web site at [http://www.nomachine.com/](http://www.nomachine.com/)
NX> 618 to acquire a valid subscription.
NX> 690 Bye.

---

### Post by pcpete on 2007-06-14
I am puzzled why I am having trouble getting nxserver running... I have got this package running on a 32bit P4 w/ HT but no go on my own AMD64. 

I used: 

dpkg -i --force-archetecture nxclient
dpkg -i --force-archetecture nxnode
dpkg -i --force-archetecture nxserver

And still run into a problem with NODE SUBSCRIPTION. The files I have played with are node.lic in the /usr/NX/bin/etc folder.... Maybe NX forum is a better place for this question, but here are some links consulted:

[http://www.nomachine.com/ar/view.php?ar_id=AR10D00424](http://www.nomachine.com/ar/view.php?ar_id=AR10D00424)
[http://www.nomachine.com/ar/view.php?ar_id=AR08D00411](http://www.nomachine.com/ar/view.php?ar_id=AR08D00411)

Anyone :) ?

---

### Post by pcpete on 2007-06-14
still no go... anyone have any experiance with this? I will try changing my node.lic file when back at home. But for the time being, I havent figured out the problem with the AMD64 install. 


I am on NX now on a work machine installed the same way!

---

### Post by illusions77 on 2007-06-20
I have the same issue, but on OpenSuse 10.2. I thought this was free software..... :( Hopefully i can find a solution.

---

### Post by praekon on 2007-06-27
Hi!

In the Release Announcement you can find a passage in the text:

> NX  Server 3.0 Free Edition and evaluation

NX Server Free Edition is a free-forever version of the NX Server including all the features of the other versions, but limited to a maximum of 2 concurrent users.

NX Node and Server packages provide an evaluation license for 30 days, named respectively /usr/NX/etc/node.lic and /usr/NX/etc/server.lic that will be activated during the installation procedure. Note that any further upgrade of the server will not renew the evaluation license.

So delete this two files, install again, finished.

greets
praekon

---

