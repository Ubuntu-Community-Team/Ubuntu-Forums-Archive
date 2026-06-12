---
title: "NXServer NX Server - ssh works but NX has authentication falure"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-20
Re:  NXServer NX Server - ssh works but NX has authentication falure

I have ssh working just fine but NXServer just will not work -- see below:

carl@klaatu:/$ sudo /usr/NX/bin/nxserver --userlist
NX> 149 Listing NX users:

Username
---------------
cwmoser

NX> 999 Bye.
carl@klaatu:/$ sudo /usr/NX/bin/nxserver --start
NX> 500 Service already running.
NX> 999 Bye.
carl@klaatu:/$ 
carl@klaatu:/$ 
carl@klaatu:/$ sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ..
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.
carl@klaatu:/$ 



Also, when I run the NX Client, I get "Server not Installed or NX access disabled".

I had this working at one time and got it all bugged up when I changed some passwords.  I've tried uninstalling and reinstalling - even changing my passwords back.

I don't see any messages in /var/log/syslog or in /var/log/messages.

I did try to run nxssh and got this:

carl@klaatu:/usr/NX/bin$ /usr/NX/bin/nxssh 
/usr/NX/bin/nxssh: error while loading shared libraries: libXcomp.so.2: cannot open shared object file: No such file or directory


Do you think that there is an issue with libXcomp.so? 
Could it be an esoteric setting in one of the config files having to do with authentication?

Any insights appreciated.

Carl

---

### Post by cwmoser on 2007-05-20
[COLOR="Blue"]**I also tried this ...**[/COLOR]

root@klaatu:/usr/NX/bin# ./nxserver --usercheck cwmoser
NX> 900 Verifying public key authentication for NX user: cwmoser.
NX> 900 Adding public key for user: cwmoser to the authorized keys file.
NX> 716 Public key is already present in: /home/cwmoser/.ssh/authorized_keys2.
NX> 900 Verifying public key authentication for NX user: cwmoser.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: cwmoser
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.
root@klaatu:/usr/NX/bin# 

[COLOR="Blue"][B]... which indicates that there is a public key problem for user cwmoser.  If so, how does one establish a public key?

Thanks

Carl[/B][/COLOR]

---

### Post by cwmoser on 2007-05-22
UPDATE....

Thought I would share what I did to solve my problem with NXSERVER.  Even after following the procedure that jkbrown offered, I still could not get NXSERVER (the one that is free for 2 user remote access) to  work.

When I issued nxserver --status, I got an error.  I had ssh working just fine.

The SOLUTION was that my config file for ssh (/etc/ssh/sshd_config) was not configured properly to work with nxserver.  Even though, ssh worked, nxserver would not.

My /etc/ssh/sshd_config is below.

Once I got my sshd_config file straightened out, the jkbrown installation instructions worked perfectly.

Carl


-----------------------------------------------------
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
AllowUsers nx cwmoser carl sharon
StrictModes no

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      /usr/NX/home/nx/.ssh/authorized_keys2
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication yes

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes
PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

### Post by chenel on 2008-04-29
Thanks for posting.  Your notes helped me figure out why (after reinstalling Hardy on a machine that had a botched upgrade) I kept getting that same error time after time.  Turns out that my sshd_config was telling the system to use ~/.ssh/authorized_keys instead of ~/.ssh/authorized_keys**2**, which is where the NX private key needed for initial authentication is located.

Props.

---

