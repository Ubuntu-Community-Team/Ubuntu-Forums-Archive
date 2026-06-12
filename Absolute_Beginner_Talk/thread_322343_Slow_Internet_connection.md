---
title: "Slow Internet connection"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-12-20
Since switching from Windows XP to Ubuntu 6.06 LTS I have noticed that my internet connection has slowed down.  It now takes 5 to 20 seconds to load a new page.  I am running Firefox 2.0.0.1 and have ADSL service.  Any help in getting this up to speed would be appreciated. 

Donnie

---

### Post by bigken on 2006-12-20
give this a shot in the browser bar type about:config the in the filter type ipv6 the just double click on network.dns.disableIPv6 ;)

---

### Post by alienexplorers on 2006-12-20
Have changed the setting for "network.dns.disableIPv6" to true.  Have a bit more speed, but it still seems like it takes forever to load pages in Firefox 2.0.0.1 or GranParadiso 3.0a2.

Tried Swiftfox and it did not like my machine at all.  Crashed all the time.

Donnie

---

### Post by bigken on 2006-12-20
sorry I cant help anymore but im sure if you look around the forum and also try a google search you will find the answer ;)

---

### Post by venik212 on 2006-12-20
I have the very same problem.  Internet speed under Windows XP is fine, but on the same machine (dual-boot) under Ubuntu it is unacceptably slow.
What do I do?

---

### Post by alienexplorers on 2006-12-20
Is there a way to preload Firefox in Ubuntu that would allow it to at least start faster.

Donnie

---

### Post by user007usa on 2006-12-20
> **alienexplorers said:**
> Since switching from Windows XP to Ubuntu 6.06 LTS I have noticed that my internet connection has slowed down.  It now takes 5 to 20 seconds to load a new page.  I am running Firefox 2.0.0.1 and have ADSL service.  Any help in getting this up to speed would be appreciated. 

Donnie

I don't have much to contribute other than to say jsut the opposite.  My "connection" is much faster under Ubuntu.  I have cable though. 

Does it seem like it is the connection, or some sort of software delay?

---

### Post by mykalreborn on 2006-12-20
also you can try fasterfox. it's a firefox plugin meant to make the most of your bandwidth. get it here:[https://addons.mozilla.org/firefox/1269/](https://addons.mozilla.org/firefox/1269/)
i had a dual boot once, but my internet connection was faster in ubuntu. :p
you can allways try formatting your windows partition and make "the step" ;)

---

### Post by venik212 on 2006-12-21
Sadly, none of the responses here solved the problem of*** unacceptably slow internet connection***.  I was told by the network administrator to use DHCP and leave all the configuration to Automatic configuration.  However, I might have to crawl back to WINDOWS if I cannot use the internet.  Any ideas why I am having trouble?  Again, the same hardware is working fine under WINDOWS XP.
I have a 3com NIC, and a LAN running at 100 mb/sec.

---

### Post by Izobalax on 2006-12-21
There is an excellent little code modification you can do to severely increase your internet speed. 

See [here](http://doc.gwos.org/index.php/DisableIPV6) and all shall be revealed unto thee ...

I admit that internet speed when I first installed Ubuntu was slower than in Win XP, but since discovering this things are much zippier. :p

---

### Post by scrooge_74 on 2006-12-21
I had some troubles in the past with my wireless card, it seem to be a litle more slow than another machine sitting right next.  It seems it was my card after all when signal was weak.

As far as browsing I go a lot faster than in 

I will give a try to the script and post back the results after the reboot

EDIT:

You were right, things have improve a lot, now the forum shows up a lot more quicker.  thanks for the info.

Question so when in the more or less distant future IPv6 gets enable we have to change those setting back right?

---

### Post by venik212 on 2006-12-22
I did disable ipv6 and it made no difference whatsoever.  However, I shall try the patch you pointed to and report back.  Since it seems that this problem is not so rare, perhaps this could become the default in the distribution of Ubuntu, or perhaps Ubuntu can support ipv6?

---

### Post by navneeth on 2006-12-22
I had the same problem. After switching to static ip, my internet connection was fast as it was in XP. But now, people tell me that I shouldn't have switched to static if my default was DHCP.

---

### Post by venik212 on 2006-12-22
The system prevented me from changing the aliases file, claiming I did not have permission for it.  I was logged on as the root or super user, as far as I know.  How do I force it to recognize that fact?
Thanks,

---

### Post by scrooge_74 on 2006-12-22
> **venik212 said:**
> The system prevented me from changing the aliases file, claiming I did not have permission for it.  I was logged on as the root or super user, as far as I know.  How do I force it to recognize that fact?
Thanks,

Thats strange did yo type in a command terminal

cd /etc/modprove.d/
sudo nano aliases

Make the changes and that should be it

---

### Post by venik212 on 2006-12-22
No, I did it from the GUI, but after your response I tried it from the terminal command line, and got the same refusal: permission denied.
When I rebooted and tried to log on as root, I was told that the root cannot log in from that screen.  I am confused...

---

### Post by scrooge_74 on 2006-12-22
> **venik212 said:**
> No, I did it from the GUI, but after your response I tried it from the terminal command line, and got the same refusal: permission denied.
When I rebooted and tried to log on as root, I was told that the root cannot log in from that screen.  I am confused...

Ok, from personal experience root should not be use to log into Gnome (security reasons)

In Ubuntu the root user is not active so everything has to be done using sudo, but using the user that first installed the system. Check if you are using the correct user to try to use sudo.  As an example in this PC only I can use sudo, my wife and kids dont have permissions to use it



In Debian also you cannot log into de GUI using root, unless in safe mode and things like that.

---

### Post by venik212 on 2006-12-22
I did it again, and this time it worked perfectly, and it sped up the internet connection.  Thanks so much for your eapert and quick help!  It is much appreciated.

---

### Post by venik212 on 2006-12-26
Well, sad to report that the internet connection is STILL very sluggish.  Disabling ipv6 did help, but from time to time things are just terribly slow.  This does not happen to me in WINDOWS XP on the same machine/connection, so I suspect I have some setting set incorrectly.
Any ideas?

---

### Post by richpor on 2006-12-27
I have the same problem.  I did all the tweaks, installed Swifterfox, and noticed a marked improvement over firefox... It's still slower than firefox on my XP sessions.  I just can't seem to get the same speed as XP.

What I have noticed is that swifterfox ( and firefox for that matter ) seem to want to cache the entire page before beginning to display it where in XP the page is displayed as soon as it starts to load (dunno if that's right, but it seems that way to me).  Could also be a problem with 6.10 resolving host names (which seems quicker in XP as well)

Try swifterfox and see if that helps.  If you know any other tricks, let me know!

---

