---
title: "yahoo audio won't play (company earning calls)"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by braddcadd on 2008-01-20
What do I have to do to get this audio to play on 7.04?  (Acer laptop)  All other sound works fine.

[http://us.rd.yahoo.com/finance/confcall/streetevents/SIG=132h10ce3/*http%3a//web.servicebureau.net/conf/meta?i=1112975339&c=2343&m=was&u=/w_ccbn.xsl&date_ticker=CYT](http://us.rd.yahoo.com/finance/confcall/streetevents/SIG=132h10ce3/*http%3a//web.servicebureau.net/conf/meta?i=1112975339&c=2343&m=was&u=/w_ccbn.xsl&date_ticker=CYT)

OR

[http://biz.yahoo.com/cc/3/85453.html](http://biz.yahoo.com/cc/3/85453.html)
then click on the link

thanks

---

### Post by Hospadar on 2008-01-20
It looks like realplayer audio, you can get the linux version of realplayer from real's website and that should do you.

---

### Post by braddcadd on 2008-01-21
Thanks for the help.  I installed realplayer for linux but still no dice.  The troubleshooting section is here:

[https://player.helixcommunity.org/2005/help/playerfaq.html#mozilla_plugin](https://player.helixcommunity.org/2005/help/playerfaq.html#mozilla_plugin)

It says that the browser and plugin need to be built with he same version of gcc, which mine are not (plugin built with 3.2.0, browser with 4.2).  Any ideas what to do next?  Should I build one or the other from source?  If so, any guidelines would be welcome.

Thanks.

---

### Post by braddcadd on 2008-01-26
I installed it this time from the Ubuntu Repository.  Still no luck.  Any ideas?

---

### Post by wormser on 2008-06-20
Did you ever get this solved?  I am having the same issue.  Audio works fine every where else like with youtube and my music.

UPDATE:  [SOLUTION FOUND]("http://ubuntuforums.org/showthread.php?t=204022&highlight=flash+sound")

# Flash also looks for /usr/lib/libesd.so.1
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

# Flash expects /tmp/.esd/socket to exist.
```
sudo mkdir -p /tmp/.esd/
```
```
sudo touch /tmp/.esd/socket
```

---

