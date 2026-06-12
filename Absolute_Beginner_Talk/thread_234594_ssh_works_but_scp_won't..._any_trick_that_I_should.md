---
title: "ssh works but scp won't... any trick that I should know?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by horito on 2006-08-11
Here is a question about ssh configuration. I have recently installer Dapper and averything works very well. However, something is really bothering me. I have a my ssh server and client running. I can, thus,  ssh to and from it. (even use svn+ssh:// !!)

Why is it that I can't do scp to transfer file? I'ld like too understand if this is a configuration issue or what? Do I really need to setup keys and all  that? 

Perhaps som wise and more experienced user could provide hints to solve this

thank you!

my sshd_config is below...

:~$ dpkg -l| grep  ssh
ii  openssh-client  4.2p1-7ubuntu3   Secure shell client, an rlogin/rsh/rcp repla
ii  openssh-server  4.2p1-7ubuntu3   Secure shell server, an rshd replacement
ii  rssh            2.3.0-1.1        Restricted shell allowing only scp, sftp, cv
ii  ssh             4.2p1-7ubuntu3   Secure shell client and server (transitional
ii  ssh-askpass-gnome 4.2p1-7ubuntu3  under X, asks user for a passphrase for ssh-

cat /etc/ssh/sshd_config
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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

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
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

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
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

### Post by ispmarin on 2006-08-24
I am having a almost similar problem: my scp connection starts, but after a few megs it just stalls. sshd and ssh configs very similar. What the heck?

Thank you!

---

### Post by tmcmack on 2007-10-21
I'm having the same issue with  a Feisty-Feisty connection. I'll try to provide some detail, but please let me know what other information I can provide.

Long story short, I can SSH from a Feisty laptop to a Feisty server, but scp, ssh -Y, and ssh -X cause the connection to crash. I'm hoping for a pointer to some troubleshooting info to figure out if the problem's in my router setup, the server, or the client. Or, what could cause a network connection to work fine for everything except scp and ssh -Y? Thanks in advance. I've been with Ubuntu and Linux since Feisty came out, so I'm not quite a first-timer but definitely not an expert.

I have a laptop (3 year old Toshiba, dual boot, feisty and XP) and a desktop to use as a server (~9 year old pentium 2, 192 MB RAM, single boot Feisty server edition). Both are connected wirelessly to my d-link router using WPA-PSK. I can SSH to the server from the laptop and everything works fine; I can issue commands, use the internet (apt-get and wget), and stay logged in all day with no problem. However, if try to copy a file to it with scp (I do this while not logged in over ssh), about 3% of the file transfers before the transfer stops and displays "stalled" instead of the transfer rate. At this point, I can no longer connect via ssh or scp; to connect again I must reset the network connection manually on the server with "sudo /etc/init.d/networking restart"

I've also installed xorg, fluxbox, and the media player XMMS to the server, hoping to use ssh -Y to see the player UI on the laptop but have the sound come out of the server, which is plugged into the stereo. I use "ssh -Y username:serveripaddress xmms", and the media player window appears on the laptop screen. I can add an MP3 to the playlist, press play, and hear the music out of the speakers. However, after 30 seconds, the media player freezes and does not respond to mouse clicks, and though the MP3 continues playing on the server, I lose the entire network connection on the client laptop. No web browsing, no more SSH, nothing. In a few minutes, the gnome network-manager reconnects to the router, and all is well again for another 30-60 seconds. I can play a long MP3 this way and sit there not touching anything as the connection goes down and up and back down again over and over. Same thing happened when I had fluxbuntu dapper on the server.

I just tried to update the server to Gutsy and nothing worked (spent my whole weekend trying to get wireless and cd rom working, but I've given up) so I wiped the server and put a clean install of Feisty server on it, with no X stuff. It is as out-of-the-box as possible. After I re-install Feisty server on the server (formatting the root partition so it's a totally clean install) all I have to do is set the /etc/network/interfaces file to the following to use the server's Hawking rt2500 wireless card. (no ndiswrapper needed.) Got this information on this page (before it was edited to say that this wasn't supposed to work in Feisty): [RalinkRT2500]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500") 

Server's /etc/network/interfaces:

```
server$ cat /etc/network/interfaces
auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "[router's essid]"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="[key]"
pre-up ifconfig ra0 up



auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```


The laptop's /etc/network/interfaces is managed by gnome network-manager, so it's just this: 

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

iwconfig on the server: 

```
server$ iwconfig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"[router essid]"  
          Mode:Managed  Frequency=2.447 GHz  Access Point: 00:0D:88:ED:51:DD   
          Bit Rate:54 Mb/s   Tx-Power:-3 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=89/100  Signal level=-47 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
iwconfig on the laptop is essentially the same. 

ifconfig on the server:

```
server$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0E:3B:06:0E:79  
          inet addr:[server's IP]  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:3bff:fe06:e79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53811 errors:1 dropped:1 overruns:0 carrier:0
          collisions:372 txqueuelen:1000 
          RX bytes:140638461 (134.1 MiB)  TX bytes:5942366 (5.6 MiB)
          Interrupt:10 Base address:0x8000 

```

ifconfig on the laptop:
```

$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:90:96:70:EC:8E  
          inet addr:[client's IP]  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fe70:ec8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54427 errors:1 dropped:0 overruns:0 frame:0
          TX packets:32967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49943245 (47.6 MiB)  TX bytes:4025051 (3.8 MiB)

eth0      Link encap:Ethernet  HWaddr 00:08:0D:6A:51:CB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6f00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1508 (1.4 KiB)  TX bytes:1508 (1.4 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-90-96-70-EC-8E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:406444 errors:27 dropped:0 overruns:0 frame:187135
          TX packets:39194 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:87153515 (83.1 MiB)  TX bytes:5843843 (5.5 MiB)
          Interrupt:11 
```



server's /etc/ssh/sshd_config:

```
server$ cat /etc/ssh/sshd_config 
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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

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


```

laptop's /etc/ssh/sshd_config:

```
$ cat /etc/ssh/sshd_config
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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
GSSAPIAuthentication no
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

#https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/111553
AddressFamily inet
```


I don't know enough about networking to know where the problem is or how to debug it. Any help? How can I find which machine is causing the problem? Sorry for the long, vague question.

---

### Post by HermanAB on 2007-10-21
If scp works, but drops out after a few megabytes, then the problem is NOT with SSH.  The problem is either due to the distant server, or a router somewhere in between.

Many older el'cheapo routers flush their NAT tables every ten minutes or so, thus breaking SSH.

---

### Post by ispmarin on 2007-10-22
Hello, 

I had a very similar problem, and found that the problem was a faulty ethernet board. Check with ssh -v or scp -v, and if you can change the board.

Hope it helps.

Ivan

---

### Post by tmcmack on 2007-10-27
The router manual doesn't say anything about refreshing the NAT tables. It may still be the router settings, but I'm not sure why it would let me stay logged in through SSH all day and quit after 10 seconds with scp.

Here's the debugging output from scp -vvv, first, for a small text file that succeeds. Most of  the early messages are for key authentication, but I'm not using keys, I just type my password each time.

```
$ scp -vvv small_file.txt username@192.ip.address.1:/home/username/Desktop/

Executing: program /usr/bin/ssh host 192.ip.address.1, user username, command scp -v -t /home/username/Desktop/
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config

debug1: Applying options for *

debug2: ssh_connect: needpriv 0

debug1: Connecting to 192.ip.address.1 [192.ip.address.1] port 22.

debug1: Connection established.

debug1: identity file /home/username/.ssh/identity type -1

debug3: Not a RSA1 key file /home/username/.ssh/id_rsa.

debug2: key_type_from_name: unknown key type '-----BEGIN'

debug3: key_read: missing keytype

debug2: key_type_from_name: unknown key type 'Proc-Type:'

debug3: key_read: missing keytype

debug2: key_type_from_name: unknown key type 'DEK-Info:'

debug3: key_read: missing keytype

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug2: key_type_from_name: unknown key type '-----END'

debug3: key_read: missing keytype

debug1: identity file /home/username/.ssh/id_rsa type 1

debug1: identity file /home/username/.ssh/id_dsa type -1

debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1

debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*

debug1: Enabling compatibility mode for protocol 2.0

debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1

debug2: fd 3 setting O_NONBLOCK

debug1: Miscellaneous failure
Improper format of Kerberos configuration file


debug1: Miscellaneous failure
Improper format of Kerberos configuration file


debug1: Miscellaneous failure
Improper format of Kerberos configuration file


debug1: Miscellaneous failure
Improper format of Kerberos configuration file


debug1: SSH2_MSG_KEXINIT sent

debug1: SSH2_MSG_KEXINIT received

debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1

debug2: kex_parse_kexinit: ssh-rsa,ssh-dss

debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96

debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96

debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib

debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib

debug2: kex_parse_kexinit: 

debug2: kex_parse_kexinit: 

debug2: kex_parse_kexinit: first_kex_follows 0 

debug2: kex_parse_kexinit: reserved 0 

debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1

debug2: kex_parse_kexinit: ssh-rsa,ssh-dss

debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96

debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96

debug2: kex_parse_kexinit: none,zlib@openssh.com

debug2: kex_parse_kexinit: none,zlib@openssh.com

debug2: kex_parse_kexinit: 

debug2: kex_parse_kexinit: 

debug2: kex_parse_kexinit: first_kex_follows 0 

debug2: kex_parse_kexinit: reserved 0 

debug2: mac_init: found hmac-md5

debug1: kex: server->client aes128-cbc hmac-md5 none

debug2: mac_init: found hmac-md5

debug1: kex: client->server aes128-cbc hmac-md5 none

debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent

debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP

debug2: dh_gen_key: priv key bits set: 133/256

debug2: bits set: 517/1024

debug1: SSH2_MSG_KEX_DH_GEX_INIT sent

debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY

debug3: check_host_in_hostfile: filename /home/username/.ssh/known_hosts

debug3: check_host_in_hostfile: match line 1

debug1: Host '192.ip.address.1' is known and matches the RSA host key.

debug1: Found key in /home/username/.ssh/known_hosts:1

debug2: bits set: 529/1024

debug1: ssh_rsa_verify: signature correct

debug2: kex_derive_keys

debug2: set_newkeys: mode 1

debug1: SSH2_MSG_NEWKEYS sent

debug1: expecting SSH2_MSG_NEWKEYS

debug2: set_newkeys: mode 0

debug1: SSH2_MSG_NEWKEYS received

debug1: SSH2_MSG_SERVICE_REQUEST sent

debug2: service_accept: ssh-userauth

debug1: SSH2_MSG_SERVICE_ACCEPT received

debug2: key: /home/username/.ssh/identity ((nil))

debug2: key: /home/username/.ssh/id_rsa (0x80054518)

debug2: key: /home/username/.ssh/id_dsa ((nil))

debug1: Authentications that can continue: publickey,password

debug3: start over, passed a different list publickey,password

debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password

debug3: authmethod_lookup publickey

debug3: remaining preferred: keyboard-interactive,password

debug3: authmethod_is_enabled publickey

debug1: Next authentication method: publickey

debug1: Trying private key: /home/username/.ssh/identity

debug3: no such identity: /home/username/.ssh/identity

debug1: Offering public key: /home/username/.ssh/id_rsa

debug3: send_pubkey_test

debug2: we sent a publickey packet, wait for reply

debug1: Authentications that can continue: publickey,password

debug1: Trying private key: /home/username/.ssh/id_dsa

debug3: no such identity: /home/username/.ssh/id_dsa

debug2: we did not send a packet, disable method

debug3: authmethod_lookup password

debug3: remaining preferred: ,password

debug3: authmethod_is_enabled password

debug1: Next authentication method: password

debug3: packet_send2: adding 48 (len 70 padlen 10 extra_pad 64)

debug2: we sent a password packet, wait for reply

debug1: Authentication succeeded (password).

debug2: fd 4 setting O_NONBLOCK

debug2: fd 5 setting O_NONBLOCK

debug2: fd 6 setting O_NONBLOCK

debug1: channel 0: new [client-session]

debug3: ssh_session2_open: channel_new: 0

debug2: channel 0: send open

debug1: Entering interactive session.

debug2: callback start

debug2: client_session2_setup: id 0

debug1: Sending environment.

debug3: Ignored env SSH_AGENT_PID

debug3: Ignored env SHELL

debug3: Ignored env DESKTOP_STARTUP_ID

debug3: Ignored env TERM

debug3: Ignored env GTK_RC_FILES

debug3: Ignored env WINDOWID

debug3: Ignored env USER

debug3: Ignored env LS_COLORS

debug3: Ignored env SSH_AUTH_SOCK

debug3: Ignored env GNOME_KEYRING_SOCKET

debug3: Ignored env SESSION_MANAGER

debug3: Ignored env USERNAME

debug3: Ignored env PATH

debug3: Ignored env DESKTOP_SESSION

debug3: Ignored env GDM_XSERVER_LOCATION

debug3: Ignored env PWD

debug1: Sending env LANG = en_US.UTF-8

debug2: channel 0: request env confirm 0

debug3: Ignored env GDMSESSION

debug3: Ignored env HISTCONTROL

debug3: Ignored env SHLVL

debug3: Ignored env HOME

debug3: Ignored env GNOME_DESKTOP_SESSION_ID

debug3: Ignored env LOGNAME

debug3: Ignored env DBUS_SESSION_BUS_ADDRESS

debug3: Ignored env LESSOPEN

debug3: Ignored env DISPLAY

debug3: Ignored env LESSCLOSE

debug3: Ignored env COLORTERM

debug3: Ignored env XAUTHORITY

debug3: Ignored env _

debug3: Ignored env OLDPWD

debug1: Sending command: scp -v -t /home/username/Desktop/

debug2: channel 0: request exec confirm 0

debug2: callback done

debug2: channel 0: open confirm rwindow 0 rmax 32768

debug2: channel 0: rcvd adjust 131072

Sending file modes: C0644 12028 eh_open_ended.txt
debug2: channel 0: rcvd ext data 36

Sink: C0644 12028 eh_open_ended.txt
debug2: channel 0: written 36 to efd 6

debug2: channel 0: read<=0 rfd 4 len 0

debug2: channel 0: read failed

debug2: channel 0: close_read

debug2: channel 0: input open -> drain

debug2: channel 0: ibuf empty

debug2: channel 0: send eof

debug2: channel 0: input drain -> closed

debug1: client_input_channel_req: channel 0 rtype exit-status reply 0

debug2: channel 0: rcvd eof

debug2: channel 0: output open -> drain

debug2: channel 0: obuf empty

debug2: channel 0: close_write

debug2: channel 0: output drain -> closed

debug2: channel 0: rcvd close

debug3: channel 0: will not send data after close

debug2: channel 0: almost dead

debug2: channel 0: gc: notify user

debug2: channel 0: gc: user detached

debug2: channel 0: send close

debug2: channel 0: is dead

debug2: channel 0: garbage collecting

debug1: channel 0: free: client-session, nchannels 1

debug3: channel 0: status: The following connections are open:

  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)



debug3: channel 0: close_fds r -1 w -1 e 6 c -1

debug1: fd 0 clearing O_NONBLOCK

debug1: fd 1 clearing O_NONBLOCK

debug1: fd 2 clearing O_NONBLOCK

debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.2 seconds

debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0

debug1: Exit status 0


```

And the output from a transfer of a large file that hangs and prevents any further connection to the server:

```
$ scp -vvv ubuntu-7.10-desktop-i386.iso username@192.ip.address.101:/home/username/Desktop/

Executing: program /usr/bin/ssh host 192.ip.address.1, user username, command scp -v -t /home/username/Desktop/
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config

debug1: Applying options for *

debug2: ssh_connect: needpriv 0

debug1: Connecting to 192.ip.address.1 [192.ip.address.1] port 22.

debug1: Connection established.

debug1: identity file /home/username/.ssh/identity type -1

debug3: Not a RSA1 key file /home/username/.ssh/id_rsa.

debug2: key_type_from_name: unknown key type '-----BEGIN'

debug3: key_read: missing keytype

debug2: key_type_from_name: unknown key type 'Proc-Type:'

debug3: key_read: missing keytype

debug2: key_type_from_name: unknown key type 'DEK-Info:'

debug3: key_read: missing keytype

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug3: key_read: missing whitespace

debug2: key_type_from_name: unknown key type '-----END'

debug3: key_read: missing keytype

debug1: identity file /home/username/.ssh/id_rsa type 1

debug1: identity file /home/username/.ssh/id_dsa type -1

debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1

debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*

debug1: Enabling compatibility mode for protocol 2.0

debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1

debug2: fd 3 setting O_NONBLOCK

debug1: Miscellaneous failure
Improper format of Kerberos configuration file


debug1: Miscellaneous failure
Improper format of Kerberos configuration file


debug1: Miscellaneous failure
Improper format of Kerberos configuration file


debug1: Miscellaneous failure
Improper format of Kerberos configuration file


debug1: SSH2_MSG_KEXINIT sent

debug1: SSH2_MSG_KEXINIT received

debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1

debug2: kex_parse_kexinit: ssh-rsa,ssh-dss

debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96

debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96

debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib

debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib

debug2: kex_parse_kexinit: 

debug2: kex_parse_kexinit: 

debug2: kex_parse_kexinit: first_kex_follows 0 

debug2: kex_parse_kexinit: reserved 0 

debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1

debug2: kex_parse_kexinit: ssh-rsa,ssh-dss

debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr

debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96

debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96

debug2: kex_parse_kexinit: none,zlib@openssh.com

debug2: kex_parse_kexinit: none,zlib@openssh.com

debug2: kex_parse_kexinit: 

debug2: kex_parse_kexinit: 

debug2: kex_parse_kexinit: first_kex_follows 0 

debug2: kex_parse_kexinit: reserved 0 

debug2: mac_init: found hmac-md5

debug1: kex: server->client aes128-cbc hmac-md5 none

debug2: mac_init: found hmac-md5

debug1: kex: client->server aes128-cbc hmac-md5 none

debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent

debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP

debug2: dh_gen_key: priv key bits set: 124/256

debug2: bits set: 507/1024

debug1: SSH2_MSG_KEX_DH_GEX_INIT sent

debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY

debug3: check_host_in_hostfile: filename /home/username/.ssh/known_hosts

debug3: check_host_in_hostfile: match line 1

debug1: Host '192.ip.address.1' is known and matches the RSA host key.

debug1: Found key in /home/username/.ssh/known_hosts:1

debug2: bits set: 541/1024

debug1: ssh_rsa_verify: signature correct

debug2: kex_derive_keys

debug2: set_newkeys: mode 1

debug1: SSH2_MSG_NEWKEYS sent

debug1: expecting SSH2_MSG_NEWKEYS

debug2: set_newkeys: mode 0

debug1: SSH2_MSG_NEWKEYS received

debug1: SSH2_MSG_SERVICE_REQUEST sent

debug2: service_accept: ssh-userauth

debug1: SSH2_MSG_SERVICE_ACCEPT received

debug2: key: /home/username/.ssh/identity ((nil))

debug2: key: /home/username/.ssh/id_rsa (0x80054518)

debug2: key: /home/username/.ssh/id_dsa ((nil))

debug1: Authentications that can continue: publickey,password

debug3: start over, passed a different list publickey,password

debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password

debug3: authmethod_lookup publickey

debug3: remaining preferred: keyboard-interactive,password

debug3: authmethod_is_enabled publickey

debug1: Next authentication method: publickey

debug1: Trying private key: /home/username/.ssh/identity

debug3: no such identity: /home/username/.ssh/identity

debug1: Offering public key: /home/username/.ssh/id_rsa

debug3: send_pubkey_test

debug2: we sent a publickey packet, wait for reply

debug1: Authentications that can continue: publickey,password

debug1: Trying private key: /home/username/.ssh/id_dsa

debug3: no such identity: /home/username/.ssh/id_dsa

debug2: we did not send a packet, disable method

debug3: authmethod_lookup password

debug3: remaining preferred: ,password

debug3: authmethod_is_enabled password

debug1: Next authentication method: password

debug3: packet_send2: adding 48 (len 70 padlen 10 extra_pad 64)

debug2: we sent a password packet, wait for reply

debug1: Authentication succeeded (password).

debug2: fd 4 setting O_NONBLOCK

debug2: fd 5 setting O_NONBLOCK

debug2: fd 6 setting O_NONBLOCK

debug1: channel 0: new [client-session]

debug3: ssh_session2_open: channel_new: 0

debug2: channel 0: send open

debug1: Entering interactive session.

debug2: callback start

debug2: client_session2_setup: id 0

debug1: Sending environment.

debug3: Ignored env SSH_AGENT_PID

debug3: Ignored env SHELL

debug3: Ignored env DESKTOP_STARTUP_ID

debug3: Ignored env TERM

debug3: Ignored env GTK_RC_FILES

debug3: Ignored env WINDOWID

debug3: Ignored env USER

debug3: Ignored env LS_COLORS

debug3: Ignored env SSH_AUTH_SOCK

debug3: Ignored env GNOME_KEYRING_SOCKET

debug3: Ignored env SESSION_MANAGER

debug3: Ignored env USERNAME

debug3: Ignored env PATH

debug3: Ignored env DESKTOP_SESSION

debug3: Ignored env GDM_XSERVER_LOCATION

debug3: Ignored env PWD

debug1: Sending env LANG = en_US.UTF-8

debug2: channel 0: request env confirm 0

debug3: Ignored env GDMSESSION

debug3: Ignored env HISTCONTROL

debug3: Ignored env SHLVL

debug3: Ignored env HOME

debug3: Ignored env GNOME_DESKTOP_SESSION_ID

debug3: Ignored env LOGNAME

debug3: Ignored env DBUS_SESSION_BUS_ADDRESS

debug3: Ignored env LESSOPEN

debug3: Ignored env DISPLAY

debug3: Ignored env LESSCLOSE

debug3: Ignored env COLORTERM

debug3: Ignored env XAUTHORITY

debug3: Ignored env _

debug3: Ignored env OLDPWD

debug1: Sending command: scp -v -t /home/username/Desktop/

debug2: channel 0: request exec confirm 0

debug2: callback done

debug2: channel 0: open confirm rwindow 0 rmax 32768

debug2: channel 0: rcvd adjust 131072

Sending file modes: C0644 729608192 ubuntu-7.10-desktop-i386.iso
debug2: channel 0: rcvd ext data 51

Sink: C0644 729608192 ubuntu-7.10-desktop-i386.iso
debug2: channel 0: written 51 to efd 6

debug2: channel 0: rcvd adjust 65581

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

debug2: channel 0: rcvd adjust 81920

```

---

