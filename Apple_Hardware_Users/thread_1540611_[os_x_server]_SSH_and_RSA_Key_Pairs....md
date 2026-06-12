---
title: "[os x server] SSH and RSA Key Pairs..."
date: 2010-07-28
forum: Apple Hardware Users
---

### Post by FiVAL on 2010-07-28
Hi Hi All!

Between Ubuntu computers it's so simple...
But between my Ubuntu Client and
three OS X Servers I can't get id done!

I did:

[LIST=1]
[*]Generate on my client (Ubuntu 10.04) 2 keys (a private and a public).
[*]On the X Server I added ~/.ssh/authorized_keys (admin account).
[*]chmod 700 ~/.ssh/ AND chmod 600 ~/.ssh/authorized_keys
[*]Changed the settings of the agent of the server (/etc/sshd_config):
RSAAuthentication yes 
PubkeyAuthentication yes
PasswordAuthentication no
UsePAM no
[/LIST]

Result: Permission denied (publickey,keyboard-interactive)

Anyone an idea what I did wrong??


---current sshd_config---
```

Port 22
Protocol 2
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

HostKey for protocol version 1
#HostKey /etc/ssh_host_key

HostKeys for protocol version 2
#HostKey /etc/ssh_host_rsa_key
#HostKey /etc/ssh_host_dsa_key

Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 3600
#ServerKeyBits 768

Logging
obsoletes QuietMode and FascistLogging
SyslogFacility AUTHPRIV
#LogLevel INFO

Authentication:

#LoginGraceTime 120
#PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile .ssh/authorized_keys

For this to work you will also need host keys in /etc/ssh_known_hosts
#RhostsRSAAuthentication no
similar for protocol version 2
#HostbasedAuthentication no
Change to yes if you don't trust ~/.ssh/known_hosts for
#IgnoreUserKnownHosts no
Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

To disable tunneled clear text passwords, change to no here! Also,
remember to set the UsePAM setting to 'no'.
PasswordAuthentication no
PermitEmptyPasswords no

SACL options
#SACLSupport yes

Change to no to disable s/key passwords
#ChallengeResponseAuthentication no

Kerberos options
KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes
#GSSAPIStrictAcceptorCheck yes
#GSSAPIKeyExchange no
UsePAM no

#AllowTcpForwarding yes
#GatewayPorts no

X11Forwarding yes
X11DisplayOffset 10

#X11UseLocalhost yes

PrintMotd no
PrintLastLog yes
TCPKeepAlive yes

#UseLogin no
#UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10
#PermitTunnel no
no default banner path
#Banner /some/path

override default of no subsystems
Subsystem sftp /usr/libexec/sftp-server

Example of overriding settings on a per-user basis
#Match User anoncvs
X11Forwarding no
AllowTcpForwarding no
ForceCommand cvs server

```

---output ssh user@system -v ---
```

OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 10.101.1.11 [10.101.1.11] port 22.
debug1: Connection established.
debug1: identity file /home/me/.ssh/identity type -1
debug1: identity file /home/me/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/me/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.2
debug1: match: OpenSSH_5.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '10.101.1.11' is known and matches the RSA host key.
debug1: Found key in /home/me/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Offering public key: /home/me/.ssh/id_rsa
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Trying private key: /home/me/.ssh/identity
debug1: Trying private key: /home/me/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: No more authentication methods to try.
Permission denied (publickey,keyboard-interactive).


```

---

### Post by FiVAL on 2010-07-29
Believe it or not...

...this problem was a terrible mistake I made when I copy the public key!

SSH Ubuntu <-> OS X now works perfect!

---

### Post by tc7 on 2011-02-17
One gotchya that had me going for a while regarding Ubuntu --> OSX 10.6 ssh connections was:

ssh my-mac
Connection closed by 160.xxx.yyy.41

or in more detail:
ssh -v my-mac
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /home/<username>/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to my-mac [160.xxx.yyy.41] port 22.
debug1: Connection established.
debug1: identity file /home/<username>/.ssh/id_rsa type -1
debug1: identity file /home/<username>/.ssh/id_rsa-cert type -1
debug1: identity file /home/<username>/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /home/<username>/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.2
debug1: match: OpenSSH_5.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'my-mac' is known and matches the RSA host key.
debug1: Found key in /home/<username>/.ssh/known_hosts:150
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Offering public key: /home/<username>/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 433
Connection closed by 160.xxx.yyy.41

and in the system log (/var/log/system.log on the Mac):
sandboxd[437]: sshd(436) deny mach-per-user-lookup


This had been bugging me for some time. The solution is very straightforward.

Ensure appropriate access rights (for the user) are defined in:
System Preferences / Sharing / Remote Login
[http://macosx.com/forums/mac-os-x-system-mac-software/316307-sshd-refuses-incoming-logins.html#post1509942](http://macosx.com/forums/mac-os-x-system-mac-software/316307-sshd-refuses-incoming-logins.html#post1509942)

Other common problems with SSH include opening port 22 (firewall) and ensuring correct directory permissions on user's home directory (no write permission for group / other), and the "~/.ssh" directory and "authorized_hosts" file (both rw for user only and x for dir of course).

tc

---

