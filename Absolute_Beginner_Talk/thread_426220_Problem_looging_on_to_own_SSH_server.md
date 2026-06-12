---
title: "Problem looging on to own SSH server"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2007-04-28
I have installed the openssh-server and start it via /etc/init.d/ssh start

Now, I am trying to log on to it remotely with Putty. So I use SSH on port 22 to logon. I have a dyndns account and port forwarding for pt 22.

When I try to logon from a remote machine, then I get this message:

ssh: connect to host myhost.domain.xxx port 22: Connection refused

I have Firestarter Firewall running but I have allowed Service on port 22 to everyone.

Can someone please let me know how I can find out:

 - whether the server is actually running (I have checked ps -All and ssh process is running - is that the right one?)

 - how I can check that it works


Thanks a lot in advance!

Anders

---

### Post by 10drill on 2007-04-28
> **ahlandberg said:**
> 
Can someone please let me know how I can find out:

 - whether the server is actually running (I have checked ps -All and ssh process is running - is that the right one?)


From your local machine:

sudo apt-get install nmap
sudo nmap -sS -p 22 localhost

If you see something like: 22/tcp open  ssh then you know it's listening on port 22...

---

### Post by gunthr on 2007-04-28
The process should be sshd. Can you login locally using 

```
ssh username@127.0.0.1
```

---

### Post by ahlandberg on 2007-04-28
I installed nmap and this is what I got:

ahlandberg@ubuntu610:~$ sudo nmap -sS -p 22 localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-04-29 12:15 EST
Interesting ports on localhost (127.0.0.1):
PORT   STATE SERVICE
22/tcp open  ssh

Nmap finished: 1 IP address (1 host up) scanned in 0.032 seconds


So it looks like it's listening on port 22.


And yes, I can logon through ssh username@127.0.0.1

The weird thing is that from the other computers (WinXP) on my LAN, I can logon with Putty/SSH onto my Linux machine. However, when I ssh into my University ssh account and FROM THERE attempt to logon, it sayd: Connection refused!

Therefore I suspect one of the two problems:

(1) My Uni account prohibits/blocks ssh connections to other/not known servers
(2) My ssh server is only accessible from within the LAN (But: I have port 22 forwarded!!!)

---

### Post by shahin on 2007-04-28
The problem could be your router.  I am using an actiontec supplied by Verizon, and I found a site with procedures for this.  Here is the link:
[http://portforward.com/english/routers/port_forwarding/Actiontec/MI-424-WR/MI-424-WRindex.htm](http://portforward.com/english/routers/port_forwarding/Actiontec/MI-424-WR/MI-424-WRindex.htm)

Let me know if you have more success than I have, I am still working on it.  I do 
not really understand the last paragraph for the ssh procedures they have posted.  They say the pc should be configured for static ip, and I did that in Ubuntu, but shouldn't I take the ip out of the dhcp pool?  

Another question I have is why do you need to install the ssh server?  shouldn't you be able to ssh w/o the server?

---

### Post by ahlandberg on 2007-04-29
I figured out what the problem was.

Indeed, it was the University's server. It doesn't allow any external connections. Crap uni!

I asked a friend of mine to logon to my ssh server and he said it worked fine.

Yes, I think ssh server is automatically installed and accessible anyway, but I wasn't sure.

Can you actually logon to your machine with ssh -l username localhost ??? If yes, then that is an indication that it will work from a remote machine, too. (Given your router and firewall are setup correctly)

---

### Post by eternalsword on 2007-04-29
> **ahlandberg said:**
> I figured out what the problem was.

Indeed, it was the University's server. It doesn't allow any external connections. Crap uni!

I asked a friend of mine to logon to my ssh server and he said it worked fine.

Yes, I think ssh server is automatically installed and accessible anyway, but I wasn't sure.

Can you actually logon to your machine with ssh -l username localhost ??? If yes, then that is an indication that it will work from a remote machine, too. (Given your router and firewall are setup correctly)

try running sshd on a non standard port.  I would suggest port 443, that way it looks exactly like https traffic.  

first, stop the sshd daemon:
sudo /etc/init.d/sshd stop

then edit the config file:
gksu gedit /etc/ssh/sshd_config

and switch the port from 22 to 443.
then restart the sshd daemon:
sudo /etc/init.d/sshd start

then when using putty, switch the port number in the gui, or if using ssh in the command line, "ssh -p 443 user@host"

---

### Post by shahin on 2007-04-29
I can not ssh to my local host from the machine.  Here is the output:
sansari@karoon:~$ ssh -l sansari localhost
ssh: connect to host localhost port 22: Connection refused
sansari@karoon:~$ ps -ef | grep ssh
sansari   4912  4877  0 03:36 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
sansari   5429  5242  0 03:50 pts/0    00:00:00 grep ssh
sansari@karoon:~$ ssh sansari@127.0.0.1
ssh: connect to host 127.0.0.1 port 22: Connection refused

I just looked for openssh server software, and I only see the openssh client. I believe I installed client ubuntu vs. server?

---

### Post by shahin on 2007-04-29
Ok I just checked on my other machine that runs ubuntu, and I was able to install ssh-server.  Once I did this, and opened the ports on my router just as advised in the posting, I was able establish and ssh session.  Life is good.  Thanks for your advice.  Now I have figure out what is going on with the other machine.

---

