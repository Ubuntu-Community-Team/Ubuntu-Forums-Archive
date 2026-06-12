---
title: "NX again"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by svehex on 2006-11-10
I have a PC running kubuntu dapper drake 6.06.1 standard install. I've added apache2, mysql5, php5 and the nx-packages for debian from [www.nomachine.com](www.nomachine.com).

I've tried just about everything of advice found on the web, but I still get this when I run a usercheck:

linda@dolly:/usr/NX/etc$ sudo /usr/NX/bin/nxserver --usercheck linda
NX> 900 Verifying public key authentication for NX user: linda.
NX> 900 Adding public key for user: linda to the authorized keys file.
NX> 900 Verifying public key authentication for NX user: linda.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: linda
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.

Do you have any solutions? Here's what I've done:
installed nxclient
installed nxnode
installed nxserver

sudo joe /etc/ssh/sshd_config
Add the following line & save the file: AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

restarted sshd

sudo /usr/NX/bin/nxserver --status
This should return:
	NX> 900 Connecting to server ..
	NX> 110 NX Server is running.
	NX> 999 Bye.
But it returns:
	NX> 900 Connecting to server ..
	NX> 204 Authentication to NX server failed.
	NX> 110 NX Server is stopped.
	NX> 999 Bye.

sudo /usr/NX/bin/nxserver --useradd linda
sudo /usr/NX/bin/nxserver --userenable linda

Add entry in the 'hosts' file for localhost, pointing to the LAN IP address

Modify the server.cfg and node.cfg and enable the ssh_auth_server and the user_db=0 / user_passwd_db=0 in server.cfg

Modify /usr/NX/etc/node.cfg add this line:
AGENT_EXTRA_OPTIONS_X="-fp /usr/share/X11/fonts/misc:/usr/share/X11/fonts/cyrillic:/usr/share/X11/fonts/Type1:/usr/share/X11/fonts/CID:/usr/share/X11/fonts/100dpi:/usr/share/X11/fonts/75dpi:/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType:/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

Please help me! I need to have a gui remote possibility to use from work. Remote Desktop Sharing and VNC doesn't work for me. As an example: I press l once and get 20 l's

---

