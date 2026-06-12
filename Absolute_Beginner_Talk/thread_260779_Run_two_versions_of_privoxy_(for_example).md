---
title: "Run two versions of privoxy (for example)"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Sarisar on 2006-09-19
Strange question I know, but I was wondering if I could run two versions of privoxy on two seperate ports.

I run privoxy normally by itself, and connect through there.  I've played around with the setup to block cookies etc.

I am pondering running tor and understand you need privoxy to do that, but I presume I can't run both through the same one without mucking about with settings, so can I run two versions of privoxy (and is that a good idea?)

If someone could give general comments on how to run two versions of a single program that would be cool as whilst I've been on ubuntu for about 6 months now there are still some things I can do in windows but don't know how to do the same things in ubuntu :(

In windows you could change the install path and change the files to make it use a different port.  Is it this simple here in ubuntu? (I didn't want to play and break my machine (again) so thought I'd ask).

Cheers

---

### Post by Sarisar on 2006-09-22
OK kI managed to get it working so I'll try and explain what I did... but forgive me if I miss anything!

Look for 'privoxy' files  directories and copy them as 'privoxy-tor':
/usr/sbin/privoxy
/etc/privoxy
/etc/init.d/privoxy
/var/run/privoxy.pid
(although that last one may be pointless?)

Amend /etc/init.d/privoxy-tor changing privoxy for privoxy-tor in all cases EXCEPT owner, keeping that as privoxy (otherwise I'd have to make a new user up?

Amended /etc/privoxy-tor/config
Changed following lines (these are the amended lines):
confdir /etc/privoxy-tor
logdir /var/log/privoxy-tor
listen-address 127.0.0.1:8008

I also disabled remote toggle and edit actions (more on actions in a moment)

Add in the 'forwards' lines as follows:
forward / localhost:9050 .
forward-socks4a / localhost:9050 .

Delete action and filter files from /etc/privoxy-tor and then replace them with links to the original /etc/privoxy files.

I also had to sort some permissions out on the /etc/privoxy-tor directory to match /etc/privoxy (privoxy and adm I think).

Then ran:
/etc/init.d/privoxy-tor start
/etc/init.d/tor start
and then pointed proxy to 8008 to confirm it's working.  Google.com redirects me to google.de so seems to be running :)

So did I make that 10 times harder then needed or not?  Yes I did keep looking at it since I posted the first comment (not fill time though!)

Hope this helps someone :)

---

### Post by skymt on 2006-09-22
You don't need Privoxy for Tor, they just work well together. You can tell your browser to connect directly to the Tor port using SOCKS, it works perfectly.

---

### Post by Sarisar on 2006-09-23
I thought you had to run something like privoxy because tor doesn't clear everything out properly and they can work out who you are if you don't.

[Like this page]("http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#head-45dbb889ebbf4f80662c9b821924e9c083f30eea") which states:
> 
Tor presents a SOCKS interface to applications, so any application that supports SOCKS (versions 4, 4a and 5; 4a is necessary for accessing hidden services in Tor) can be anonymized using Tor. Most web browsers, many instant messaging and IRC clients, SSH clients and email clients already have built-in support for SOCKS.

Since Tor does not anonymize message content, additional software agents should be used to anonymize content. For example, Privoxy is a good HTTP proxy for filtering dangerous web content. 

I don't mean to disagree with you, just want to know the correct answer :)

---

### Post by skymt on 2006-09-23
If you run Tor without Privoxy, "they" can track your website viewing, but can't find your IP. "They" know one person is going to x sites (assuming, of course, they have cookies/web bugs on all the sites you go to), but "they" don't know who. With Privoxy + Tor, every page view is unconnected to all the others, as far as "they" know.

If all you want to do is protect your IP, plain Tor is fine.

Also, if you don't clear your cookies before surfing without Tor, "they" can find you that way.

---

### Post by Sarisar on 2006-09-24
Ahhh OK, so they pick up the 'referrer' tag then presumably?

Cheers for the info :)

---

### Post by skymt on 2006-09-24
> **Sarisar said:**
> Ahhh OK, so they pick up the 'referrer' tag then presumably?

Cheers for the info :)

That's one thing. Cookies and web bugs are also used. All those methods can be blocked with Privoxy.

---

