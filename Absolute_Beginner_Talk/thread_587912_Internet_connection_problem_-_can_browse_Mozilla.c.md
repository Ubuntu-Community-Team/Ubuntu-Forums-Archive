---
title: "Internet connection problem - can browse Mozilla.com but nothing else"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by nuttyphilt on 2007-10-23
Hi,

Thought I'd give Ubuntu a go (getting fed up with Windows!) and the install went fairly smoothly, I now have a dual booting Windows/Ubuntu (7.04) setup.

Big problem though...  I don't seem to have any internet connectivity using Ubuntu. 

Points:
I can connect wirelessly and via a wire, i.e. Ubuntu tells me I'm connected succesfully
In Firefox I can click on the 'Getting Started' bookmark which takes me to mozilla.com.  This is fine and I can browse around here without any problems.  If I try anywhere else, i.e. news.bbc.co.uk, [www.google.com](www.google.com) then firefox hangs. i.e in the status bar it says 'Waiting for [www.google.com](www.google.com)...'
If I ping [www.google.com](www.google.com) then all looks fine
Gaim also cannot connect
I've deleted my router as a DNS server and added the opendns servers
I've disable the ipv6 thing in Firefox (although it seems a wider issue than just Firefox)

Not sure what else to try!  It's worth noting I had some similar weird issues using Vista and after some googling found the following command: netsh int tcp set global autotuninglevel=disabled .  Not exactly sure what it did but this fixed all my Vista issues.

Help would be appreciated....  I really want my Linux adventure to work out...  :)

---

### Post by realvz on 2007-10-23
try using opendns

[B]OpenDNS | Providing A Safer And Faster Internet 
OpenDNS is a better DNS service. We make your Internet safer, faster, smarter and more reliable. It's free, and there's nothing to download.
[www.opendns.com/](www.opendns.com/) [/B]

---

### Post by TinMachine on 2007-10-23
try installing konqueror or something? Does the internet work in any applications other than the web browser?

---

### Post by nuttyphilt on 2007-10-23
Tried Opendns - no joy.

Nope, no other applications seem to work.  Tried Evolution to retrieve my pop mail and it hangs on send/receive.  Tried Gaim for MSN messaging and hangs on 'connecting'.  If I add/remove programs and try and update the files, it hangs on 'downloading package information'

---

### Post by hyper_ch on 2007-10-23
turn ipv6 off.

---

### Post by nuttyphilt on 2007-10-23
Done that in Firefox.  

Is there a system wide setting?

---

### Post by realvz on 2007-10-23
what do u get when you click the link below?
[http://72.14.207.99/](http://72.14.207.99/)

---

### Post by hyper_ch on 2007-10-23
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

---

### Post by nuttyphilt on 2007-10-23
> **realvz said:**
> what do u get when you click the link below?
[http://72.14.207.99/](http://72.14.207.99/)

Waiting for 72.14.207.99...

> **hyper_ch said:**
> [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

Done this and confirmed that ipv6 is not enabled - still not working.

This is frustrating.....:mad:

---

### Post by realvz on 2007-10-23
do you have any addons...??

can you try opera browser?

---

### Post by nuttyphilt on 2007-10-23
> **realvz said:**
> do you have any addons...??

can you try opera browser?

It's a clean Ubuntu install so I've done absolutely nothing to it.  Surely there's no point trying Opera because I've already proved that other applications can't connect either??

---

### Post by realvz on 2007-10-23
and it used to work in feisty?

---

### Post by nuttyphilt on 2007-10-23
> **realvz said:**
> and it used to work in feisty?

I've installed 7.04. 

I've tried the LiveCD of 7.10 and have the same problem.

---

### Post by nuttyphilt on 2007-10-23
Fixed it, finally!

It turns out there was a new firmware available for my router - I applied it and now all is good.

For information, the router is a Thomson Speedtouch 716 from Be There broadband.  The firmware is available on the Be There support pages.

Thanks for all the help.

---

