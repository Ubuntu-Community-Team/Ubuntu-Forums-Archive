---
title: "New IP Address"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-09-10
Hey guys. I was thinking about possibly creating a server for web hosting, so I think a new dedicated IP address would be nice to have. I found this link ([http://www.usefulutilities.com/support/technote/2l.html](http://www.usefulutilities.com/support/technote/2l.html)) that shows me how. Do you think this would work? If not, how I could? Thanks.

---

### Post by CaptainInsaneO on 2007-09-10
I don't see any reason why it wouldn't work. Get apache though. :)

---

### Post by bodhi.zazen on 2007-09-10
You might also like to check out dyndns :

[http://www.dyndns.com](http://www.dyndns.com)

You can obtain a static IP from them at no cost , well up to 5 domains at no cost ...

They have excellent how-to to get you up and running as well

HTH

---

### Post by drndrw on 2007-09-10
Oh, okay. So then do I need apache installed to run that? Also, how can I find out whether the ip I specify is taken or not? Thanks.

---

### Post by armandh on 2007-09-10
dyndns works by a program on your computer pinging your line to discover your dynamic IP and reports it to dyndns so it may be kept linked to your URL [I have been told, no first hand] I find my dynamic IP will remain static for over a month unless I leave nothing up or loose power.
[http://70.243.155.59/FLASH_2_1_1/diy2url.htm](http://70.243.155.59/FLASH_2_1_1/diy2url.htm)
it even runs linux, uses very little power

---

### Post by CaptainInsaneO on 2007-09-10
Apache is just web server software. I'm working on a website for my mom right now and run apache so she can check it out straight from my computer. I'll buy hosting and a domain when it's finished :)

You need to have SOME way to host your content in order for it to be a website, but apache is not required. You can use ANY web server suite.

---

### Post by drndrw on 2007-09-10
Yeah, I know. So I guess what my question is, is that if I follow the steps in that link I listed at the beginning, I should be able to type that web adress into any computer and I should see whatever web site I have set up there (assuming of course I have Apache or another wb server installed)? And then I could configure things like FTP, SMTP and what not to get a server going? And does your server need to be turned on for the dydns thing to work?

---

### Post by armandh on 2007-09-11
my understanding is yes it must be on to report any change in the IP address to dyndns but why would anyone leave it off?
off it matters not if the IP is current with the URL.

---

### Post by CaptainInsaneO on 2007-09-11
At my work we use DNS on Windows, so I can't really speak for Linux or whatever that company is offering, but in my experience the machine does have to be on for the DNS records to propagate.

It might be different with this company though. They may just enter in a hostname record and point it at your IP address, which is what I think they probably do.

And yes, if you have a webserver set up on your home computer and it's properly configured to reach the internet, and you've asked your ISP for a second IP address, there is no reason at all why you shouldn't be able to do this. As I said before, I'm doing this myself on my own computer, the only difference is I'm using one IP address for everything.

Hope this helps and didn't confuse! ](*,)

---

### Post by tgalati4 on 2007-09-11
dyndns.com works well.  Most modern routers have a built-in dyndns updater.  There is also ddclient. If you do nothing, you will get an email every 35 days telling you that your address will expire unless you update it manually or upgrade to a paid service.

This server uses dyndns.com:

wofmusic.homelinux.org:9000

---

### Post by drndrw on 2007-09-11
Ah, okay. So but if I was to do the other thing, it would be a subnet IP. What is this as opposed to a regular IP address?

---

