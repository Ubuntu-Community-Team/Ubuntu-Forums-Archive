---
title: "Frustrated with web surfing..."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by unmitgatedaudacity on 2007-07-21
Okay, first, let me say that this forum's architecture is really impressive.  I've never had a forum suggest threads to read based on my subject.  I have a feeling using Linux will be very much like that:  a constant flow of serendipity.

But first, I have to solve a problem.  I am having a lot of difficulty surfing some of my favored web pages.  For instance, when I navigate to the login page for My Yahoo! it times out.  I tried to make a purchase on Newegg, and it wouldn't let me through to the page where I'd finish the transaction.

(I have a sense that those two examples will reveal a lot about the problem, but try as I may I can't find the answer...)

I've done my homework here, I promise.  I believe I've managed to install Flash and Java properly.  I've tried to find other posts, and what I'm concluding is that I may have done something wrong.

Do you have any idea where it was that I screwed up?

Many thanks,

unmitigatedaudacity

---

### Post by DBStevens on 2007-07-21
What browser?   What specific pages, urls very helpful in this.

---

### Post by unmitgatedaudacity on 2007-07-21
Ah.  I'm using Firefox 2.0.0.4 and Swiftfox 2.0.0.4, and the Yahoo page that won't pop is [http://us.rd.yahoo.com/my/login/drawbridge/signin/*http://login.yahoo.com/config/login?.page=p1&.partner=&.intl=us&.src=my&.done=http://my.yahoo.com](http://us.rd.yahoo.com/my/login/drawbridge/signin/*http://login.yahoo.com/config/login?.page=p1&.partner=&.intl=us&.src=my&.done=http://my.yahoo.com).

The item i as buying on Newegg got sold.  Damn it all.

I'm also oddly unable to send or receive email through either Thunderbird or Evolution mail, so I suspect the problem lies outside of the browsers in some system settings.

Thx,

ua

---

### Post by unmitgatedaudacity on 2007-07-21
Also unable to load [http://en-US.add-ons.mozilla.com/en-US/firefox/2.0.0.4/extensions/](http://en-US.add-ons.mozilla.com/en-US/firefox/2.0.0.4/extensions/), which is the basic Firefox add-ons page, and I can't load [https://en-US.add-ons.mozilla.com/en-US/firefox/2.0.0.4/search-engines/](https://en-US.add-ons.mozilla.com/en-US/firefox/2.0.0.4/search-engines/)

Security settings too high?

Thx,

ua

---

### Post by testube_babies on 2007-07-21
I've had timeout issues while ipv6 is enabled; you could try disabling it:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

...Although I think your problem may go deeper than this.

---

### Post by DBStevens on 2007-07-21
unmitigatedaudacity,

Did you notice that every single page you are having trouble with is SSL.

Talk to me about what you have in edit >> preferences >>  advanced >> encryption tab

---

### Post by unmitgatedaudacity on 2007-07-21
I sense a revelation is imminent...

"Use SSL 3.0" is checked.

"Use TLS 1.0" is checked.

When a web site requires a certificate, I'm set to select one automatically.

I'm not using OCSP for certificate validation.

I can go into security devices if you need me to.  What do you make if it so far?

---

### Post by DBStevens on 2007-07-21
security.OCSP.enabled is at its default setting of 0 on my system and the others are as you have them ...

---

### Post by DBStevens on 2007-07-21
You haven't by any chance blocked outbound port 443 traffic via a firewall rule set have you?

And is the ca-certificates package installed?

---

### Post by pyros on 2007-07-21
Sort of a shot in the dark, but try running these commands:
```

dpkg-reconfigure libssl0.9.8
dpkg-reconfigure openssl
dpkg-reconfigure libxmlsec1-openssl
dpkg-reconfigure ssl-cert

```

---

