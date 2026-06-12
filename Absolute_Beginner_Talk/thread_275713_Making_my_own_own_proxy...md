---
title: "Making my own own proxy.."
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by makko on 2006-10-11
HI Guys,

Hi,

I want to make my own private proxy as in.. I type [www.myaddress.com](www.myaddress.com) into a web browser then up comes a text box then I type in [www.mychosenurl.com](www.mychosenurl.com) and it gives me that page under my URL.
Similar to [www.shysurfer.com](www.shysurfer.com) and [www.hidemyass.com](www.hidemyass.com)

I am thinking of setting up squid on my server. Will squid do this for me?? Also, I wouldnt mind getting my hands on a guide or two for this subject..

Thanks,

Makko

---

### Post by skymt on 2006-10-11
A little Googling came up with [this](http://www.jmarshall.com/tools/cgiproxy/) (EDIT: CGIProxy). It doesn't use Squid. Instead, it goes through Apache and Perl. It's probably your best bet if you want something like the sites you mentioned.

---

### Post by makko on 2006-10-11
Ha, thanks skymt.. I actually found that site straight after I started this thread..I will look into it.. How would I go about setting it up with apache and Perl? I know nothing about Perl

---

### Post by skymt on 2006-10-11
Well, obviously the first step is to install apache2. It's in the package called "apache2" (sudo aptitude install apache2). ;) 

Perl should already be installed, and Apache has a very good default configuration, so the next step is to download CGIProxy and put it in "/var/www/cgi-bin". You'll need to change the first line of nph-proxy.cgi (the name of the CGIProxy file). to:```
#!/usr/bin/perl
```

I think that's it. I may have missed something, I haven't worked with CGI in a long time. [Test it](http://localhost/cgi-bin/nph-proxy.cgi) (link will be dead until everything's installed), and post if you have problems.

EDIT: I assume you don't want just anyone to use your proxy. If that's the case, read [this](http://httpd.apache.org/docs/2.2/howto/auth.html), and post if you have any questions.

---

### Post by Quintin Riis on 2006-10-11
What are you wanting to use this for?

If it is to evade some kind of content-filtering it will most likely be unsuccessful unless you run it over SSL / TLS.

I would use squid.  Best solution, in my opinion.

There are also things like "CGIProxy" that you can use with apache.  Again, you'd want to run it over an encrypted connection.

---

### Post by skymt on 2006-10-11
> **Quintin Riis said:**
> What are you wanting to use this for?

If it is to evade some kind of content-filtering it will most likely be unsuccessful unless you run it over SSL / TLS.

I would use squid.  Best solution, in my opinion.

There are also things like "CGIProxy" that you can use with apache.  Again, you'd want to run it over an encrypted connection.

I already suggested using CGIProxy, as discussed in posts 2-4.

I didn't suggest using squid, because I assumed this might be used in a situation where the browser HTTP proxy settings aren't configurable (like in a locked-down school computer lab). Plus, the OP mentioned a couple of sites that use web-based proxies.

Using SSL is a good idea though. If you want it, install apache2-common and read [this](http://httpd.apache.org/docs/2.2/ssl/). As always, post back if you have problems/questions!

---

### Post by Quintin Riis on 2006-10-11
> **skymt said:**
> I already suggested using CGIProxy, as discussed in posts 2-4.To quote you, you suggest using 'this'.  I can't follow every link in a thread. :)

[Click Here]("http://www.w3.org/QA/Tips/noClickHere").

CGIProxy works fine though, yea.  There is also a PHP proxy, but last time I looked it broke if you ran it on php5.  The load of the php one was also pretty nasty.

---

### Post by skymt on 2006-10-11
> **Quintin Riis said:**
> To quote you, you suggest using 'this'.  I can't follow every link in a thread. :)

[Click Here]("http://www.w3.org/QA/Tips/noClickHere").

Yeah, bad habit, I know. :oops: 

I mentioned it by name in a later post though. And you could have moused over the link, which would tell you that it goes to cgiproxy.

Am I being overly defensive? If I am, that's another bad habit. ;)

---

