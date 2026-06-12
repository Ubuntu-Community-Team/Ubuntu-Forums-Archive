---
title: "Firefox 1.5 just too slow"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by jan on 2006-05-25
Hi folks,

my patience goes slowly away... Firefox is simly too slow for my browsing needs - i usualy have more windows opened with even more tabs each - and here we go, the switching between tabs and windows takes sometimes up to 2 seconds before the other tab/window is viewed...

I've been wanting to avoid installing Opera, Swiftfox etc. but now it seems this will be a must. I wanted to avoid it since i hate manual installs...

I upgraded from Breezy to Dapper because of 1.5 FF but it is not as fast as i need.

Any advices???

---

### Post by frodon on 2006-05-26
Install the fastest web brother ever seen : epiphany
```
sudo apt-get install epiphany
```
It's the gnome web browser, everybody here will confirm that epiphany is faster than firefox, swiftfox, opera and mozilla, i'm stuck with epiphany because of that.

---

### Post by Sef on 2006-05-26
Do it this way:

sudo apt-get update

sudo aptitude install epiphany-browser epiphany-extensions

After install, the extensions will be under Tools.

And yes, it is fast.

---

### Post by KarmaKing on 2006-05-26
[QUOTE=Sef]Do it this way:

sudo apt-get update

sudo aptitude install epiphany-browser epiphany-extensions

After install, the extensions will be under Tools.

And yes, it is fast.[/QUOTE]


Hello Sef, all

if one install epiphany (cool name) then will it install itself as the default browser?  Or will one have to edit a config file?

I love FF and its extensions but it is slow at times, but am willing to try.  however, I don't want to go through the time consuming process of finding and installing all my extensions over again.
I would just like to try it.

thanks

KK

---

### Post by bruce89 on 2006-05-26
[QUOTE=KarmaKing]Hello Sef, all

if one install epiphany (cool name) then will it install itself as the default browser?  Or will one have to edit a config file?

I love FF and its extensions but it is slow at times, but am willing to try.  however, I don't want to go through the time consuming process of finding and installing all my extensions over again.
I would just like to try it.

thanks

KK[/QUOTE]
Epiphany doesn't support firefox extentions, but it has adblock and greasemonkey.  To set it as default, goto System/Preferences/Preferred Applications.

---

### Post by mynimal on 2006-05-26
I don't think it sets itsself as default, but you can easily by going to System -> Preferences -> Preferred Applications. :)

---

### Post by Sef on 2006-05-26
> I don't think it sets itsself as default, but you can easily by going to System -> Preferences -> Preferred Applications. 

That is correct. That's how I set epiphany as my default browser.

---

### Post by PhilOSparta on 2006-05-26
I currently use FF on this AMD 64 box and I had to install a special 32 bit version and go through hoops to get flash and some other extensions to work.

If I convert over to Epiphany will flash work on 64 bit machine, or should I forget it for now and wait until 64 bit is more widely used?

---

### Post by Sef on 2006-05-26
The backend is the same for Epiphany and Firefox.  Have you tried [RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats") for the flash?

---

### Post by dmizer on 2006-05-26
i would suggest epiphany too, but it crashes on me all the time.  firefox is plenty fast enough for me.  opera's awesome, and i don't remember jumping through hoops to get it to install.  i've been playing with it for a while to see if i can make mplayer the default video player for it.  but i really haven't put alot of effort into it because firefox's adblock is WAY superior to either epiphany or opera.

could be other things hoging resources and making it appear that firefox is slower than it really is.

---

### Post by Sef on 2006-05-26
> i would suggest epiphany too, but it crashes on me all the time.

I wonder why it does that to you.  It is very rare it happens to me.

---

### Post by sherlock-holmes on 2006-05-26
OR:

type about:config 
in FF and scroll down and do these

set: 

```
network.dns.disableIPV6 ---> double click to set it "true"
network.http.pipelining ----> true
network.http.pipelining.maxrequests ----> around 25-30
network.http.proxy.pipelining ----> true
```

and restart FF...

and feel the speed...hope this helps...

---

### Post by Sef on 2006-05-26
> network.dns.disableIPV6 ---> double click to set it "true"
network.http.pipelining ----> true
network.http.pipelining.maxrequests ----> around 25-30
network.http.proxy.pipelining ----> true

Works for epiphany too.

**Warning:** To do the above with any browser, you must have cable, dsl, or other fast internet service.  If you have dial up, don't do it.

---

### Post by pshnfry on 2006-05-26
Beautiful.  Restarted and change noticed immediately.

Thank you.

---

### Post by 3rdalbum on 2006-05-26
Thanks sef, this actually solved my problem with Firefox on Ubuntu after going over my download limit! (I had turned on the speed modifications without realising that it would hurt performance in low bandwidth)

---

### Post by dmizer on 2006-05-26
i had a site deny me entry for those modifications.  just fyi.  no idea where that site was though ... mighta been a bank of mine.

but i tell you what ... i'm glad i turned off ipv6 in firefox.  had it disabled system side, but not in my browser.  huge difference now.  didn't add the pipelining, but turning off ipv6 was heaven sent.

no idea why epiphany crashes on me.  but it rarely lasts more than 10 minutes straight before blowing it's top.  nautilus does it occasionally too.  and i can't keep gedit open for the life of me.

but she's way more stable now than when i started.

---

### Post by jan on 2006-05-26
Hi folks,

of course i run Fasterfox and the FF speed-up tweaks but that cant make the browser rocket of course... :mrgreen: :mrgreen: :mrgreen: 

Hm, I have both Epiphany and Galeon installed but I did not experience a great speed-up with them... so i wanted to ask whats around. It seems like i give them one more try (transfering bookmarks sucks though) or hit Opera in the and. I will see.

---

### Post by jan on 2006-06-01
Ok folks,

so i moved over to Epiphany's, transfering my basic bookmarks and it seems to be faster than FF 1.5. I think it uses Gecko 1.8.

---

