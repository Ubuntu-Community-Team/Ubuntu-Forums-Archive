---
title: "network-manager-pptp / KVpnc"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by o0beaner on 2008-02-27
I am trying to connect to my company's PPTP VPN connection, and am having issues from every angle I take.

Using network-manager-pptp, I get a very vague "VPN Connection failed" error on every try.

I have followed various guides on connecting to Windows networks to no avail what so ever. As I was becoming increasingly frustrated, I read about another option: KVpnc.

I immediately download, install and configure the utility. 

Bam.

First try, I'm connected.

Now, much to my dismay, I see my new issue. I am disconnected every 24-30 seconds. Once again, my clues as to the problem are vague. Here is what syslog says about my connection attempts.

*note- any instance of a colon followed by the letter p was changed to a dash followed by the letter p, as the forum interpreted it as as me using smilies.

Feb 27 21:13:29 tydesk pppd[25311]: no device specified and stdin is not a tty
Feb 27 21:13:29 tydesk pppd[25315]: pppd 2.4.4 started by root, uid 0
Feb 27 21:13:29 tydesk pppd[25315]: Using interface ppp0
Feb 27 21:13:29 tydesk pppd[25315]: Connect: ppp0 <--> /dev/pts/1
Feb 27 21:13:29 tydesk pptp[25318]: anon log[main-pptp.c:267]: The synchronous pptp option is NOT activated 
Feb 27 21:13:29 tydesk pptp[25320]: anon log[ctrlp_rep-pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Feb 27 21:13:29 tydesk pptp[25320]: anon log[ctrlp_disp-pptp_ctrl.c:738]: Received Start Control Connection Reply
Feb 27 21:13:29 tydesk pptp[25320]: anon log[ctrlp_disp-pptp_ctrl.c:772]: Client connection established.
Feb 27 21:13:30 tydesk pppd[25315]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Feb 27 21:13:30 tydesk pptp[25320]: anon log[ctrlp_rep-pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Feb 27 21:13:30 tydesk pptp[25320]: anon log[ctrlp_disp-pptp_ctrl.c:857]: Received Outgoing Call Reply.
Feb 27 21:13:30 tydesk pptp[25320]: anon log[ctrlp_disp-pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 57065). 
Feb 27 21:13:30 tydesk pptp[25320]: anon log[ctrlp_disp-pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Feb 27 21:13:30 tydesk pptp[25320]: anon log[ctrlp_disp-pptp_ctrl.c:952]:   send_accm is 00000000, recv_accm is FFFFFFFF
Feb 27 21:13:30 tydesk pptp[25320]: anon warn[ctrlp_disp-pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Feb 27 21:13:30 tydesk pppd[25315]: CHAP authentication succeeded
Feb 27 21:13:30 tydesk pppd[25315]: MPPE 128-bit stateless compression enabled
Feb 27 21:13:32 tydesk pppd[25315]: not replacing existing default route via 192.168.1.1
Feb 27 21:13:32 tydesk pppd[25315]: Cannot determine ethernet address for proxy ARP
Feb 27 21:13:32 tydesk pppd[25315]: local  IP address 192.168.100.157
Feb 27 21:13:32 tydesk pppd[25315]: remote IP address 192.168.100.180
Feb 27 21:13:59 tydesk pptp[25320]: anon log[callmgr_main-pptp_callmgr.c:231]: Closing connection (unhandled)
Feb 27 21:13:59 tydesk pptp[25320]: anon log[ctrlp_rep-pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Feb 27 21:13:59 tydesk pptp[25320]: anon log[call_callback-pptp_callmgr.c:78]: Closing connection (call state)
Feb 27 21:13:59 tydesk pppd[25315]: Modem hangup
Feb 27 21:13:59 tydesk pppd[25315]: Connect time 0.5 minutes.
Feb 27 21:13:59 tydesk pppd[25315]: Sent 22156 bytes, received 137698 bytes.
Feb 27 21:13:59 tydesk pppd[25315]: MPPE disabled
Feb 27 21:13:59 tydesk pppd[25315]: Connection terminated.
Feb 27 21:13:59 tydesk pppd[25315]: Exit.


I'm completely stuck.

Any ideas

---

### Post by spiderbatdad on 2008-02-27
Sorry I don't know a lot about this, but it looks like your trying to connect via a proxy. Did you install anon-proxy? It appears your modem connection succeeds but then tries to pass the connection along to a proxy where you get this message: "Cannot determine ethernet address for proxy ARP."
 So it seems you need to either add proxy settings to your network configuration, or remove anon-proxy and/or TOR...or whatever program you installed that is using anon-proxy.

---

### Post by o0beaner on 2008-02-27
Hmm.. No need to run through a proxy. I don't know anything about anon-proxy, nor did I voluntarily install it. It must have been packaged with something else. Would that be causing my interruptions?

---

### Post by spiderbatdad on 2008-02-27
A simple test I can think of is to run sudo apt-get update. If you get a lot of cannot connect to local host 4001...that's anon-proxy.

---

### Post by o0beaner on 2008-02-27
No connection errors  when running apt-get update.

---

### Post by spiderbatdad on 2008-02-27
Ah. I think it is the server unable to resolve ARP with your machine...maybe you need to add the sever to your whitelist in Firestarter...or the servers IP to your network hosts...'m really guessing. Hang in there. You sure to get answers.

---

### Post by o0beaner on 2008-02-27
Currently, I'm not running any firewalls. Firestarter nor iptables are installed.

---

### Post by spiderbatdad on 2008-02-27
I thought iptables was installed by default and linked to the network manager in Gutsy.

---

### Post by o0beaner on 2008-02-27
How would I access it?

service iptables stop and service firestarter stop both yield unknown service.

---

### Post by spiderbatdad on 2008-02-27
Take a look at the host settings for your connection. It should have entries like all-routers, all-hosts, all-nodes...

---

### Post by o0beaner on 2008-02-27
in my hosts, after my loopback entries, i have:



fe00::0     ip6-localnet
ff00::0     ip6-mcastprefix
ff02::1     ip6-allnodes
ff02::2     ip6-allrouters
ff02::3     ip6-allhosts

---

### Post by spiderbatdad on 2008-02-28
```
Cannot determine ethernet address for proxy ARP

This is due to an issue with the pppd program, which attempts to find a hardware interface on the subnet to which the pppd client has been assigned. In this case its looking for a hardware interface on the 192.168.5.0 subnet. It will fail to find one, and will drop the proxyarp request.

The simplest way around this problem, and the one that is suggested in the pppd documentation, is to set the pppd client IP assignment to be on the local subnet. An example in this case might be 192.168.56.129. However, it may not be possible to do that. In the case of a fully loaded subnet, there may not be any addresses to spare. Or there may be some security issues with giving out local subnet addresses. What to do?

The place to look is in the arp table. If you run tcpdump on host (192.168.56.12) during the time when client is pinging, you will see unanswered arp requests from host attempting to find the hardware address for 192.168.5.12. You need to proxy the hardware address of the pptp_srvr for client in order for this request to be fulfilled. This is the job of proxyarp. However, proxyarp has let us down in this instance, and we need to find a workaround.

This can be done manually using the arp command on pptp_srvr. For example, if the hardware address of the ethernet card on pptp_srvr is 00:60:08:98:14:14, you could force the arp to proxy the client pptp address by saying

	arp --set 192.168.5.12 00:60:08:98:14:13 pub

You should now be able to ping from client to host through the pptp connection.

This can be a problem, however, in a dynamic environment when clients are logging into and out of the pptp server on a continuous basis. One way around this problem is to write a script that will execute upon the initiation of each ppp connection.

The place to do this is in /etc/ppp/ip-up. This script is executed each time a new ppp connection is started. It gets some variables passed into it, one of which is the assigned IP address of the client. Note that RedHat systems use ip-up.local as the place for you to make the script. Don't forget to chmod +x !

#! /bin/bash

REMOTE_IP_ADDRESS=$5

date > /var/run/ppp.up
echo "REMOTE_IP_ADDRESS = " $REMOTE_IP_ADDRESS >> /var/run/ppp.up
arp --set $REMOTE_IP_ADDRESS 00:60:08:98:14:14 pub >> /var/run/ppp.up

exit 0

This should put you in business for accessing the remote subnet under this scenario. I am a little bit concerned, however, because I also built a script ip-down.local, that should remove the arp proxy when client disconnected. It doesn't seem to do anything, however, and if I try to delete the arp entry manually, it just spits out a cryptic error message. The arp entries remain persistent, as far as I can tell. If this is a problem or not, I don't know. The next few clients that log in are treated well, so I guess its OK.


```

[http://poptop.sourceforge.net/dox/qna.html](http://poptop.sourceforge.net/dox/qna.html)

---

### Post by o0beaner on 2008-02-28
So to make sure I understand correctly, following this, I need the MAC address of the NIC on the remote server?

---

### Post by spiderbatdad on 2008-02-28
That appears to be the case, and that author supplies a script to include in /etc/ppp/ip-up to run on start up. so long as the script is made executable.

---

### Post by o0beaner on 2008-02-28
This is where I have yet to develop any expertise. 

Are these lines added to ip-up anywhere? What makes the script executable or not?

---

### Post by spiderbatdad on 2008-02-28
well...that makes two of us. I would think the script would work fine at the end of the file...that file is  already  executable. but sudo chomd a+x *filename* is how you  make a file executable.
I guess I would leave off !# bin/bash as the file contains that the environment shell command.

---

### Post by o0beaner on 2008-02-28
Should I be using the lan address or the public IP?

---

### Post by spiderbatdad on 2008-02-28
lan

---

### Post by o0beaner on 2008-02-28
This is what I added. I still get the same error in syslog when I try to connect.


192.168.100.180=$5

date > /var/run/ppp.up
echo "192.168.100.180 = " $192.168.100.180 >> /var/run/ppp.up
arp --set $192.168.100.180 00:53:45:00:00:00 pub >> /var/run/ppp.up

exit 0

---

### Post by spiderbatdad on 2008-02-28
try
192.168.10.18=$5
echo "192.168.10.18 = " $192.168.10.18 >> /var/run/ppp.up
 arp --set $192.168.10.18 00:53:45:00:00:00 pub >> /var/run/ppp.up

and /var/log/messages for errors.

---

### Post by o0beaner on 2008-02-28
which logs apart from syslog should i look at?

syslog output is the same with those changes. I'm not positive that the script is located in the right place within ip-up. Should it matter?

---

### Post by spiderbatdad on 2008-02-28
I'm not positive about that either...and I wonder if this section should be commented out, at least temporarily, as it looks like it could interfere:

# if pon was called with the "quick" argument, stop pppd
if [ -e /var/run/ppp-quick ]; then
  rm /var/run/ppp-quick
  wait
  kill $PPPD_PID
fi

I was thinking look at /var/log/messages. or /var/log/pppd.log

---

### Post by o0beaner on 2008-02-28
log of last connection from /var/log/messages:

Feb 28 00:13:11 tydesk pppd[26552]: pppd 2.4.4 started by root, uid 0
Feb 28 00:13:11 tydesk pppd[26552]: Using interface ppp0
Feb 28 00:13:11 tydesk pppd[26552]: Connect: ppp0 <--> /dev/pts/2
Feb 28 00:13:12 tydesk pppd[26552]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Feb 28 00:13:12 tydesk pppd[26552]: CHAP authentication succeeded
Feb 28 00:13:12 tydesk pppd[26552]: MPPE 128-bit stateless compression enabled
Feb 28 00:13:14 tydesk pppd[26552]: local  IP address 192.168.100.124
Feb 28 00:13:14 tydesk pppd[26552]: remote IP address 192.168.100.180
Feb 28 00:13:15 tydesk pppd[26552]: Modem hangup
Feb 28 00:13:15 tydesk pppd[26552]: Connect time 0.1 minutes.
Feb 28 00:13:15 tydesk pppd[26552]: Sent 0 bytes, received 0 bytes.
Feb 28 00:13:15 tydesk pppd[26552]: Connection terminated.
Feb 28 00:13:16 tydesk pppd[26552]: Exit

---

### Post by o0beaner on 2008-02-28
Commented out that if function, same results.

---

### Post by spiderbatdad on 2008-02-28
well it's not quite the same...at least the remote address is assigned...whereas originally you had Cannot determine ethernet address for proxy ARP.

Not sure why the modem is hanging up and I'm too tired to think very well. You might consider a different program for your modem as pppoe can be troublesome. Maybe kppp or gnome-ppp as a frontend.

Going to bed. Best of luck to you. Will check back tomorrow if I think of anything.

---

### Post by o0beaner on 2008-02-28
Actually, the same problem exists. That error, for whatever reason, just didnt exist in /var/log/messages.

This is taken directly from the KVpnc window.

debug: No default interface given, tried default interface, got success, using "eth1".
debug: Using (NT) domain name "xxxxxxxxxxxxxxxxx".
debug: Username: xxxxx
debug: Trying to connect to server "xx.xx.xx.xx" with user "xxxxx"... 
debug: [pppd] Using interface ppp0
debug: [pppd] Connect: ppp0 /dev/pts/2
debug: [pppd] Warning - secret file /etc/ppp/pap-secrets has world and/or group access
debug: [pppd] CHAP authentication succeeded
debug: [pppd] MPPE 128-bit stateless compression enabled
debug: [pppd] not replacing existing default route via 192.168.1.1
debug: [pppd] Cannot determine ethernet address for proxy ARP
debug: [pppd] local IP address 192.168.100.166
debug: [pppd] remote IP address 192.168.100.180
success: Successful connected to server "xx.xx.xx.xx" user: "xxxxx" at Thu Feb 28 00:23:14 2008 [PPTP]
success: Connection established.

Stayed connected for about 10 seconds, then bombed out again.

Thanks much for all the effort. Here's hoping for a solution.

---

### Post by spiderbatdad on 2008-02-28
Had one last thought, and you last post kind of confirms...eth will compete with your modem you should disable all eth connections.

---

### Post by o0beaner on 2008-02-28
but this is over a tcp/ip connection, using an ethernet card. if i disable my eth connections, im going to get network unreachable errors. correct?

---

### Post by spiderbatdad on 2008-02-28
> **o0beaner said:**
> but this is over a tcp/ip connection, using an ethernet card. if i disable my eth connections, im going to get network unreachable errors. correct?

That only shows how little I understand what is happening. I assumed the modem connection was an adsl your were using. 

debug: No default interface given, tried default interface, got success, using "eth1".
debug: Using (NT) domain name "xxxxxxxxxxxxxxxxx".
debug: Username: xxxxx
debug: Trying to connect to server "xx.xx.xx.xx" with user "xxxxx"...
debug: [pppd] Using interface ppp0

I don't know how else to interpret this...using  ppp0 interface, as far as I know is your modem interface.

One thing I noticed reading a little more of that article containing the connection script you've been trying, is that he says you must set a static ip address for yourself (client.)

---

### Post by o0beaner on 2008-02-28
Yeah I've tried with both dynamically assigned and static addresses. I typically have a static address on that machine, so I went that route first.

---

### Post by spiderbatdad on 2008-02-28
bleh.

---

### Post by spiderbatdad on 2008-02-28
I can't tell for sure whether that proxyarp script is intended to go in the pptp_svr or the client. It appears to me now to be intended for the server.

After reading a dozen pages on this modem hang up error, the consensus seems to be firewall is blocking:
"Firewall isn't configured correctly

If this is the case you should see logs from your firewall blocking things from your ip to my.vpn.server, but in case it helps, here is what it looks like from the pppd logs.

When the firewall is blocking things

pppd[25387]: pppd 2.4.4 started by root, uid 0
pppd[25387]: Using interface ppp0
pppd[25387]: Connect: ppp0 <--> /dev/pts/7
pptp[25388]: anon log[main:pptp.c:276]: The synchronous pptp option is NOT activated
pppd[25387]: LCP: timeout sending Config-Requests
pppd[25387]: Connection terminated.
pppd[25387]: Modem hangup
pppd[25387]: Exit.

---

### Post by o0beaner on 2008-02-28
So where would I look to do that? Or what should I do rather?

I was under the impression that I didnt have one running. I didn't have to configure anything to allow VNC or ssh connections out of the box.

---

### Post by spiderbatdad on 2008-02-28
I wish I could give a definitive answer. From what I'm learning, two connections are being established. The lan connection and the ppp0 connection. The latter apparently should be taking place on port 1723 (I think, can't find it again yet.) You can set the modem port in your network configuration settings. 

Is the server Red Hat based? That would affect where you would locate the proxyarp assigning script. 

Take a look at the set up on Arch linux: [http://wiki.archlinux.org/index.php/Microsoft_VPN_client_setup_with_pptpclient](http://wiki.archlinux.org/index.php/Microsoft_VPN_client_setup_with_pptpclient)
where he talks about "touch mycon" where the server id in chap-secrets didn't match the remote name in his connection file.

---

### Post by o0beaner on 2008-02-28
no, its a Windows 2003 environment.

---

### Post by spiderbatdad on 2008-02-28
Ok so that last link should translate to your application fairly well. Logged in as root, in your chap-secrets you should have the following: 

Of those files we only need to muck with options.pptp and chap-secrets

My options.pptp file has these options set

lock
noauth
refuse-eap
refuse-chap
refuse-mschap
nobsdcomp
nodeflate


In chap-secrets put username, password, a name to identify the server and a * for ip addresses

```
DOMAIN\\MyUserName TheServer MyPassWord *
```

Note: If your pptp server does not require a domain name, leave it and the slashes out.

Yes you really did just put your password in a file in plain text, so

```
chmod 600 chap-secrets
```

If it wasn't already that way.

Now its time to define our vpn connection: 

First
```

mkdir peers; cd peers

```
Now come up with a name for your connection, I'll call it myCon.

```
touch myCon

```
Add the following lines with your editor of choice, making sure that the variables match what you defined in chap-secrets:

```
remotename TheServer
ipparam myCon
pty "pptp my.vpn.server --nolaunchpppd"
name DOMAIN\\MyUserName
usepeerdns
require-mppe-128
refuse-eap
noauth
file /etc/ppp/options.pptp
```



With that you should be able to execute the following command

```
pon myCon
```


Issuing

```
ifconfig ppp0
```

Hope this helps.

---

### Post by o0beaner on 2008-02-28
so lets see

in my chap-secrets, i have the following:


# Secrets for authentication using CHAP
# client        server            secret                  IP addresses


So 

Client = username
Server = (confused on what to put here...)
Secret = password
IP addresses = *


Correct? Aside from server anyway...

---

### Post by spiderbatdad on 2008-02-28
It appears to me the line that gets put in chap-secrets is

DOMAIN\\MyUserName TheServer MyPassWord *

Where DOMAIN is literal. TheServer would be the name of the sever connection.

And in peers the directory you create. my.vpn.server (I'm assuming) is an ip address. To bad the instructions aren't geared a little more toward novice level.
You should have the peers directory in /etc/ppp already. Just create an executable text file with the needed info.

---

### Post by o0beaner on 2008-02-28
anyone able to put this in just a little more of a dumbed-down form?

---

