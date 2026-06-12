---
title: "Firefox heavy on uses"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-12-09
Is the Firefox slowness linked to (what ive experienced) A.  poor java and heavy java sites that use alot of flash animations, B.  Speed/specs of one's computer or the processor ..just trying to understand why in the world in linux is seems buggy and just unresponsive...I would think "in an ideal world with linux since there arent any spyware//viruses and those things it would run flawlessley...This isnt a rant, just trying to kind of understand why it would act this way (In my opinion, this shouldnt happen to alot of people who use it)  I'd like to get more opinions as well...

---

### Post by kellemes on 2007-12-09
Firefox isn't the fastest browser out there, and it's performance is highly depending on the page it has to render.
GNU/Linux is just an OS like any other, it's not flawless at all, although you may have it setup in such a way it outperforms others. Obviously specs are important.. compiz, beagle and other heavy packages meant for comfort are often creating the slowdown of the system..
Any OS will be buggy and unresponsive when setup wrong or running on hardware not able to handle it.

---

### Post by jordanmthomas on 2007-12-09
Try another browser.  Epiphany uses the same rendering engine but feels a lot faster than Firefox.  Firefox isn't your only choice.

I'm using Firefox now, but I am a huge fan of Opera...lightning fast.

---

### Post by sports fan Matt on 2007-12-09
Hey Jordan..

I have used eipiphany also, im typing this in opera now though...It just seems to me that on a standard windowze machine (that has enough ram like 1 gb or more) and a decent processor, the speed difference on Firefox (at least to me) running 384 ram, and a celeron processor was noticeable when I booted ubuntu...just saying it felt sluggish and I didnt understand why it would in the transfer from Windows XP to Ubuntu

---

### Post by edm1 on 2007-12-09
are you trying to say firefox on windows on 1 gb of ram and a decent processor is faster than firefox on ubuntu on 384mb of ram and a celeron?

---

### Post by sports fan Matt on 2007-12-09
I was just throwing that figure out there..I was using my experience cause I know alot have trouble with it and I was just trying to understand why it may be slower coming from an xp based machine to Ubuntu... I think im just going to use Opera...It seems from what ive seen better (even though its not open source) in just faster web surfing and performance and responsiveness...

---

### Post by jordanmthomas on 2007-12-09
Yeah, if Opera was open-source I would be an evangelist. :)
I can't say exactly why Firefox is slower on Linux than Windows (it would be likely very technical anyway) but you should know that you're not alone.

Firefox is getting slower and slower with every release.

---

### Post by mcduck on 2007-12-09
No matter what you do, Java and Flash use a lot of memory and CPU power. And if your Ubuntu machine is indeed that much slower than the Windows machine it's no surprise if it doesn't perform as well. You are comparing apples and oranges here..

Slower computer is slower computer, and even running Linux can't change that.

---

### Post by sports fan Matt on 2007-12-09
mc..Exactly..no matter what you do, its based on the computer system...Problem is alot of sites are also heavy (meaning things wont display properly without flash/java wnabled)

Jordan, Agreed, you would think they would address the issues of speed,/slowness in a release..They might be addressing in in FF3/Gran Paradso, I wouldnt be surprised..I wonder when a release date for Opera 9.5 Final and FF 3 (Gran Paradiso) is?

---

### Post by jordanmthomas on 2007-12-09
They say they are working on the speed inf FF3.  I haven't bothered to try it out, but I think they are working on it.

---

### Post by edm1 on 2007-12-09
Firefox 3 (well Swiftfox) has incredible speed improvements with respect to the application loading time. Takes ~1 sec to load compared to 5. General usage seems to be nippier too.

---

### Post by Austin_KW on 2007-12-09
Another vote for firefox 3. It is only the first beta but it is much faster, especially noticeable on older PC.

Also try running the adblock plus extension, many delays are caused by slow ad servers.

---

### Post by crimesaucer on 2007-12-09
> **edm1 said:**
> Firefox 3 (well Swiftfox) has incredible speed improvements with respect to the application loading time. Takes ~1 sec to load compared to 5. General usage seems to be nippier too.

Yeah, Swiftfox 3 prebeta 2 is so fast!!!!! 

I had Minefield prebeta 2 which also was fast, but damn...


Then again, I just stopped using Compiz Fusion and now that I'm on xfwm4, my computer is so much faster!


I'm on Archlinux-->--xfce4.4.2-->--xfwm4-->--Swiftfox 3 prebeta 2..... and it so freaking fast!!!!!

---

### Post by sports fan Matt on 2007-12-09
How can I get this Swiftfox 3 prebeta 2 you all speak of?

---

### Post by crimesaucer on 2007-12-09
> **sox fan Matt said:**
> How can I get this Swiftfox 3 prebeta 2 you all speak of?

here: [http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by jordanmthomas on 2007-12-09
I had been putting off trying Firefox 3 because I've been busy.
I just tried it out though and I think my favorite part of all is it actually uses the buttons from my gtk theme.

---

### Post by edm1 on 2007-12-10
> **sox fan Matt said:**
> How can I get this Swiftfox 3 prebeta 2 you all speak of?

It is in the repos. Swiftfox is just firefox optimised for your specific processor. It uses the same config files as firefox so you'll still have all your bookmarks, addons, passowrds. However, you may have problems with extensions if they are not yet compatible with ff3.

---

### Post by spiderbatdad on 2007-12-10
some folks have done this:
[http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html](http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html)
Feisty performance - Fly like a butterfly.

Quote:
1. Disable IPv6
Edit /etc/modprobe.d/aliases and change the line:

alias net-pf-10 ipv6

to

alias net-pf-10 off #ipv6


3. Aliasing hostname to localhost
Modify /etc/hosts's first two line as follows:

127.0.0.1 localhost yourhost
127.0.1.1 yourhost

where yourhost, is your chosen hostname. This will fasten up applications load.

I followed another thread and entered about:config into the browser address bar then scrolled down to find ipv6=true. I right clicked on it and chose toggle, changing the value to false. Firefox does seem to be running noticeably faster.
__________________

---

### Post by sourcemorph on 2007-12-10
is there a foxyproxy kinda thing for opera... if ther is i'll switch right away...

---

### Post by KalTorak on 2007-12-10
Disable ipv6 (via about:config) and use opendns

---

### Post by ddrplayer512 on 2007-12-10
Do you Compiz Fusion? Or Beryl? Because Firefox has some trouble with me while that is turned on. That is one of the reasons I leave the eye candy turned off.

---

### Post by crimesaucer on 2007-12-10
> **spiderbatdad said:**
> some folks have done this:
[http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html](http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html)
Feisty performance - Fly like a butterfly.

Quote:
1. Disable IPv6
Edit /etc/modprobe.d/aliases and change the line:

alias net-pf-10 ipv6

to

alias net-pf-10 off #ipv6


3. Aliasing hostname to localhost
Modify /etc/hosts's first two line as follows:

127.0.0.1 localhost yourhost
127.0.1.1 yourhost

where yourhost, is your chosen hostname. This will fasten up applications load.

I followed another thread and entered about:config into the browser address bar then scrolled down to find ipv6=true. I right clicked on it and chose toggle, changing the value to false. Firefox does seem to be running noticeably faster.
__________________


For more tips like this, check these links:

[http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)
[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)
[http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html](http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html)
[http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml](http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml)
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)




You can also check these 3 Mozilla pages out concerning **[COLOR="Red"]about:config[/COLOR]** settings:

[http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)
[http://kb.mozillazine.org/Category:Preferences](http://kb.mozillazine.org/Category:Preferences)
[http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)


... this is pretty much the same thing as about:config, except it edits those settings through the pref.js in your profile (the op wrote user.js but is wrong... it is the pref.js):

[http://ubuntuforums.org/showthread.php?t=181107](http://ubuntuforums.org/showthread.php?t=181107)

---

### Post by sports fan Matt on 2007-12-10
Ddr,

I tried to uninstall compiz and actually upon doing that...my Firefox was srinking in the page and i couldnt get a full page display and the tiops of pages were cut off, so I had to reinstall...

Crimw, i'll loook into those pages as well, Thanks!

---

### Post by crimesaucer on 2007-12-10
> **sox fan Matt said:**
> Ddr,

I tried to uninstall compiz and actually upon doing that...my Firefox was srinking in the page and i couldnt get a full page display and the tiops of pages were cut off, so I had to reinstall...

Crimw, i'll loook into those pages as well, Thanks!

 For you problems about the tops of the pages being cut off... that would be your Emerald windows being uninstalled along with Compiz.


To get uninstall Compiz/Emerald and get your original window manager back (metacity or xfwm4), you need to do this:

for ubuntu:

```
killall compiz
``` 

```
metacity --replace &
```

... or if you use xubuntu:

```
killall compiz
``` 

```
xfwm4 --replace &
```


Now, for those links I put up there, be sure to read them all and figure out what you are comfortable with. 

I would recommend you only do these at first (these are more for browsing... the others are for bootup and other stuff):

OpenDNS: [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)
Local DNS: [http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html](http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html)


and these Mozilla about:config tweaks until you are comfortable with some of the other tips: [http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)



... and some of those tips are a little outdated, so do your research before doing anything.

---

