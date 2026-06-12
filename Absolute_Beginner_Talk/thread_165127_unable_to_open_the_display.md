---
title: "unable to open the display"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by tkghosh on 2006-04-24
Hi,
 
Recently, I have installed Ubuntu 5.10 on a Toshiba laptop along with xp Windows.
In Ubuntu linux, I have installed SSH server to login in other host mechine in the network.
I am able to login in the host mechine, I can do lot of things in the host mechine 
through SSH. For example, I can edit & compile .tex file and generate a .ps file.
However, I can not view the ps file. when I am typing "gv filename.ps", it simply
says "unable to open the display".
Could you please tell me how I can display the ps/pdf files in the host mechine
through SSH?

Thank you in advance.

---

### Post by nanotube on 2006-04-24
logging in through ssh only gives you commandline access to the machine, you cannot view any gui directly through your ssh connection. 

you have two (probably more) options: download the .ps file to your client machine, and view it locally, or use a remote desktop client like tightvnc to connect to your ubuntu machine, instead of ssh.

---

### Post by tkghosh on 2006-04-24
[QUOTE=nanotube]logging in through ssh only gives you commandline access to the machine, you cannot view any gui directly through your ssh connection. 

you have two (probably more) options: download the .ps file to your client machine, and view it locally, or use a remote desktop client like tightvnc to connect to your ubuntu machine, instead of ssh.[/QUOTE]


Previously, i was using Suse linux, instead of Ubuntu.  i was  able to view ps/pdf files in the host mechine from my local mechine through ssh.
i do not know why it is not happening in Ubuntu.

---

### Post by xenmax on 2006-04-24
Just a guess on my part, i could be wrong. My guess is thet $DISPLAY is wrong. Check your $DISPLAY variable on host machine. It has to be correctly set to ip addr of the local machine and the desktop id.

---

### Post by cgjones on 2006-04-24
Take a look at /etc/ssh/sshd_config on the host machine to see if X11Forwarding is set to yes.

---

### Post by tkghosh on 2006-04-25
[QUOTE=cgjones]Take a look at /etc/ssh/sshd_config on the host machine to see if X11Forwarding is set to yes.[/QUOTE]



I have checked it, X11Forwarding is set to yes.
I am copying it here, if you have any suggestion,
please tell me to solve that problem.

here is the output of /etc/ssh/sshd_config on the host machine:


#       $OpenBSD: sshd_config,v 1.65 2003/08/28 12:54:34 markus Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options change a
# default value.

#Port 22
#Protocol 2,1
#ListenAddress 0.0.0.0
#ListenAddress ::

# HostKey for protocol version 1
#HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 768

# Logging
#obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
#PermitRootLogin yes
PermitRootLogin yes
#StrictModes yes

#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile     .ssh/authorized_keys

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication no
#PermitEmptyPasswords no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes


# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCreds yes

# Set this to 'yes' to enable PAM authentication (via challenge-response)
# and session processing. Depending on your PAM configuration, this may
# bypass the setting of 'PasswordAuthentication'
UsePAM yes

#AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes#PrintMotd yes
#PrintLastLog yes
#KeepAlive yes
#UseLogin no
UsePrivilegeSeparation no
#PermitUserEnvironment no
#Compression yes
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10

# no default banner path
#Banner /some/path
#Banner /some/path

# override default of no subsystems
Subsystem       sftp    /usr/lib/ssh/sftp-server





# RhostsRSAAuthentication and HostbasedAuthentication

---

### Post by cgjones on 2006-04-25
Ok, hopefully this will help. If it doesn't, take a look at the man page for ssh.

> 
   X11 and TCP forwarding
     If the ForwardX11 variable is set to yes
     the -X and -x options described later) and the user is using X11 (the
     DISPLAY environment variable is set), the connection to the X11 display
     is automatically forwarded to the remote side in such a way that any X11
     programs started from the shell (or command) will go through the
     encrypted channel, and the connection to the real X server will be made
     from the local machine.  The user should not manually set DISPLAY.  For-
     warding of X11 connections can be configured on the command line or in
     configuration files.


-X enables X11 forwarding
-x disables X11 forwarding

---

### Post by tkghosh on 2006-04-26
[QUOTE=cgjones]Ok, hopefully this will help. If it doesn't, take a look at the man page for ssh.



-X enables X11 forwarding
-x disables X11 forwarding[/QUOTE]


i am not expert in linux. could you please tell me in detail
how to use the above mentioned commands to view properly

---

### Post by cgjones on 2006-04-27
If you want to enable X11 Forwarding, try this the next time you log in.
```

ssh -X *username*@*hostname*

```

And to see the documentation for pretty much any command, type the following:
```

man *command*

```

---

### Post by tkghosh on 2006-04-27
[QUOTE=cgjones]If you want to enable X11 Forwarding, try this the next time you log in.
```

ssh -X *username*@*hostname*

```

And to see the documentation for pretty much any command, type the following:
```

man *command*

```[/QUOTE]


it works very well. thanks a lot.

---

### Post by cgjones on 2006-04-27
Glad I could help.

---

