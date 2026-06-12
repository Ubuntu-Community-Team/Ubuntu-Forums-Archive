---
title: "100% CPU Usage?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Darko Beta on 2007-02-24
Hey all.  I'm experiencing worse performance on Ubuntu than I did on XP.  Mainly when I'm web surfing, which is most of the time.  Check out the screenie from from the system monitor.  You can see how I keep hitting 100% CPU usage, and this is just from loading web pages and switching tabs in Swiftfox, with Amarok playing in the background (this happens even when Amarok is not playing).  This can be frustrating as surfing is then slow going and hangs up for 5 seconds at a time.

I feel like I should be getting better performance from this setup:
Pentium 4 1.8ghz
1mb RAM
Nvidia 6600gt

Just from reading other people's posts, it sounds like this is a perfectly good setup to be running Ubuntu.  And like I said, XP is very snappy and I don't have this problem (just for comparison's sake--I have no desire to go back to MS).

Any ideas on why this could be happening, and/or suggestions to improve things?  Thanks!

---

### Post by jordanmthomas on 2007-02-24
Do you have smooth scrolling enabled in Swiftfox?
If so, try turning it off and see if you get some better performance

Edit --> preferences --> advanced --> uncheck smooth scrolling.
See if that's any nicer.

---

### Post by Darko Beta on 2007-02-24
Thanks for the advice, jmt.  I checked and I don't have smooth scrolling enabled...

---

### Post by jordanmthomas on 2007-02-24
Do you have nvidia's drivers or the default ones?
(not sure if you even WANT the proprietary drivers but it would help performance)

I'm not sure what else may be wrong.  Firefox has always done the same thing for me:  my solution:  I just use Opera.

Furious scrolling tests (not really scientific)
Opera :  47 % CPU
Firefox : 100 % CPU

Not sure what the deal is, but Opera likes me more.

---

### Post by Darko Beta on 2007-02-24
I installed the nvidia drivers, which did help a certain amount.  You know, I haven't used Opera in a while...  I'll give it a try.

---

### Post by irish_flu on 2007-02-24
Hey Darko-

Nice avatar!

Not that this helps you, but I have similar machine specs and do not experience that.  I'm using Firefox instead of Swiftfox, but that's the only major difference.

---

### Post by jordanmthomas on 2007-02-24
> 1mb RAM
I found the problem!!

Just kidding, I know it was a typo

---

### Post by STREETURCHINE on 2007-02-24
open terminal and type or paste

                                 ```
top
```

it will tell you what is using up the proccessor

---

### Post by foxmulder881 on 2007-02-24
I have the same 100% CPU usage problem too, but with Firefox. I have begun to ignore it because I simply don't know how to fix it.

See my sig for systems specs if you're interested.

---

### Post by Darko Beta on 2007-02-24
Here is the output from the top command twice.  First, when I am not actively using swiftfox and then I captured the output when I have opened a couple of tabs and things are bogging down badly.

```
top - 18:55:52 up 1 day, 12:22,  2 users,  load average: 2.03, 1.62, 1.41
Tasks:  98 total,   3 running,  95 sleeping,   0 stopped,   0 zombie
Cpu(s): 28.5%us,  6.0%sy,  0.0%ni, 60.9%id,  0.0%wa,  2.3%hi,  2.3%si,  0.0%st
Mem:   1034964k total,   997424k used,    37540k free,    32432k buffers
Swap:  3028212k total,     8156k used,  3020056k free,   683600k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
13125 root      15   0 98.4m  62m 9912 R 12.6  6.2  25:27.97 Xorg                                                                                            
16015 bbolende  16   0 45056  15m 9.8m R 12.3  1.6   0:04.98 gnome-terminal                                                                                  
13344 bbolende  15   0  133m  46m  27m S 11.9  4.6  18:45.44 amarokapp                                                                                       
15988 bbolende  15   0  153m  48m  20m S  0.7  4.8   0:26.20 swiftfox-bin                                                                                    
16035 bbolende  15   0  2248 1136  840 R  0.7  0.1   0:00.11 top                                                                                             
13337 bbolende  15   0 15460 4480 3448 S  0.3  0.4   0:05.31 gnome-screensav                                                                                 
    1 root      16   0  1628  536  448 S  0.0  0.1   0:01.27 init                                                                                            
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    3 root      34  19     0    0    0 S  0.0  0.0   0:03.76 ksoftirqd/0                                                                                     
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.18 events/0                                                                                        
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                                                         
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                                                         
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 kblockd/0                                                                                       
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
   96 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod                                                                                         
  129 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
  130 root      15   0     0    0    0 S  0.0  0.0   0:00.26 pdflush                                                                                         
  131 root      15   0     0    0    0 S  0.0  0.0   0:00.43 kswapd0                                                                                         
  132 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1723 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 1803 root      10  -5     0    0    0 S  0.0  0.0   0:00.76 kjournald                                                                                       
 1876 root      15   0  1600  548  468 S  0.0  0.1   0:00.03 logd                                                                                            
 2021 root      13  -4  2612 1052  360 S  0.0  0.1   0:00.53 udevd                                                                                           
 2771 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 shpchpd                                                                                         
 2805 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                       
 2931 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                       
 2932 root      10  -5     0    0    0 S  0.0  0.0   0:00.27 usb-storage                                                                                     
 2934 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                       
 2935 root      10  -5     0    0    0 S  0.0  0.0   0:02.83 usb-storage                                                                                     
 2937 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                       
 2938 root      10  -5     0    0    0 S  0.0  0.0   0:02.86 usb-storage                                                                                     
 3381 dhcp      13  -2  2396  636  316 S  0.0  0.1   0:00.65 dhclient3                                                                                       
 3666 root      16   0  1600  508  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3667 root      16   0  1600  508  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3668 root      16   0  1596  504  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3669 root      16   0  1600  508  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3670 root      16   0  1596  500  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3671 root      16   0  1600  504  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3882 root      16   0  2200 1152  640 S  0.0  0.1   0:00.01 acpid                                                                                           
 4005 root      16   0  1724  512  420 S  0.0  0.0   0:10.04 dd                                                                                              
 4007 klog      16   0  2424 1308  384 S  0.0  0.1   0:03.33 klogd                                                                                           
 4079 root      15   0 11804 1804 1268 S  0.0  0.2   0:00.00 gdm                                                                                             
 4112 messageb  16   0  2180  872  636 S  0.0  0.1   0:22.40 dbus-daemon                                                                                     
 4129 haldaemo  15   0  7256 5728 1648 S  0.0  0.6   0:18.50 hald 
```

```
top - 18:58:47 up 1 day, 12:25,  2 users,  load average: 1.88, 1.53, 1.39
Tasks:  99 total,   4 running,  95 sleeping,   0 stopped,   0 zombie
Cpu(s): 86.4%us, 10.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  2.3%hi,  1.3%si,  0.0%st
Mem:   1034964k total,  1018104k used,    16860k free,    32328k buffers
Swap:  3028212k total,     8156k used,  3020056k free,   688364k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
15988 bbolende  25   0  180m  69m  24m R 51.1  6.9   0:58.59 swiftfox-bin                                                                                    
13125 root      15   0  105m  62m 9912 S 19.9  6.2  25:45.45 Xorg                                                                                            
13344 bbolende  15   0  133m  46m  27m R 13.9  4.6  19:08.85 amarokapp                                                                                       
16015 bbolende  15   0 45056  15m 9.8m R 13.3  1.6   0:08.40 gnome-terminal                                                                                  
13214 bbolende  16   0 38368  22m  11m S  1.0  2.3   0:31.63 gnome-panel                                                                                     
16035 bbolende  15   0  2248 1140  844 R  0.7  0.1   0:00.54 top                                                                                             
13355 bbolende  15   0 26764  10m 8708 S  0.3  1.0   0:03.00 kded                                                                                            
    1 root      16   0  1628  536  448 S  0.0  0.1   0:01.27 init                                                                                            
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    3 root      34  19     0    0    0 S  0.0  0.0   0:03.76 ksoftirqd/0                                                                                     
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.18 events/0                                                                                        
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                                                         
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                                                         
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 kblockd/0                                                                                       
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
   96 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod                                                                                         
  129 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
  130 root      15   0     0    0    0 S  0.0  0.0   0:00.26 pdflush                                                                                         
  131 root      15   0     0    0    0 S  0.0  0.0   0:00.44 kswapd0                                                                                         
  132 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1723 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 1803 root      10  -5     0    0    0 S  0.0  0.0   0:00.77 kjournald                                                                                       
 1876 root      15   0  1600  548  468 S  0.0  0.1   0:00.03 logd                                                                                            
 2021 root      13  -4  2612 1052  360 S  0.0  0.1   0:00.53 udevd                                                                                           
 2771 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 shpchpd                                                                                         
 2805 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                       
 2931 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                       
 2932 root      10  -5     0    0    0 S  0.0  0.0   0:00.28 usb-storage                                                                                     
 2934 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                       
 2935 root      10  -5     0    0    0 S  0.0  0.0   0:02.84 usb-storage                                                                                     
 2937 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                       
 2938 root      10  -5     0    0    0 S  0.0  0.0   0:02.86 usb-storage                                                                                     
 3381 dhcp      13  -2  2396  636  316 S  0.0  0.1   0:00.65 dhclient3                                                                                       
 3666 root      16   0  1600  508  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3667 root      16   0  1600  508  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3668 root      16   0  1596  504  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3669 root      16   0  1600  508  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3670 root      16   0  1596  500  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3671 root      16   0  1600  504  432 S  0.0  0.0   0:00.00 getty                                                                                           
 3882 root      16   0  2200 1152  640 S  0.0  0.1   0:00.01 acpid                                                                                           
 4005 root      15   0  1724  512  420 S  0.0  0.0   0:10.06 dd                                                                                              
 4007 klog      16   0  2424 1308  384 S  0.0  0.1   0:03.33 klogd                                                                                           
 4079 root      15   0 11804 1804 1268 S  0.0  0.2   0:00.00 gdm                                                                                             
 4112 messageb  15   0  2180  872  636 S  0.0  0.1   0:22.40 dbus-daemon  
```

---

### Post by Darko Beta on 2007-02-24
> **irish_flu said:**
> Hey Darko-

Nice avatar!

Not that this helps you, but I have similar machine specs and do not experience that.  I'm using Firefox instead of Swiftfox, but that's the only major difference.

Heck yeah--Bender rules!  Actually, that does help because I have been wondering if this is normal or not.  So it's at least nice to know that there is some hope and to keep looking for a solution.

---

### Post by halitech on 2007-02-24
question, the pages you are loading, is there any flash, java or "garbage" on them? I've noticed my system do the same thing when I go to pages that have alot of java and stuff and I think it is related to the way it's handling java.

---

### Post by Darko Beta on 2007-02-24
> **halitech said:**
> question, the pages you are loading, is there any flash, java or "garbage" on them? I've noticed my system do the same thing when I go to pages that have alot of java and stuff and I think it is related to the way it's handling java.

Well, it's definitely worse on pages with a lot of that stuff.  I don't even bother visiting espn.com anymore because it's so bad.  But it doesn't seem to be *caused* by that sort of thing.  It's any web pages, really.

---

### Post by foxmulder881 on 2007-02-24
Yeah I get it on my machine and I don't even have Flash and Java installed.

---

### Post by yabbadabbadont on 2007-02-24
I get this behavior in firefox all the time when I open multiple tabs on these forums.  It is the javascript that causes the problem for me.  If I disable it for ubuntuforums.org, then I don't have any usage spikes.  Of course, the way these forums are written it pretty much sucks without JS.  (They need to learn a thing or two from the gentoo forums.  They work perfectly with or without JS enabled.)

---

### Post by halitech on 2007-02-24
wierd, I'm not at home on my box right now but I've never had any problems on the forum here but I notice it when I go to sites with java. I've even had multiple pages open here when searching for things and haven't noticed it. are all updates installed?

---

### Post by Darko Beta on 2007-02-24
All updates are installed.  I guess I'll try Opera for a bit and see how that goes...

---

### Post by tagra123 on 2007-02-24
Try this site.

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)


Check the swappiness setting -- really-- I mean really helped.  The ipv6 stuff helped too.

Try using the regular firefox.  I had some trouble with swiftfox and just tweaked firefox.

I believe I change eneable piping to true and set the max pipes to 8. Then disable ipv6 in it too.

Type about:config in the browser to change settings in firefox and search for maxpipes, and ipv6 etc.

---

### Post by tagra123 on 2007-02-24
One other thing some of the firefox extensions have caused problems too. If you have extensions installed disable them 1 by 1 and see if the problem goes away.

---

### Post by yabbadabbadont on 2007-02-24
In my case, it *is* the javascript.  I get the same behavior with no extensions installed and javascript enabled as I do with them (extensions) installed and javascript enabled.  Disable the javascript, problem goes away.  These forums rely too much on JS in my opinion anyway.  The options in the Search and Quick Links drop down menus should be (readily) available even without JS.

---

### Post by foxmulder881 on 2007-02-24
If these forums rely so much on Javascript, then how come I can happily use UbuntuForums.org without any issues when I don't even have Java installed? Explain that?

---

### Post by yabbadabbadont on 2007-02-24
> **foxmulder881 said:**
> If these forums rely so much on Javascript, then how come I can happily use UbuntuForums.org without any issues when I don't even have Java installed? Explain that?

Hmmm.  Perhaps it is becuase Java != JavaScript.

---

### Post by Darko Beta on 2007-02-24
```
Try this site.

http://tvease.net/wiki/index.php?tit...untu_for_speed

Check the swappiness setting -- really-- I mean really helped. The ipv6 stuff helped too.
```

Hey, thanks for that link.  I hadn't seen these particular tweaks before.  I applied them and rebooted and things have improved.  I'm still getting spikes, but usage doesn't seem to linger at 100% anymore--and my browser is noticeably faster.

---

### Post by foxmulder881 on 2007-02-24
> **yabbadabbadont said:**
> Hmmm.  Perhaps it is becuase Java != JavaScript.

WTF! :confused:

---

### Post by yabbadabbadont on 2007-02-24
> **foxmulder881 said:**
> WTF! :confused:

[http://en.wikipedia.org/wiki/Java_%28programming_language%29](http://en.wikipedia.org/wiki/Java_%28programming_language%29)

[http://en.wikipedia.org/wiki/Javascript](http://en.wikipedia.org/wiki/Javascript)

---

### Post by foxmulder881 on 2007-02-24
I know the difference, but are you saying these forums use Java or Javascript? Because I don't have the Javascript plugin installed.

---

### Post by yabbadabbadont on 2007-02-24
I apologize to the OP for hijacking his thread.  No more posts from me here.

---

### Post by foxmulder881 on 2007-02-24
> **yabbadabbadont said:**
> No more posts from me here.

Hmmm, convenient!

And since when did we go off topic?

---

### Post by tagra123 on 2007-02-25
> **Darko Beta said:**
> ```
Try this site.

http://tvease.net/wiki/index.php?tit...untu_for_speed

Check the swappiness setting -- really-- I mean really helped. The ipv6 stuff helped too.
```

Hey, thanks for that link.  I hadn't seen these particular tweaks before.  I applied them and rebooted and things have improved.  I'm still getting spikes, but usage doesn't seem to linger at 100% anymore--and my browser is noticeably faster.


I did my filesystem settings differently than described in the article.  I seem to get better performance with the filesystem set to  "data=journal" 

If you want to try it   edit your /etc/fstab   and add data=journal to the options for one of your partitions and give it a try.  Restart the computer.

---

### Post by jordanmthomas on 2007-02-25
foxmulder881, you do not need a javascript plugin installed.  It is a feature of the browser.  Firefox interprets the javascript by itself.  Don't believe me?  

Tools --> Error Console

That is the javascript error console.  Any javascript errors will be printed here.  
...or look for javascript examples online.  I guarantee you they will work unless you have explicitly turned javascript off.

---

### Post by Darko Beta on 2007-02-25
Just thought I'd note that I booted an xfce session and experimented, and the same thing occurred.  Then I booted XP and did a stress test by opening a bunch of tabs/web pages at once and then reviewed the system monitor.  It seems that XP is *slightly* better at this task, but with several tabs loading it bogs down as well (this is why it seems better on normal use with one or two tabs loading at a time).  So it seems as if this is is good as I can get with the setup I have right now.  I definitely achieved some improvement in my Ubuntu due to the suggestions here, so thanks again.  Now, I'm off to look for CPUs on the cheap... :)

---

### Post by moshuptrail on 2007-02-25
Have you disabled IPv6?

---

### Post by tagra123 on 2007-02-26
It sound to me like IPv6 is still churning too.


The machine I'm using right now has a geode 1750  and firefox is using less 1.8% of the processor and less than 7% of the memory according to conky.  

Ditch swiftfox -- completely remove it.  Do the adjustments to firefox described above and I  think you should have similar results.

---

