---
title: "Office communicator"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by He|iX on 2007-08-16
Hi, is there an application in ubuntu that can talk to MS communicator 2005? We use this around the office to IM people, any ideas?

---

### Post by mojorising on 2007-08-17
I am searching around for the same thing. 

There is this plug-in:
[http://sipe.sourceforge.net/](http://sipe.sourceforge.net/)

It does have to be built with a special Pidgin plugin build tool, I believe, which I have yet to try. 

If your office uses the Communicator web client, that is an option. Mine, I believe does not so I need to make it work on the desktop.

The only posts I found on this forum are [http://ubuntuforums.org/showthread.php?t=91083&highlight=lcs+communicator](http://ubuntuforums.org/showthread.php?t=91083&highlight=lcs+communicator) (very old) and [http://ubuntuforums.org/showthread.php?t=344748&highlight=communicator](http://ubuntuforums.org/showthread.php?t=344748&highlight=communicator) (has no replies).


If anyone has info on a good way to do this, please post it here. I'll do the same if I find anything. 


Thanks,
Mike

---

### Post by Jamie Jackson on 2007-08-22
Yeah, there's a plugin for Pidgin (pidgin-sipe). It's not in the official repos yet, but you can add a repo to get it (further down in this message).

Caveat: It doesn't work through TLS yet, so if your company enforces it, you're out of luck, for the moment. However, I got an email from the pidgin-sipe developer last Friday:
> 
Je, efectively my plugin-in doesn't have TLS support yet.

I hope to do this weekend, because is easy but I have been very busy
the last weeks :(

Please be patient ..


I doubt he got it done last weekend, but I do know it's the next task on his list.

As far as getting pidgin in Ubuntu, this seems to be your best bet. The guys running the backported pidgin repo have been communicating here: [https://bugs.launchpad.net/baltix/+bug/112511](https://bugs.launchpad.net/baltix/+bug/112511)

> 
In addition to the inclusion of these extra packages, Trausch and I have
also created an apt repository for all of our backports.  You'll be able
to get the following packages (i386, AMD64, and source):

To add our repository to your apt source.list, simply add the following
lines:

deb [http://www.ansemreport.com/pidgin/repo](http://www.ansemreport.com/pidgin/repo) feisty feisty-backports
deb-src [http://www.ansemreport.com/pidgin/repo](http://www.ansemreport.com/pidgin/repo) feisty feisty-backports

pidgin
pidgin-blinklight
pidgin-data
pidgin-dbg
pidgin-dev
pidgin-encryption
pidgin-extprefs
pidgin-guifications
pidgin-hotkeys
pidgin-libnotify
pidgin-librvp
pidgin-otr
pidgin-plugin-pack
[pidgin-sipe]
gaim-xfire    --works with Pidgin, despite the gaim naming convention
libotr2
libotr2-bin
libotr2-dev
musictracker
nautilus-sendto
gaim (transitional)
gaim-extendedprefs (transitional)
gaim-guifications (transitional)
gaim-hotkeys (transitional)
gaim-irchelper (transitional)
gaim-libnotify (transitional)
gaim-thinklight (transitional)


---

### Post by scarolan on 2007-08-23
I am trying to get SIPE working as well, here is the final output from debug mode.  My IP addresses have been replaced with IPADDRESS

######
SIP/2.0 404 Not found.
Via: SIP/2.0/TCP IPADDRESS:5060;branch=z9hG4bK69B1CF6C5968BB8D2DC5;ms-received-port=55558;ms-received-cid=80300
From: <sip:sean.carolan@IPADDRESS>;tag=2869627959;epid=1234567890
To: <sip:sean.carolan@IPADDRESS>;tag=1E7CFE51A02F53D3CEF96B3543AC0B6F
Call-ID: AAF6g4468aF6BEi6DB0mD200t4BC9b1B93x81CAx
CSeq: 3 REGISTER
Content-Length: 0

#######

(12:19:21) sipe: in process response response: 404
(12:19:21) sipe: msg->response(404),msg->method(REGISTER)
(12:19:21) sipe: RE-REGISTER
(12:19:21) sipe: in process register response response: 404
(12:19:26) util: Writing file accounts.xml to directory /home/scarolan/.purple
(12:19:55) sipe: sipe_input_cb: read error

Anyone have an idea how I can fix this?

---

### Post by Prometheus7 on 2007-08-28
This sounds great and I'm sure that a lot of people will use it, but how can we check and be sure that there isn't any sort of spyware in it?

Any word on TLS implementation?

---

### Post by mlabelle on 2007-08-29
> **Prometheus7 said:**
> This sounds great and I'm sure that a lot of people will use it, but how can we check and be sure that there isn't any sort of spyware in it?

Any word on TLS implementation?

A good thing about open source software is that you can read the source :lolflag:

---

### Post by mojorising on 2007-08-30
From what I hear, TLS should be implemented very soon (within weeks, I hope).

Jamie, thanks a ton for the replies. 


Mike

---

### Post by Jamie Jackson on 2007-08-31
> **mojorising said:**
> From what I hear, TLS should be implemented very soon (within weeks, I hope).

Jamie, thanks a ton for the replies. 


Mike

Yup. While I was on vacation, it looks like folks have been testing the (very experimental, at this point) TLS implementation. Maybe some folks here could help with the debugging, as the developer doesn't have a TLS server to test against, and nobody's gotten 100% success out of it.

---

### Post by mojorising on 2007-08-31
Awesome. I want to test TLS as I have it here and its use is forced at my office's server. 

Forgive me if this has already been revealed or I'm just blind but the only problem is I can't find any files for this new experimental release your talking about. I checked the new project page at ([https://sourceforge.net/projects/sipe](https://sourceforge.net/projects/sipe)) and web site (sipe.sf.net). is this release in your apt repository? Where can we get it?


Mike

---

### Post by Jamie Jackson on 2007-08-31
Note: The developer (fixxxer) has renamed the project from (Pidgin) SIPE to (Pidgin) SipLCS.

I'm not familiar with the GIT SCM, but it appears that's where it's held:
[http://repo.or.cz/w/siplcs.git?a=shortlog;h=fixer](http://repo.or.cz/w/siplcs.git?a=shortlog;h=fixer)

And instructions for this particular repository are here: [http://sipe.sourceforge.net/cogito/](http://sipe.sourceforge.net/cogito/)

Once TLS is tested successfully, I'll ask the maintainers of that Ubuntu repo (that I posted earlier) to compile and post it to replace the current pidgin-sipe package.

---

### Post by Prometheus7 on 2007-09-28
How is this going? Can I help test if it is still needed?

---

### Post by Jamie Jackson on 2007-09-28
Well, it seems development has [stalled]("http://developer.pidgin.im/ticket/48") due to the developer's commitments.  I've been very anxious to have this plugin, because LCS communication is all but required at my company.

I'm hoping someone else will pick up the slack. I would, but I have any of the requisite skills. :(

---

### Post by mojorising on 2007-11-05
Thought others out there who have to use LCS might want to know about the LCS web client. 

I'm using it at my office on Firefox and it works pretty well. Of course, I'd much rather have a real local application instead of the web client but this gets me through, 

Hopefully some others out there can try this as an option and hopefully the Pidgin plugin gets finished (or at least functional) some time relatively soon. 


Mike

---

### Post by scarolan on 2008-01-08
I have got to the point with pidgin-sipe where I can see everyone on my buddy list.  Obviously it is authenticating and grabbing this data from the server.  I can't actually send or receive IMs to anyone.  Anyone have suggestions on how to correct this?

---

### Post by Woody AZ on 2008-03-11
Seems to be the limits of the 1.2 release.  I have yet to find a way to have any native connection to LCS under Ubuntu.  Thank goodness for virtualbox!  :)

---

### Post by mojorising on 2008-05-26
Unfortunately, it appears much hasn't happened on this in the last year or so since work on the Pidgin plug-in was last updated. 

Anyone who's interested in seeing a working LCS plug-in for Linux can post a note at the below locations to request it gets a little more attention. 


The LCS plug-in page for Kopete (be sure to register and vote for this bug to be moved up in priority):
[http://bugs.kde.org/show_bug.cgi?id=110402](http://bugs.kde.org/show_bug.cgi?id=110402)

The LCS plug-in page for Pidgin:
[http://developer.pidgin.im/ticket/48](http://developer.pidgin.im/ticket/48)


I suspect the more people who ask for this functionality, the more likely it is developers will see a need to develop it and respond to that need. 

I only wish I had the programming skill (I'm a server/ networking person) so I could just contribute the plug-in myself. 


Mike

---

