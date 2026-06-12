---
title: "SSH Help"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by ilkertanli on 2006-01-06
After I installed ubuntu, I installed ssh by using sudo apt-get install ssh command. 

The problem is ssh service runs and I can log in to ubuntu in my network but 
I can't login outside. (ubuntu machine has a ip 192.168.0.106 and 68.36.147.__ when I type 192.168.0.106 in putty I can log in, but I can't when I type 68.36...)

Anybody had the same problem?

---

### Post by patrick295767 on 2006-01-06
[QUOTE=ilkertanli]After I installed ubuntu, I installed ssh by using sudo apt-get install ssh command. 

The problem is ssh service runs and I can log in to ubuntu in my network but 
I can't login outside. (ubuntu machine has a ip 192.168.0.106 and 68.36.147.__ when I type 192.168.0.106 in putty I can log in, but I can't when I type 68.36...)

Anybody had the same problem?[/QUOTE]
  
I guess everybdy ... You have a NAT or router or enabling VPN ... 
You may try the tunneling or port forwarding ...
  
Some people are very expert in some stuffs like this ...

---

### Post by ilkertanli on 2006-01-06
[QUOTE=patrick295767]I guess everybdy ... You have a NAT or router or enabling VPN ... 
You may try the tunneling or port forwarding ...
  
Some people are very expert in some stuffs like this ...[/QUOTE]

I set my ubuntu machine as DMZ in the router/firewall settings.

---

### Post by Chipmunk on 2006-01-06
I have heard (second hand unfortunately) of this being caused by the router itself having an SSH server of sorts running, have you tried (as I have successfully) forwarding external port say 2200 to internal 192.168.0.106 port 22 ?

From inside you just use putty to login to the default port (22), from outside you need to specify port 2200.

This would be called port forwarding or virtual server, depending on your router. It also gives you a measure of 'security by obscurity', which is generally regarded to be worthless, but it will prevent a large number of random login attempts. It's also possible your isp is blocking port 22.

You can test whether port 22 is open/closed from outside by using 'shields up' at [http://grc.com](http://grc.com) . This will show you if your isp is blocking ports/a range of ports.

---

### Post by Suger on 2006-01-06
Are you trying to ssh to your external IP from the WAN or from the LAN ? It won't work from the LAN, even if you're in a DMZ.

---

### Post by ilkertanli on 2006-01-06
[QUOTE=Suger]Are you trying to ssh to your external IP from the WAN or from the LAN ? It won't work from the LAN, even if you're in a DMZ.[/QUOTE]

I used to have Redhat installed on the same machine and never had such a problem.

By the way I have tried ssh both from Wan and Lan.

---

### Post by harisund on 2006-01-06
Could you solve the problem using the suggestions given by chipmunk earlier in this thread?

---

### Post by ThaRabbit on 2006-01-06
[QUOTE=ilkertanli]I used to have Redhat installed on the same machine and never had such a problem.

By the way I have tried ssh both from Wan and Lan.[/QUOTE]

So I take it that you are in fact trying to ssh to your external IP from your local network ?

Never a good thing to try as you are creating a loop, if this is the case then ask somebody outside your local network :)

---

### Post by ilkertanli on 2006-01-07
[QUOTE=harisund]Could you solve the problem using the suggestions given by chipmunk earlier in this thread?[/QUOTE]

I have tried everthing, its not working outside. Am I the only one having this problem?

---

### Post by Suger on 2006-01-07
Try

```
 ssh -vvv yourname@yourip
```
preferably from the WAN and post the output here

---

### Post by harisund on 2006-01-07
Ok here are some of the basic things I would check (if you have already, just ignore it.) 

1. There is something between the internet (external WAN) and your local network (LAN.) That is what converts an ip address of 68.36.147._ into local ip addresses of 192.168.0.* I think it is the router. 

2. When you type your external ip address, you reach your router. You reach it through a particular port. For example, if you type your ip address on a browser, you reach the router through port 80. If you type your ip address to SSH into it, you are reaching the router through port 22. 

3. The router should know which computer on the internal LAN should receieve the request depending on the port. Since you have your machine on the DMZ I believe that should be fine. 

4. It is likely that your ISP blocks certain ports. This is most likely. For this here a small fix. Make your SSH listen on port 8622 (just some number. 8622 works for me.) Since your machine is already on the DMZ you don't need to change any router/firewall settings. 

5. Now,
If you want to access the server from the local network (ie. from a machine that has a 192.168.0.* address) you can simply use
ssh user_name@192.168.0.106
If you want to access the server from outside the local network (or from the local network using your extenal ip, the 68.*.*.* ) you can do 
ssh -p 8622 user_name@68.*.*.*

Post back what happens. When you post, do be specific about the following: 
The port on which your SSH server is listening. 
The settings of your DMZ. 

And in case this could be of help to you, I too have a SSH server running behind a firewall setup very very similar to your setup. I don't have my machine on the DMZ, but rather forward external port 8622 to my server's 22, so if I do ssh -p 8622 user@68.* it works fine, and my SSH server configuration need not be changed.

---

### Post by darckhart on 2006-01-07
hi ilkertanli

i was having the same problem, even when i was in the dmz. therefore, i connected myself directly to the dsl modem and had my friend connect. now he is able to. i concluded that my router was not forwarding the port correctly.

---

### Post by Suger on 2006-01-08
I'm not sure it's a NAT problem (router port forwarding), that's why I've been asking you two guys the output of the ssh -vvv. I have a similar problem here, but  the failure is not with port forwarding, it's during the exchanges of identification between the client and the server. I'm not yet sure if the problem is with ssh, Ubuntu's ssh or sshd (I have been able to test the external ssh only with ubuntu boxes right now, but my sshd is running on an OpenBSD box).

If you'd post your ssh -vvv, I or someone else might be able to tell you where the problem is :D

---

### Post by ilkertanli on 2006-01-08
[QUOTE=Suger]Try

```
 ssh -vvv yourname@yourip
```
preferably from the WAN and post the output here[/QUOTE]
root@tekirdag:~# ssh -vvv ilker@68.36.247.66
OpenSSH_4.1p1 Debian-7ubuntu4, OpenSSL 0.9.7g 11 Apr 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 68.36.247.66 [68.36.247.66] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.1p1 Debia                                                                              n-7ubuntu4
debug1: match: OpenSSH_4.1p1 Debian-7ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-gro                                                                              up14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,                                                                              aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c                                                                              tr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,                                                                              aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c                                                                              tr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open                                                                              ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open                                                                              ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-gro                                                                              up14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,                                                                              aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c                                                                              tr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,                                                                              aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-c                                                                              tr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open                                                                              ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open                                                                              ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
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
debug2: dh_gen_key: priv key bits set: 149/256
debug2: bits set: 520/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /root/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /root/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 0 for host 68.36.247.66
debug3: check_host_in_hostfile: filename /root/.ssh/known_hosts2
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts2
debug3: check_host_in_hostfile: filename /root/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 2 for host 68.36.247.66
The authenticity of host '68.36.247.66 (68.36.247.66)' can't be established.
RSA key fingerprint is 78:4e:af:23:a8:f9:c0:29:bb:65:cf:33:6a:85:c0:11.
Are you sure you want to continue connecting (yes/no)?

here is the output.

---

### Post by Suger on 2006-01-08
Well, you have to answer yes at the last question for the connexion to go on. If you don't answer, it just times out. Once you've done that, I'm quite sure it will go on OK

A few things are established :

You get through the router, and the authentication procedure goes on smoothly.

P.S. : you should remove your username and IP from your post.

---

