---
title: "My battle with FreeNX, Please help"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by OneLinux on 2007-07-20
OK, I have read just about everything on these forums and online, and I'm getting nowhere. I can SSH to my machine fine, and I can VNC as well... but I would like to try out FreeNX to see if the speed advantage is noticeable. I have tried both FreeNX and Nomachines NX and gotten nowhere. I have removed both completely and just re-installed Freenx.

When I attempt to connect via my machine at work with Nomachine's NX client, it connects and then gives the error:

"Server not installed or NX access disabled"

Wen I click the Details button here is the output:

NX> 203 NXSSH running with pid: 2452
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: <My IP Address Here> on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
sh: /usr/bin/X11/xauth: Permission denied
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 Killed by signal 15.

It appears to me that it is a permission issue of some sort, but nothing I've tried has helped.

I'm running Freenx_0.6.0-0~seveas2_i386.deb
And Nomachine windows client Release:  	3.0.0-68

Any and all help is much appreciated! Thanks.

---

### Post by Trebaruna on 2007-07-20
Did you check the permissions on the file/folder specified?

---

### Post by Synflux on 2007-07-20
Hi,

Can you please post the output of:

cat /etc/ssh/ssh_config | grep authorized

cat /etc/ssh/sshd_config | grep authorized

cat /etc/ssh/sshd_config | grep AllowedUsers

There was a really good howto I found with step by step instructions that I followed and it worked first time, I can't find it anywhere though!:(

---

### Post by rdoolen on 2007-07-20
In the client configuration there is an option to enable/disable SSL. Try toggling that and re-atempt to connect.

I think it should be unchecked, but try it both ways.

---

### Post by Synflux on 2007-07-20
Under configure->Advanced I have 'enable ssl encryption of all traffic' ticked, otherwise I have to have loads of ports open (4000+ from memory), with it ticked I only have to have port 22 (or whatever your sshd listens on) open.

I'm wondering if you've defined the 'allowed users' setting but haven't added the 'nx' user to the list.

---

### Post by OneLinux on 2007-07-20
I have tried toggling the SSL option in the client, and it is set to use SSL on port 22 which works fine. It fails not matter what though with the same error that I listed above.

As for the output from those commands:


me@mymachine:~$ cat /etc/ssh/ssh_config | grep authorized
me@mymachine:~$ cat /etc/ssh/sshd_config | grep authorized
#AuthorizedKeysFile     %h/.ssh/authorized_keys
me@mymachine:~$ cat /etc/ssh/sshd_config | grep AllowedUsers

So, as you can see the only response was from the second command. It has to be a permission error, but I don't know what to change and to what permission.

---

### Post by Synflux on 2007-07-20
Hmmm,

My sshd_config says:

AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

So I wonder if it's worth making a backup and modifying it to test?

If so:

Make backup:
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak

Modify file:
sudo nano /etc/ssh/sshd_config

scroll down to your current authorizedkeys line and put a # in front to comment it out and then copy my line from above in. Ctrl+X to exit, Y to save and then enter to confirm the file name

Restart SSH:

sudo /etc/init.d/ssh restart


And then try connecting again, if that doesn't work then I'm not sure i'm afraid :confused:

---

