---
title: "deb files download forbidden"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by sergiodlc on 2007-10-03
The network admins forbid .deb files through proxy. Is there a way to bypass this restriction and download the files (let's say to download a renamed version or something)?

Is there a way to request .deb files by email and get it send automatically?

Regards,

Sergio

---

### Post by rsambuca on 2007-10-03
Do you mean the network administrators where you work?  If so, they have restricted this for a reason - so regular users don't mess around with installing programs.

---

### Post by ryanVickers on 2007-10-03
Wow, that's a good sign - they must know Linux is in the building! :p

Sooner or later, those adds that look like an xp window moving around saying "you win!" is going to have an *Ubuntu* border to fool the **majority** once more!...: )

---

### Post by sergiodlc on 2007-10-03
Yes, network administrators at work. The problem is that I'm the only one here using Ubuntu and they are afraid of .deb file sizes (kinda slow internet connection) even though I assured them that they are mostly short sized files.

Please, help me.

Sergio

---

### Post by Jive Turkey on 2007-10-03
In no particular order, #3 should be your first choice though.

1. bring them from home on removable media.  copy the urls output when trying to DL them at work to a text file to use at home. 
2. obfuscate your traffic somehow
3. talk to your admins to get at least a temporary reprive, say its for critical security updates, they wouldn't block those from MS would they?

---

### Post by sergiodlc on 2007-10-03
Thanks:

1. I have no internet connection at home.
2. Perfect, How do I do it?
3. Already tried that and failed

---

### Post by sergiodlc on 2007-10-04
I have no solution yet. Please, help me.

Sergio

---

### Post by rsambuca on 2007-10-04
What specific packages do you want to download?

---

### Post by SpiritIsReality on 2007-10-04
howdy
just wanted to suggest that there's internet access at the nearest library?
would that work? or hotspot if you can roam. ...where the buffalo roam....
buds
[http://www.google.ca/search?hl=en&q=linux+%22introducing+linux+*+workplace%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+%22introducing+linux+*+workplace%22&btnG=Google+Search&meta=)
see 2.2. Installing Packages (With Internet access on another computer) here:[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
but how would the security updates be kept track of and updated? ask and ..[http://ubuntuforums.org/showthread.php?t=567525](http://ubuntuforums.org/showthread.php?t=567525) check out post #2.
I've never been to your stompin' grounds so I don't know where to get internet access there.

rsambuca ...please excuse me for interrupting.

---

### Post by nowshining on 2007-10-04
you could find an online proxy server - [http://www.zend2.com/](http://www.zend2.com/)

---

### Post by SpiritIsReality on 2007-10-04
howdy
nowshining ...have you seen/heard this [http://ubuntuforums.org/showthread.php?t=566861](http://ubuntuforums.org/showthread.php?t=566861)
heading ...Ubuntu makes NY Times
and just how would a proxy work? I know, read ..
buds

---

### Post by nowshining on 2007-10-04
well just input the url and browse just as u normally do and that site keeps the url address box at top and u can uncheck and check allow cookies, etc.. the cookies will be stored under the sites name however the home page or so lets you delete the cookies.. 

Again that's an online proxy or web proxy that lets you do that kind of stuff - other proxies just allow you to change the ip with an extranal program or you can go thru one via changing network settings or use use a  proxy in IE, which then just uses the ip of the other computer - somewhere in the world, and which one u chose. I'm not good at explaining them, so you'll have to look it up urself  :)

In other words every site you visit goes thru thru computers/servers, I don't know if just changing the ip will work  so I suggested an online one which will bypass anything, esp. the hosts file :) i use a hosts file myself and block a TON of sites that are bad, ads, etc.. :) that bypasses it..

I'm going to stop rambling now....

and no I didn't hear. thanks for the link tho.

---

### Post by macogw on 2007-10-05
> **nowshining said:**
> well just input the url and browse just as u normally do and that site keeps the url address box at top and u can uncheck and check allow cookies, etc.. the cookies will be stored under the sites name however the home page or so lets you delete the cookies.. 

Again that's an online proxy or web proxy that lets you do that kind of stuff - other proxies just allow you to change the ip with an extranal program or you can go thru one via changing network settings or use use a  proxy in IE, which then just uses the ip of the other computer - somewhere in the world, and which one u chose. I'm not good at explaining them, so you'll have to look it up urself  :)

In other words every site you visit goes thru thru computers/servers, I don't know if just changing the ip will work  so I suggested an online one which will bypass anything, esp. the hosts file :) i use a hosts file myself and block a TON of sites that are bad, ads, etc.. :) that bypasses it..

I'm going to stop rambling now....

and no I didn't hear. thanks for the link tho.
It's not that archive.ubuntu.com is blocked, though, so I highly doubt a proxy would do anything.  It'd still stop files with a .deb file extension.

---

### Post by nowshining on 2007-10-05
maybe or maybe not, it should bypass those restrictions :) but how would one block a .deb file, if you know how, let us/me know so we/me can learn how it's done or link us/me.

---

### Post by SpiritIsReality on 2007-10-05
howdy
went looking for a beginner's blocking downloads
[http://www.google.ca/search?hl=en&q=linux+%22blocking+downloads%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=linux+%22blocking+downloads%22&btnG=Search&meta=)
find in this page, blocking downloads
[http://www.usatoday.com/tech/products/software/2007-02-19-cuba-linux_x.htm](http://www.usatoday.com/tech/products/software/2007-02-19-cuba-linux_x.htm)
I know it doesn't solve the problem, but thought it was interesting.
buds

---

### Post by nowshining on 2007-10-05
google sucks on using quotes, i suggest clusty.com for that. :)

---

### Post by bobbocanfly on 2007-10-05
Could you not just get someone here to make a Rar or Tar archive of the debs you want and download that. Assuming your netadmins dont block them you should be fine.

---

### Post by ryanVickers on 2007-10-05
> **macogw said:**
> It's not that archive.ubuntu.com is blocked, though, so I highly doubt a proxy would do anything.  It'd still stop files with a .deb file extension.

Hm, whenever I have to sneak a **safe** file past the gmail "virus scanner"* (that's called .exe), I just rename it .abc and then tell people to rename it and it works!  Could you not do this somehow...?

*That's the one problem with gmail - and it doesn't even actually work!  It doesn't actually scan for viruses, it just blocks all executables :p

---

### Post by nowshining on 2007-10-07
> **ryanVickers said:**
> Hm, whenever I have to sneak a **safe** file past the gmail "virus scanner"* (that's called .exe), I just rename it .abc and then tell people to rename it and it works!  Could you not do this somehow...?

*That's the one problem with gmail - and it doesn't even actually work!  It doesn't actually scan for viruses, it just blocks all executables :p


oooh lolz kool thanks for that info. ::P

---

### Post by SpiritIsReality on 2007-10-07
> **bobbocanfly said:**
> Could you not just get someone here to make a Rar or Tar archive of the debs you want and download that. Assuming your netadmins dont block them you should be fine.
man the first few words of your post and I thought I was in trouble for something, and then a few words further, ... wow this is great !!!
buds

---

