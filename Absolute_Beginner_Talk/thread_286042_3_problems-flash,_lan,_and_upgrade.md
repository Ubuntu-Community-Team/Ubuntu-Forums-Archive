---
title: "3 problems-flash, lan, and upgrade"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by NotNutts on 2006-10-27
Hello all;
I installed Ubuntu the other day (of course 2 days later the upgrade is released ](*,) ) and have been having a few problems.

First, I installed flash with automatix, but when my kids go to disney.com, it says I need an upgraded flash.  I even tried downloading and installing-still no worky.

Second, when I go to the network, the shared folders on my other computer don't show up.  Internet works, so the lan connection works--what gives?

Lastly, I thought upgrading to edgy might fix my problems.  I alt-f2'd, entered the update -c command, clicked the button to update, and it errored out, saying "failed to fetch http://packages.freecotrib.org...etc"  Are the servers overloaded, maybe?

Thanks in advance

---

### Post by NotNutts on 2006-10-28
bump...

---

### Post by lazyart on 2006-10-28
If you take a look around the boards you'll see Edgy has it's issues.  Dapper was released with 18 months of ongoing support, so you might want to stay where you are.

As for Flash-- Flash 7 is what you downloaded with automatix.  However Flash 8 is the current release... and that release isn't available for Linux.  So yes you have Flash-- the newest available for this OS.  You can try out Flash 9 beta (check adobe's site), but again, it is beta, so your mileage may vary.

As for network-- can other computers see the shares?  Can you see Windows Network?

I think the general rule is 24 hours before bumping.  I know it's frustrating, and with so many new threads things get lost quickly.  Just a friendly notice, that's all. :)

Hope this helps.

---

### Post by NotNutts on 2006-10-31
Sorry for the fast bump--I gues I should have read the FAQs closer.  

Anyways, I've solved all the problems save one by doing a clean install of EDGY.  I tried MEPIS and Freespire, but I like UBUNTU best.  The only problem I have left is not seing the othe computer on the lan.  This happened after installing Dansguardian using a script from whatwouldjesusdownload.com  I already posted it the ubuntu CE forum, so I don't want to crosspost--just let you know my status.  Thanks!

---

### Post by David Corrales on 2006-10-31
Do you have samba installed? If you're using a firewall, it'll block shared folders for sure unless you poke a hole for them in -both- PC's.

---

### Post by NotNutts on 2006-10-31
> **David Corrales said:**
> Do you have samba installed? If you're using a firewall, it'll block shared folders for sure unless you poke a hole for them in -both- PC's.


Yes, I do.  I added 'SERVER SAMBA ACCEPT' in the firehol.conf file.  I can't find a gui to further configure the firewall, and am LINUX-stupid...

---

### Post by rykel on 2006-11-16
> **NotNutts said:**
> First, I installed flash with automatix, but when my kids go to disney.com, it says I need an upgraded flash.  I even tried downloading and installing-still no worky.

Hi,

If you install Flash Player 9 Beta, you can view Disney.com without problems. (see screenshot - my Firefox on Ubuntu Edgy)

To do so, go to:
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

Download, unzip and copy "libflashplayer.so" to your Firefox Plugins folder.

My Plugins folder was found at ~/.mozilla/plugins.

---

