---
title: "Kopete &amp; Gaim : &quot;Connection Actively Refused&quot;"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Her Ghost on 2007-08-27
Hi, I'm struggling to connect to msn using both Kopete and Gaim.

When I try to log in I get an error message saying that the connection is actively refused.

If I switch to "Use HTTP Method" then it allows me to connect and see people's online status, but I can't send messages, and if people send them to me, I get no notification.

I have currently got a dual boot set up with Windows XP and I can still log into and use messenger through that.

I was originally using Kopete, but when it failed I tried Gaim, but got the same results.

Has anyone experience this before?  Does anyone know of a fix?

Thanks, 
Leigh

---

### Post by Her Ghost on 2007-08-27
just tried running it through the console to see if I can get anything more verbose from it:

```

leigh@leigh-desktop:~$ kopete
leigh@leigh-desktop:~$ kopete (msn): WARNING: [void MSNSocket::slotSocketError(int)] Error: 10 (connection actively refused)


```

---

### Post by Jimmyfj on 2007-08-27
Have you tried installing aMSN instead to see if you get the same error from that? 

you can download aMSN from [http://www.getdeb.net](http://www.getdeb.net)  or

[http://www.getdeb.net/download.php?release=1116&fpos=0](http://www.getdeb.net/download.php?release=1116&fpos=0)

---

### Post by Her Ghost on 2007-08-28
yep - aMSN does exactly the same...

---

### Post by Her Ghost on 2007-08-28
right, I've narrowed this down a bit, but I'm quickly getting out of my depth..

My router has port 1863 forwarded for the MSN connection.  This appears to be working, since I can connect through windows.  However, using canyouseeme.org in kubuntu I get a message that this port isn't forwarded correctly...it can't be both!!

**So, my question now becomes, is there an internal mechanism through which kubuntu might be blocking the forwarding of a port?**

---

### Post by Zimmer on 2007-08-28
I am experiencing problems sending URLs  using GAIM to my son who is using an old !LIVE beta and he cannot send them to me either,  error message of client mismatch, have not had these problems previously.
So, maybe the new MSN Live stuff server side causing the problems with 3rd party apps?

My account is an old free hotmail.com address  , in case that might be relevant...

---

### Post by Her Ghost on 2007-08-28
right, I've definately narrowed this down to a kubuntu issue now, I think.  I put my computer in the DMZ of the router and still got the same issues.  

As I understand it, doing this removed the router from the equation?  So it has to be related to kubuntu since the connections works on windows..

---

### Post by AirRaven on 2007-08-28
Oddly enough, I've been getting this same issue sporadically- on the occasions that I *do* manage to connect, conversations "time out" rather frequently, meaning that no messages sent for a while actually get through until I get a "contact has left the chat" notification, which seems to allow the conversation to "renew" itself, renewing the connection and letting more messages get through. 

The symptoms remind me of a "timeouts" problem [Miranda](http://miranda-im.org/) used to have with their MSN protocol plugin- as far as I know, it needed fixing at the source level.

Sounds pretty similar, though.

---

### Post by SunnyRabbiera on 2007-08-28
well even here on PClinux I have the same basic issue...
it might be an issue with the client

---

### Post by Her Ghost on 2007-08-29
thought I would update for the sake of closure (to some degree):

I still do not understand what the actual problem was here.
I had changed my router from a Zoom X3 to a Belkin 54g Wireless.  Beforehand, XP worked fine and Kubuntu worked fine.  Afterwards, XP worked fine but Kubuntu threw up the issues above.

This led me to conclude that the problem was in fact with Kubuntu, since the new router was still working with XP.

I became suspicious of the functionality of the router because I was also having trouble forwarding ports (note that on my Zoom, I didn't need forwarded ports for MSN to work).  Basically my kTorrent connections were now all now "not clever".

Belkin Tech Suport told me that there were some known issues, but that the fix was to download a programme called DrTCP from dslreports.com....this struck me as odd since he seemed to be essentially admitting that their product doesn't function without a third-party application that...(drumroll) only works on Windows!  (It was actually a struggle to keep the guy talking to me after he figured out that Kubuntu was not just my odd regional pronunciation of Windows and was in fact a GNU/Linux distro!)

So what have I learned that I can pass on to you?

1. It could be a Kubuntu/Belkin config/compatibility issue
2. The Zoom X6 works a treat, has FAR superior documentation, FAR superior functionality (that I can go into for you, if you like) and costs £10GBP less at PC World (UK) than the Belkin 54g does!

I hope this helps someone, in some way.  :)

Thanks again to everyone who tried to help, above.  <3

---

### Post by Zalbor on 2007-08-29
I've read that something changed in the MSN servers and you can't connect using HTTP any more, except with the official client. The amsn people at least are working on it, but there's no clue when it will work again.

---

### Post by Her Ghost on 2007-08-29
I found that I could connect and see other users, but that they couldn't see me (and obviously messages could not be sent) when using HTTP method.

both messengers work fine now for me though.

---

### Post by Zimmer on 2007-08-30
I also 'resolved' the issue with URLS  not being sent in IM messages.. 
It is 'censorship' by aMSN.
See
[http://www.amsn-project.net/forums/viewtopic.php?t=157&postdays=0&postorder=asc&start=0](http://www.amsn-project.net/forums/viewtopic.php?t=157&postdays=0&postorder=asc&start=0)

---

### Post by por100pre1 on 2007-08-30
> **Zimmer said:**
> I also 'resolved' the issue with URLS  not being sent in IM messages.. 
It is 'censorship' by aMSN.
See
[http://www.amsn-project.net/forums/viewtopic.php?t=157&postdays=0&postorder=asc&start=0](http://www.amsn-project.net/forums/viewtopic.php?t=157&postdays=0&postorder=asc&start=0)

Actually Microsoft server censorship, aMSN is not at fault.

---

### Post by Zimmer on 2007-08-30
ooPS!  
I knew I should have typed M$ !!

Sorry..

---

### Post by vodkaPT on 2007-12-24
I have the same problem, and i try other Router and it works, so the problem is in Belkin :\

---

