---
title: "Speed Tweak Doesn't Work in Feisty"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by milkolate on 2007-07-03
[http://thewebsbest.net/index.php?option=com_content&task=view&id=121&Itemid=30](http://thewebsbest.net/index.php?option=com_content&task=view&id=121&Itemid=30)

The tips in that site doesnt work since my /etc/sysctl.conf is different from what is referred there

---

### Post by moore.bryan on 2007-07-03
[I]if you have feisty, the /etc/sysctl.conf file is fairly empty.  i've added the following for both swappiness and network speed-up:
```

vm.swappiness=10
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

```
for the /etc/inittab file, since edgy ubuntu has used upstart instead.  all that really means for you is that instead of one file for you to comment things out, you have to go into more; namely, edit the /etc/event.d/tty# files.  [here's]("http://blog.mypapit.net/2007/03/where-can-i-find-inittab-in-ubuntu-edgy-eft-or-feisty-fawn.html") some more info on upstart...
[/I]

---

### Post by milkolate on 2007-07-03
So I'll just paste that whole code into the sysctl.conf?

---

### Post by moore.bryan on 2007-07-03
*yup... worked for me and really speeded-up my network.*

---

### Post by crimesaucer on 2007-07-03
I like a lot of the tips from tips guide: [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)

---

### Post by milkolate on 2007-07-03
crimesaucer, which of thsoe work for Feisty?

---

### Post by crimesaucer on 2007-07-04
I think most are good for Feisty, but I'm not an expert....I researched a lot of pages that are new, and they are are all basically the same settings, this list was just written very well.

For me, I did these in my Feisty: 


1.) Swappiness (but then I changed it back to default because I only have 512MB of RAM...the reason why is that if I had a few GIMP's open on different workspaces, and a few other apps open, it got slow...but when just using Firefox, it goes really fast with vm.swappiness=5 or 0)


2.) Removing unused tty's (I only need one tty to fix my system...)


3.) Removing junk files (I use sudo apt-get autoclean and sudo apt-get clean every now and then)


4.) Redistributing RAM usage  (I did this one, and also was told to add the echo 1000 line from post #8, here: [http://ubuntuforums.org/showthread.php?t=443515&highlight=Thunar+root](http://ubuntuforums.org/showthread.php?t=443515&highlight=Thunar+root) ) 

"These tweaks goes in /etc/rc.local->":

echo 1000 > /proc/sys/dev/rtc/max-user-freq &
echo "base=0x98000000 size=0x8000000 type=write-combining" >| /proc/mtrr &


5.) Starting services in concurrency mode (seemed to help, but if I used sysv-rc-conf to turn off bluetooth it might work better...I just was a little lazy)


6.) IPV6  (really helped...)


7.) Firefox ( I used a few of these, but I prefer the list from these links below. The first page is old, but it explains a few things that are still current, I used it as a guide for the new settings:

[http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)

... this next page is the current page that the first page will link you to:

[http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)

... I used this next page to learn more about different settings that were recommended from various guides:

[http://kb.mozillazine.org/Category:Preferences](http://kb.mozillazine.org/Category:Preferences)

... and page 2 of the same list:

[http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Mail.db+timestamp+leeway](http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Mail.db+timestamp+leeway)

... and another list of about:config settings:

[http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)

and after all of that, I recommend using Swiftweasel for the fastest browser:

[http://swiftweasel.sourceforge.net/about.php](http://swiftweasel.sourceforge.net/about.php) 

......after doing a bit of work, my browser is very fast)


8.) Checking /etc/resolv.conf  (I changed to OpenDNS and like it so far)


9.) /etc/hosts  (I changed this too)


10.) Checking /etc/syctl.conf  (I also did this and have seen it on every guide for a speed tip)


11.) Concluding...  (and I have edited my grub menu with "profile")


I have thought about "Removing unnecessary services" and "Prelinking" but I haven't done it yet. 

As for "Removing unnecessary services", I have read that it was for older versions, but I still might turn off Bluetooth and some other things that I don't need, just to see if it works faster durring boot up....and as for "Prelinking", I am happy with the way my computer feels now, so I won't mess with that...and as for all of the other ones that I left off, I figured that I didn't need them on my laptop.


I hope this helps...and I do recommend doing your homework for the the "about:config" settings, and also using Swiftweasel that's optimized for your processor.



ALSO, I read somewhere that default vm.swappiness is already 60, so I don't even have that in my sysctl.conf, but you could always add "vm.swappiness=5" to lower it if you never use your swap file...I need my swap, even though I only use between 1% to about 9%...and if I open a page that uses a lot of memory (like this cool photo of NYC: [http://www.harlem-13-gigapixels.com/](http://www.harlem-13-gigapixels.com/) ), then I have enough swap memory.

```


net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

```

---

### Post by CrankyFilipino on 2007-07-04
Wow.. I'm sure these tips are really great.. I just wish I understood what half of them meant lol

---

### Post by milkolate on 2007-07-05
Thanks **crimesaucer**... will try those later..

**CrankyFilipino**, taga saan ka?

---

### Post by CrankyFilipino on 2007-07-05
> **milkolate said:**
> Thanks **crimesaucer**... will try those later..

**CrankyFilipino**, taga saan ka?

I'm in california.. but me and my wife are moving back to washington soon.. ikaw?

---

