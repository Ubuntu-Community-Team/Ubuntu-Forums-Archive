---
title: "ssh keys from OS X.04 to ubuntu server"
date: 2011-05-13
forum: Apple Hardware Users
---

### Post by wlraider70 on 2011-05-13
I have a 10.04ubuntu server and I would like to ssh into it from my regular mack running 10.4.

I've done the keygen and added it to known hosts but it wont work.
I know I did it right because I have a pure Ubuntu box 11.04 that I just did it with and it works perfectly. I'm not sure where to begin.

--edit  

some verbose info.



```

RJMac:~/.ssh robbiejo$ ssh -v server@hyrule
OpenSSH_5.1p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to hyrule [10.10.10.2] port 22.
debug1: Connection established.
debug1: identity file /Users/robbiejo/.ssh/identity type -1
debug1: identity file /Users/robbiejo/.ssh/id_rsa type 1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu6
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu6 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'hyrule' is known and matches the RSA host key.
debug1: Found key in /Users/robbiejo/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/robbiejo/.ssh/identity
debug1: Offering public key: /Users/robbiejo/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey,password).

```

---

