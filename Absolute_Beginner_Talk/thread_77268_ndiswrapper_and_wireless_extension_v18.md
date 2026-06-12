---
title: "ndiswrapper and wireless extension v18"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by ingenious on 2005-10-16
Hello,

I just installed breezy badger and it has been working pretty well, except for my wireless card (Netgear MA521).  I found that breezy came with ndiswrapper 1.1, and the latest version was 1.4, so I completely uninstalled the prior with synaptic and then followed directions at the following pages to get it compiled and installed:

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)
[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Everything was going well when I hit a brick wall.  When I run iwconfig, it tells me:
> wlan0     Recommend Wireless Extension v18 or later,
          Currently compiled with Wireless Extension v17.

I did some investigating and found a patch for v17-v18, and downloaded it but I am not familiar with diff files and what to do with them.  Without wireless support, I probably won't be using linux at all as most of the time I don't have an ethernet cord handy (especially at school).  Does anyone have any advice?

I appreciate your help.

Joel

---

### Post by AgenT on 2005-10-16
Search the forum/wiki on how to apply diff patches. It is pretty simple (one command). ```
man patch
```. The -p option is the tricky part to get which is why I am not telling you the exact command you need to execute since that depends on your patch and how/where you extract it to (that and it has been a long time since I used patch). Read the readme that came with your patch. Note (just in case): you apply the patch PRIOR to compiling.

---

### Post by ingenious on 2005-10-16
Thanks for the tip, but after toying with it some more, I found that I could get it to work when I didn't use a WEP password.  Then, I tried with WEP shared key instead of WEP PSK (i guess there's a big difference) and it works!  Thank god.  I don't think I will patch the wireless extensions, as long as it works as well at schcool as it does at home.

thanks again

---

