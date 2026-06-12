---
title: "Caller-ID Serving Over Growl?"
date: 2009-01-28
forum: Apple Hardware Users
---

### Post by rshnike on 2009-01-28
Hey everyone.

Anyone have any ideas on first setting up my Ubuntu Server box to pull Caller-ID info from my telephone line that's plugged into its modem and then maybe send that info over the network as a growl notification to my macs?

I see that there really isn't any nice looking way to send growl notifications from a linux box but I did see a PHP script here: [http://clickontyler.com/php-growl/](http://clickontyler.com/php-growl/)

but I'm not quite sure how to implement it. (I assume I'd need to add LAMP to this server yes?)

Thanks a lot!

---

### Post by cyberdork33 on 2009-01-28
Well, that is just a class, so you would still have to write the php script that utilizes these functions to send the events. You probably only need php not a whole lamp stack though (I didn't read it too deeply yet.)

Wither way, you will probably need a little PHP knowledge to get that working.

I don't think GROWL would care whether events came from Linux or OSX (or windows even), as long as the messages are formatted properly (which the class you got should help with). and OSX isn't blocking the port you need.

You will also probably need an application or script that can read the Caller-ID data and put it in a format that you can send over the network for the Growl notification. This part is definitely not Mac-related, so you could probably get better help with that somewhere different.

Sounds like an interesting project though. Could even be scaled up so that a Linux server can send status messages to your desktop when certain events occur (disk space getting low, a torrent is done downloading, TV show done recording, etc.) I am almost surprised this doesn't exist yet.

---

### Post by rshnike on 2009-01-28
> **cyberdork33 said:**
> 
Sounds like an interesting project though. Could even be scaled up so that a Linux server can send status messages to your desktop when certain events occur (disk space getting low, a torrent is done downloading, TV show done recording, etc.) I am almost surprised this doesn't exist yet.

So am I. I don't know too much PHP but lets see what happens with a little research... I'm curious as to whether I could implement the same functionality in Python which I'd be much more comfortable with.

Oh well. Some work to do over the next couple of weeks. If I find anything interesting I'll try to post it here.

Thanks for the help.

EDIT: Well, the local version in python is here... [http://growl.info/documentation/developer/gnotify.php](http://growl.info/documentation/developer/gnotify.php)

Probably needs to be dissected to do what I'd want. Ok. Tinkering ahead.

---

### Post by cyberdork33 on 2009-01-28
should be able to port from php to python relatively easily. php is not a hard language though and there are a lot of resources out there for it (much like python).

EDIT
Oh you owe me a beer...

[http://the.taoofmac.com/space/Projects/netgrowl](http://the.taoofmac.com/space/Projects/netgrowl)

and here is something similar with some type of telephony equipment... Unfortunately it is all in german.
[http://www.wehavemorefun.de/fritzbox/index.php/Mac_OS_X](http://www.wehavemorefun.de/fritzbox/index.php/Mac_OS_X)

---

### Post by rshnike on 2009-01-28
> **cyberdork33 said:**
> should be able to port from php to python relatively easily. php is not a hard language though and there are a lot of resources out there for it (much like python).

EDIT
Oh you owe me a beer...

[http://the.taoofmac.com/space/Projects/netgrowl](http://the.taoofmac.com/space/Projects/netgrowl)

and here is something similar with some type of telephony equipment... Unfortunately it is all in german.
[http://www.wehavemorefun.de/fritzbox/index.php/Mac_OS_X](http://www.wehavemorefun.de/fritzbox/index.php/Mac_OS_X)

Hah. I'll gladly send over that beer, and I also found this:

[http://code.google.com/p/pygnotify/](http://code.google.com/p/pygnotify/)

though the instructions are unclear and I haven't gotten it working yet though I've only spent a half hour on it. I'll try that link out that you found too. I'll let you know.

Edit: Looks like that site I was working on was working off the code you found. I'm gonna see if I can get it working with just that one script netgrowl, so far looks promising. The python parts I do ok on. It's the Ubuntu side I might ask for help for later to configure the server to send messages at whatever events I'd choose (like you said for low disk space etc.).

Thanks again!

---

### Post by threadhead on 2009-02-08
rshnike,
I'm interested in doing the same.

What modem are you using? and what software/app are you using to pick-up the CID in Ubuntu?

Thx.

---

### Post by rshnike on 2009-03-11
The growl side has turned out to be brutally simple. The caller id end is slightly more complicated but looks doable. I've been working with cid (found here: [ftp://ftp.tummy.com/pub/tummy/cid/](ftp://ftp.tummy.com/pub/tummy/cid/)) but it's deprecated (and the code is obfuscated as well). I should be able to get it working though I just haven't had the time (February was incredibly fast). I'll post back if (hopefully when) I get it working.

---

