---
title: "ssh tunneling and firefox"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by ubum on 2008-03-11
My ssh login doesn't ask for my password.  I have setu pub/private key.
User on remote machine is: me
User on the comp I am trying to do ssh from: ja

I have following keys in /home/ja/.ssh:
ssh_tun
someotherkey

How does ssh client know which private key to use?

When I do the following, it just waits forever:
[ja@mybox ~]$ ssh -D 2345 -f -C -q -N [email]me@my.com[/email]


In my firestarter, inbound traffic policy:
Allow service: ssh_tun
port: 2345
for: my.com

In my firefox manual proxy settings as follows:
socks proxy: localhost port: 2345

On the brower I get this:
SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.1

Any help appreciated.  thank you.

---

### Post by ubum on 2008-03-11
> [ja@mybox ~]$ ssh -D 2345 -p 2345 -i ~/.ssh/ssh_tun  [email]me@my.com[/email]
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 2345
Could not request local forwarding.
Linux me-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Tue Mar 11 17:03:04 2008 from 1.2.3.4

me@me-desktop:~$ 


> [ja@mybox ~]$ ssh -L 2345:localhost:2345 -i ~/.ssh/ssh_tun  [email]me@my.com[/email]
ssh: connect to host my.com port 22: Connection timed out
[ja@mybox ~]$

Why is this connectiong port 22 when I tell it to connect ot 2345?
someone help please!

In my firestarter, inbound traffic policy:
> Allow service: ssh_tun
port: 2345
for: everyone

"everyone" in firestarer a problem?

---

### Post by wormser on 2008-03-11
> ssh -D 2345 -f -C -q -N [email]me@my.com[/email]

That command you are using does not have the switch to indicate the port.  You need to put -p infront of the port.  I am not understanding what other issues you are having.  If you are still having a problem after adding the -p switch please explain what they are.

```
ssh -D 9999 -p 2345 -f -C -q -N [email]me@my.com[/email]
```

The -D switch needs port 9999 behind it.  It is the socks port for forwarding the internet connection,  I do not think you need the -N switch or the -q switch.  -N is do not execute remote commands and -q is quite mode.  The -C switch for compression is a great idea.

Do you have the Firefox settings right?  Firefox> Edit> Preferences> Advanced tab> Network tab> Settings> Manual proxy configuration> SOCKS Host: localhost Port 9999 and No Proxy for: localhost, 127.0.0.1.

> How does ssh client know which private key to use?

I do not technically know how it works but somehow it assigns that key to the address.

---

### Post by bodhi.zazen on 2008-03-11
you need a few more flags :)

ssh -p 2345 -i /path_to_key -L ....

-p sets the port to connect to

-i tells it what key to use. This is likely unnecessary, but I like to specify if the user name is not the same on the clinet and server.

I use -L to bind the port (if you need to do that). You will need to -X to forward X :)

---

### Post by wormser on 2008-03-11
> **bodhi.zazen said:**
> you need a few more flags :)

ssh -p 2345 -i /path_to_key -L ....

-p sets the port to connect to

-i tells it what key to use. This is likely unnecessary, but I like to specify if the user name is not the same on the clinet and server.

I use -L to bind the port (if you need to do that). You will need to -X to forward X :)

It looks like he is trying to ssh tunnel his internet connection and not forward X.  So, the -L and the -X is not needed in this case.  I think the following command will work.

```
ssh -D 9999 -p 2345 -f -C -q -N me@my.com
```

Then change the port in Firefox from 2345 to 9999 .

---

### Post by ubum on 2008-03-11
Running openssh server: > OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007

Remote Machine's /var/log/auth.log:
> Mar 11 18:42:10 me-desktop sshd[7787]: reverse mapping checking getaddrinfo for dsl-4-6-2-2.my.com [4.6.2.2] failed - POSSIBLE BREAK-IN ATTEMPT!
Mar 11 18:42:10 me-desktop sshd[7787]: Accepted publickey for me from 4.6.2.2 port 60803 ssh2
Mar 11 18:42:10 me-desktop sshd[7789]: pam_unix(ssh:session): session opened for user me by (uid=0)


this just logs me into the remote machine shell:
> ssh -D 9999 -p 2345 -f -C -q -N -i ~/.ssh/ssh_tun [email]me@my.com[/email]

I have the following in my firefox:

> Firefox> Edit> Preferences> Advanced tab> Network tab> Settings> Manual proxy configuration> SOCKS Host: localhost Port 9999 and No Proxy for: localhost, 127.0.0.1

When I open the brower and type cnn.com, I just get blank white page.  No errors, nothing.

My remote machine is using tcp6 to listen on port 2345.  Maybe this the problem.  How can I disable IP_V6?

---

### Post by wormser on 2008-03-11
It is good that it is logging in.  That means the command is working but there must be something wrong with the forward or Firefox settings. Double check the Firefox settings.  Make sure SOCKS v5 is selected.  Are you able to surf the internet on the remote machine?  Is it an Ubuntu box?  Here is a [HowTo]("http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6+disable") to disable IPv6.  Keep us up to date.

Here is the command I use and a screenshot of the Firefox settings.

```
ssh -p 2222 -D 9999 -C me@ipaddress.com
```

---

### Post by kevdog on 2008-03-11
Ive actually seen the word localhost cause problems for some -- I would replace this with 127.0.0.1 to avoid a potential problem!

---

### Post by ubum on 2008-03-11
> **kevdog said:**
> Ive actually seen the word localhost cause problems for some -- I would replace this with 127.0.0.1 to avoid a potential problem!

I just taken out localhost and only had 127.0.0.1 and this works.  Thank you.  by the way I am posting this via tunnel ;).  

Is there a way to verify this by look at some sort of log, either on client or remote machine, so that I can be sure tunneling is actually taking place rather than plain http?.

I can't believe I spent whole day one this ;(.   Time to go to bed.

---

### Post by wormser on 2008-03-11
> **ubum said:**
> I just taken out localhost and only had 127.0.0.1 and this works.  Thank you.  by the way I am posting this via tunnel ;).  

Is there a way to verify this by look at some sort of log, either on client or remote machine, so that I can be sure tunneling is actually taking place rather than plain http?.

I can't believe I spent whole day one this ;(.   Time to go to bed.

In Firefox just go to [http://www.whatismyip.com/](http://www.whatismyip.com/) with it on and off.  You could also run Wire Shark on the remote machine to see if the packets are going through it.  U do not know if there is any type of log that shows it is working besides the /var/log/auth.log that shows you logged in.  Make sure you mark the thread solved.

---

### Post by ubum on 2008-03-12
In my firestarter, inbound traffic policy:
> 
Allow service: ssh_tun
port: 2345
for: everyone
"everyone" in firestarer policy means that my comp allows anyone to connect to port 2345, even the ones without ssh keys?

---

