---
title: "Internet speed drops when using bittorrent"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by dag0 on 2007-04-20
When I downloads more than 1 torrent my speed drops to 0. 
I have tried Azureus and now I'm using Deluge.
I have set up my portforwarding in the router, have good speed from ISP. The torrents don't have to have fast downloads (kb/s) they can have 5 kb/s each and still conection speed drops. Can't open websites(using Firefox) and also slow using samba connection to desktop computer.

I have no clue what to do to make my speed normal..


Thanks

Dag

---

### Post by disabled_20220313 on 2007-04-20
I think you have a wider networking problem rather than just bittorrent. 

You may have more luck searching for solutions to a slow network. Sorry I can't be much more help.

Good luck.

---

### Post by Mizled on 2007-04-20
You may also want to check and make sure it's not maxing out your upload speed. You need to find out what your max upload speed is and throttle it back. If your maxing out your upload speeds it will bottleneck your download speeds and kill your connection. I would suggest setting your max upload speed to less than 85% and see if that works.

---

### Post by Joseaa on 2007-04-20
Bit-torrent clients like utorrent has the feature to specify the number of incoming and outgoing connection. The default value for this is very large and it not needed at all. Moreover, a large number of open connections can truncate the available bandwidth for other application.

---

### Post by dag0 on 2007-04-21
Think I found the problem here. I can use bittornado without problems with great speed. When I use Azureus it stops. Dont find web pages and so on...

I think my broadband router (Zyxel Prestige 334) is to blame here. I have config the sua/nat and when I check the log I get this: [COLOR="Red"]exceeds the max. number of session per host![/COLOR]

I also did config the 334 to allow 1024 sessions thru the router too. And still the same problem.

Think the router is to blame here and I'll go for an another router :-)


Thanks for help all you people


Best Regards
Dag

---

### Post by Brynn on 2007-05-01
I'm not sure if this is a relatively new problem, it's only been since i upgraded to 7.04 that this has happened to me. There are a few other posts saying the same in other forums that I've read

---

### Post by Haegin on 2007-08-27
Nevermind - I'm stupid

---

### Post by Hallvor on 2007-08-27
Try: 

-logging in to your router and see if there is an option to drop idle TCP/UDP connections. Reduce to some 300 ms. This will allow a bad router to function better, if the router has the option at all.

-reduce the upload speed to 70-85% of your *real* upload capacity.

-reduce the number of upload slots.

-reduce the number of allowed connections.

Some clients are "fast" by default, but only because they are extremely aggressive.

---

