---
title: "[SOLVED] Change SSHD_CONFIG back to default?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by ninja nicco on 2008-03-22
Hi. I am an absolute beginner at Linux but very curious about it so the last few weeks I have tried to learn as much as I can about it.

So what happened was that I was trying to setup a ssh tunnel to secure my connection but then I stumbeled across some guide telling me to change the sshd_config file to ensure security even further.

Here is my sshd_config dump:
```

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

 Later on I learned that you should always backup this file before you begin editing it. I'm not sure it is a problem but I would like to know if it is a way to change this file back to its defaults.

---

### Post by (((X))) on 2008-03-22
Hi,

PermitRootLogin is been set to yes, who told you to do that?
change it to no, you don't even have root on your system(by default).

---

### Post by ninja nicco on 2008-03-22
I think it was set like that to begin with. But perhaps I edited it without thinking about it. I was pretty tired when I messed around with the file, but that is the problem, I don't know exactly what I reconfigured so I don't know what to change back.

---

### Post by (((X))) on 2008-03-22
I understand your, happens to me all the time. And then I end up with nothing.

But still, I don't understand, what do you want to fix exactly?
You are able to login that box, do you

Here is tutorial I found, it explains a lot of these options, decide yourself which you want to allow.
[http://www.faqs.org/docs/securing/chap15sec122.html](http://www.faqs.org/docs/securing/chap15sec122.html)

---

### Post by (((X))) on 2008-03-22
by the way, 
I suppose it should be possible to reconfigure it by
sudo dpkg-reconfigure ssh
Although I'm not very sure, you could also try to purge ssh-server 
sudo apt-get --purge remove ssh

---

### Post by ninja nicco on 2008-03-22
Thanks for all the info :)  When it comes to the real problem it is that I can't seam to get my ssh tunnel working properly. After connecting to the ssh-server on localhost and forwarding data on a specific port like explained here:

[https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29#head-edc382321673e192fe467cb5d73f2b5e723ae806]("https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29#head-edc382321673e192fe467cb5d73f2b5e723ae806")

I am supposed to get a different IP-adress right? Well, when I check at [www.whatismyip.com](www.whatismyip.com) or [www.ip-adress.com](www.ip-adress.com) it is the same, thus I assumed that it was something wrong with the server-configuration because I had messed with it earlier.

EDIT: I feel very stupid not to have searched the forums throughly before posting but after a long night I found this little thread witch solved my problem:
[SSHD_CONFIG](http://ubuntuforums.org/showthread.php?t=511940&highlight=sshd_config)
so how do you mark your thread as solved??

---

### Post by (((X))) on 2008-03-23
Hi,
It doesn't matter, just post your questions/answers here, so I can learn too:)

To mark this thread as solved.
Left click on thread tools>mark as solved.

---

