---
title: "Server issues..."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Tixer on 2007-06-23
I currently run 2 ubuntu servers, in my home (yes, I'm crazy). The first one has been great, and works amazingly well. I'm a bit of a "lunix" n00b, so it was weird for me setting it up, but it's been amazingly stable for LAMP. Unfortunately, other programs have been dying.

On server 1, I run an IRC bot, using mIRC. I had to throw it up quickly, and I didn't want to start figuring out a new program, so I just used WINE. Bad mistake, it crashes horribly. Additionally, I want to remove my graphics card, since it's tall, and the server has to go in a thin area, so administering it over GUI isn't an option. So what replacements are there for XDCC / DCC servers, that are easy to set up and can be done entirely over SSH?

Second question, is that my FTP daemon keeps dying. I don't know why, and it doesn't say anything in the logs, but it keeps dying, since people keep telling me they can't connect. I use GProFTPd right now, but I'd like to change. Partially because it uses a GUI, and also because it keeps dying. What are my options? I need something with user accounts, and easily set limitations per account.

On the second server, the MythTV box I'm currently building, it's currently running in a closet (no TV to use yet).  I set it up on my monitor, and I had it working. However, when I unplugged it all, and moved it, I lost contact with VNC. SSH works, but I can't connect over VNC. How can I change Remote Desktop options using only SSH?
I don't want to pull apart my desk again.

---

### Post by DBStevens on 2007-06-23
LOL,

Tell me would I be considered as aiding and abetting if I helped you with that setup :-)

However as for your snipe at the stability of the LAMP stack I'll just say the last I looked I knew of a 5 server cluster that has been front facing and heavily used without a kick in the hind end since 12/04.

How about running pureFTP for ftp.   You can also forward x server to run a gui on those remote servers.

Hope your closet is cool.

Are you running into a max concurent user limit with your ftp setup?

---

### Post by Tixer on 2007-06-23
Nope. I have under 8 users, and, although theres alot of traffic, I can't see why it wouldn't work. I have several layers of redundancy, and everything works except for FTP. Going to the folder over HTTP and logging in with HTaccess works, but still, no FTP.

Yes, my closet is cool. I use a custom made cooler, which keeps the proc at <30 C at peak. It's rather ghetto, but it works. Heat Dispersion is done with Q-Tips.

---

### Post by DBStevens on 2007-06-23
Did you change any of the defaults after you installed proftpd?

How is it running standalone or inetd?

---

### Post by Tixer on 2007-06-23
No clue what either of them are, or which one is used.

---

### Post by DBStevens on 2007-06-23
Could you post the contents of /etc/proftpd/proftpd.conf ?

---

### Post by Tixer on 2007-06-23
I'd like to, but it contains account data, as well as other stuff.

Is there something in particular you're looking for?

---

### Post by DBStevens on 2007-06-23
ServerName			"Debian"
ServerType			standalone
DeferWelcome			off

MaxInstances			30

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

---

### Post by Tixer on 2007-06-23
ServerType standalone
DefaultServer on
Umask 022
ServerName "XXXXXX.dynalias.net"
ServerIdent on "My FTPD"
ServerAdmin [email]edited@omg.com[/email]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 50000 60000

<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>

Also, what are passive ports? Do they need to be forwarded? I only have 21 open right now...

---

### Post by DBStevens on 2007-06-23
What kind of firewall are you running?

I'll have to look some stuff up, however I suspect the answer will be no if your firewall is SPI but I'll to check up on how the passive ports get used if they are controlled by the server then the answer is no for a SPI firewall. 

I loaded proftp on my system back after you told me which server you were using, I haven't punched a hole in my firewall to try a download from the outside yet.  Maybe tomorrow.  I'm watching the idiot box and answering questions that require no real thought or trying things out..

---

### Post by Tixer on 2007-06-24
bump. Not using a firewall, just a router

---

### Post by DBStevens on 2007-06-24
If there is no firewall then you have no blocks to those ports, they will be controlled by the ftp server you need do nothing.   If you were running a non SPI firewall then that port range would have to be opened.   You are saying that there is no firewall (seems that is a bit strange since most routers I've seen on home systems have one available).

---

### Post by Tixer on 2007-06-24
Firewall != Router.

I have a router, just no firewall. I still need to forward ports.

Any ideas to the other problems?

---

### Post by DBStevens on 2007-06-24
Yes I understand that Firewall != Router and I hope you understand that most Routers for home use normally also provide a firewall.

So the answer depends on what your box actually has and what is turned on or not.  So I can't answer your question, to answer that question from outside your system ftp using pasv mode.

You didn't provide your version of this:

 <IfModule mod_ctrls.c>
ControlsEngine on
ControlsMaxClients 2
ControlsLog /var/log/proftpd/controls.log
ControlsInterval 5
ControlsSocket /var/run/proftpd/proftpd.sock
</IfModule>

MaxInstances 30

The default proftpd setup allows only two clients to be logged on at a time and for each client to have 30 transfers in flight at a time.

---

