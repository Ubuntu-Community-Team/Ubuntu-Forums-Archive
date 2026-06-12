---
title: "error on connecting with pidgin"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Ryadt on 2008-01-21
hi...can someone please help me...it just seem every now and then when I try to use pidgin    
i get an error message saying:'connection error from Notification server:Writing error'
your help will be greatly appreciated.

---

### Post by Kulgan on 2008-01-21
What protocoll are you using? MSN, Jabber, etc. Have you tried with another client? Could always check it by connecting to the Ubuntu IRC channel, server: irc.freenode.net, channel: #ubuntu. 
Another thing you could do to illiminate the possibility of an error in the configuration:
```
mv ~/.purple ~/.purple_bk
```

This will back up your config in a place that pidgin will not look for it. If that doesn't work, you can restore it by moving it back:
```
mv ~/.purple_bk ~/.purple
```

Other than that, I have never encountered that specific error before, so I can only assume it's protocoll specific.

---

### Post by Ryadt on 2008-01-21
thx for your reply..
I am using msn and google...
both does not want to connect

---

### Post by Kulgan on 2008-01-21
I see...
You say "every now and then" - I take it that means it works as well, so there shouldn't be anything wrong with the config. Sorry I missed that part first time round. 

This sounds more like a local network issue then. I take it there isn't anything odd going on with port forwarding on the router, or some highly secure firewall settings preventing the servers from acting as a two-way host?

---

### Post by Ryadt on 2008-01-21
I thought it was a port or router problem..but i am really crap when coming on hardware issues...

---

### Post by Kulgan on 2008-01-21
Hehe, you're not alone. I hate NAT with a passion. 

What you could also do is try starting pidgin from the terminal. That should give a better foundation to work on. To get all the debug info, enter in the terminal:
```
pidgin -d > dbg.txt
```
Then upload the dbg.txt file as an attachment. You'll have to keep repeating this until you get the error you want. Each time you run the command, the file will be started from scratch, so you don't have to worry about cleaning out any previous successful starts. 

btw, when there's an error, is it both gmail and msn at the same time, or do they sometimes give errors on their own?

---

### Post by Ryadt on 2008-01-21
Wow am not alone....\\:D/
anyway the problem occurs with both of them at the same time....

---

### Post by Kulgan on 2008-01-22
could you post the debug, so that the problem is clearer?

---

### Post by taduikis on 2008-01-22
I had prblem when logging in with google.
I solved it by changing domain from google.com to googlemail.com
Hope it helps.

---

### Post by Kulgan on 2008-01-22
That depends on what you use to send/recieve mail (and it should be gmail.com anyway: [http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073](http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073) )

That wouldn't explain why the MSN account also disconnects. The log is the clearest way to tell what's going wrong - Ryadt, if you need help with getting it, let me know.

---

### Post by AdamPond on 2008-03-16
> **Kulgan said:**
> That depends on what you use to send/recieve mail (and it should be gmail.com anyway: [http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073](http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073) )

That wouldn't explain why the MSN account also disconnects. The log is the clearest way to tell what's going wrong - Ryadt, if you need help with getting it, let me know.

I'm getting this problem too when connecting to **MSN **using HTTP method with a proxy on the windows version (yes, I know this is an Ubuntu forum, but it seems to be a generic problem that is not OS related, and the most relevant and recent post I could find). I can fire up an ubuntu VM session if necessary to test if that will help.

**Pidgin v****2.4.0**

My gut feel is that the problem may be a timing issue as it consistently happens without debug information, doesn't happen if debug information is shown in console, and is inconsistent if the debug info is piped to a file.

Relevant log information:

...

(13:25:49) account: Connecting to account [email]me@hotmail.com[/email]
(13:25:49) connection: Connecting. gc = 010101A8
(13:25:49) msn: new httpconn (0104AD70)
(13:25:49) dnsquery: Performing DNS lookup for 10.123.123.9
(13:25:49) msn: C: NS 000: VER 1 MSNP9 MSNP8 CVR0
(13:25:49) dnsquery: IP resolved for 10.123.123.9
...
(13:25:49) proxy: Attempting connection to 10.123.123.9
(13:25:49) proxy: Connecting to gateway.messenger.hotmail.com:80 via 10.123.123.9:3128 using HTTP
(13:25:49) proxy: Connection in progress
(13:25:49) proxy: HTTP proxy connection established
(13:25:49) msn: Connection error from Notification server (gateway.messenger.hotmail.com): Writing error
(13:25:49) msn: C: NS 000: OUT
(13:25:49) msn: Attempted HTTP write before session is established
(13:25:49) msn: Connection error from Notification server (gateway.messenger.hotmail.com): Writing error
(13:25:49) msn_session_disconnect: assertion `session->connected' failed

...

(13:26:05) dnsquery: Performing DNS lookup for 10.123.123.9
(13:26:06) account: Connecting to account [email]me@hotmail.com[/email]
(13:26:06) connection: Connecting. gc = 0101F930
(13:26:06) msn: new httpconn (00C8EFA0)
(13:26:06) dnsquery: Performing DNS lookup for 10.123.123.9
(13:26:06) msn: C: NS 000: VER 1 MSNP9 MSNP8 CVR0
(13:26:06) dnsquery: IP resolved for 10.123.123.9
(13:26:06) proxy: Attempting connection to 10.123.123.9
(13:26:06) proxy: Connecting to gateway.messenger.hotmail.com:80 via 10.123.123.9:3128 using HTTP
(13:26:06) proxy: Connection in progress
(13:26:06) proxy: HTTP proxy connection established
(13:26:06) msn: Connection error from Notification server (gateway.messenger.hotmail.com): Writing error
(13:26:06) msn: C: NS 000: OUT
(13:26:06) msn: Attempted HTTP write before session is established
(13:26:06) msn: Connection error from Notification server (gateway.messenger.hotmail.com): Writing error
(13:26:06) msn_session_disconnect: assertion `session->connected' failed
(13:26:06) account: Disconnecting account 00C8C650
(13:26:06) connection: Disconnecting connection 0101F930
(13:26:06) msn: destroy httpconn (00C8EFA0)
(13:26:06) connection: Destroying connection 0101F930

...

This repeats itself a few times in the log before I closed the session

---

### Post by bartkl on 2008-05-21
I have the same problem and I found this:
[http://developer.pidgin.im/ticket/1217](http://developer.pidgin.im/ticket/1217)

I cite from one of the last comments there:
> 
I have an OpenBSD router/firewall that has a scrub line that causes the connect problem (MSN)

scrub on $ext_if all reassemble tcp

Removing this line from the pf firewall fixes the error.

Another solution (for linux clients), is to disable the tcp_timestamps:

echo 0 > /proc/sys/net/ipv4/tcp_timestamps
or 
sysctl net.ipv4.tcp_timestamps=0

I hope this helps 


Is it safe to try this? And if so, would there be disadvantages to disabling tcp_timestamps?

Thanks

---

### Post by Kulgan on 2008-05-21
I can't say I see any problems with that - but I'm by no means an expert. If it doesn't help, you can always undo it my issuing:
```
echo 1 > /proc/sys/net/ipv4/tcp_timestamps
```

---

### Post by bartkl on 2008-05-21
Yes, so I figured out, but thanks :)
I'm just wondering if it won't result into trouble that I will run into a long time from now (say months), without possibly guessing this would be the thing that messed it up.

Anyways, I've tried it for a few hours and it actually seems to work for me.
I was able to connect by the way, but Pidgin would disconnect with the error described by the topic starter once in at least 30 minutes.
Now I'm running Pidgin for some hours without trouble. Perhaps it works.

---

