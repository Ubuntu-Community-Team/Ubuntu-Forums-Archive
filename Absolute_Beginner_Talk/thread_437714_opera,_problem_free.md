---
title: "opera, problem free?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-05-09
Is anybody out there in Ubuntu land running OPERA with no problems?



I like firefoz, I really, really like Epiphany but I have been having issues with both.

I use opera email client fo rmy emailing needs and I love it. I also love the browser and the saving sessions bit.

I woul dlove to keep using jus topera but there a sites where it freeezes up and it is very annoying.


robi

---

### Post by kerry_s on 2007-05-09
Mine's running fine, i installed via the opera repo->

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free 

key->

gpg --keyserver subkeys.pgp.net --recv-key 033431536A423791
sudo gpg --armor --export 033431536A423791| sudo apt-key add -

---

### Post by derred on 2007-05-09
Just use the one that Automatix gives you. It works for me just fine. 
__________________________________
[www.getautomatix.com](www.getautomatix.com) is my homepage

---

### Post by beanco on 2007-05-09
last tiem i checked automatix there was no opera there, but i could be wrong... it has been a week...

i will be home later and check....

robi

---

### Post by Sef on 2007-05-09
> Is anybody out there in Ubuntu land running OPERA with no problems?



I like firefoz, I really, really like Epiphany but I have been having issues with both.

I use opera email client fo rmy emailing needs and I love it. I also love the browser and the saving sessions bit.

I woul dlove to keep using jus topera but there a sites where it freeezes up and it is very annoying.



It seems like you have a problem with your browsers.   What problems are you having with Firefox and Epiphany?  

I use Opera and have never had a problem with it.    What site are you having problems with?

Easy way to download Opera is this:  [http://www.opera.com]("http://www.opera.com") > Click on dowload > Click on the downloaded package to open.

---

### Post by beanco on 2007-05-09
i should mention that the problems are:


certain sites... mostly telemarktips.com and this forum

freeze up when I am using the forums. I have to force quite, restart and it may work then or it may not.


the other sucky thing is on this forum, the msg field keeps changing size ... sometimes it gets so small I cannot actually read-write.

robi

---

### Post by Sef on 2007-05-09
I don't have a problem with Opera with those sites.   I wonder if there is something up on your end.  I don't know enough to give you any advice on it.

---

### Post by galv on 2007-05-09
I'm using Opera, it runs OK (not perfect).
I've some Flash issues, and other minor upsets (like donwload a file and open it with an external program, or middle click opening new tab [not pasting])

Instaled it from Opera website (using Feisty)

---

### Post by kerry_s on 2007-05-09
> **beanco said:**
> i should mention that the problems are:


certain sites... mostly telemarktips.com and this forum

freeze up when I am using the forums. I have to force quite, restart and it may work then or it may not.


the other sucky thing is on this forum, the msg field keeps changing size ... sometimes it gets so small I cannot actually read-write.

robi

the message field shrinking is the the fit-to-width setting under, preferences, webpages, next to zoom, make sure that's unchecked.

Are you using a block list for opera? it will get rid of most of that crap.

gedit ~/.opera/urlfilter.ini
copy and paste under [exclude]

*-ad.cgi*
*-ads/*
*.2o7.net*
*.ad-*
*.ad.*
*.adbrite.*
*.ads.*
*.adtomi.*
*.advertising.*
*.banner*
*.blogads.*
*.casalemedia.*
*.click*
*.doubleclick.*
*.geo.yahoo.*
*.google-analytics.*
*.google.*/adfetch*
*.google.*cleardot.gif
*.googlesyndication.*
*.kontera.*
*.linkbuddies.*
*.overture.*
*.qksrv.*
*.roar.*
*.slickkicks.*
*.tradedoubler.*
*.trafficzap.*
*.tribalfusion.*
*/accresults.*
*/ad.*
*/ad/*
*/ad_*
*/adbot.*
*/adc_*
*/adclient.*
*/adcouncil/*
*/adframe.*
*/adgifs/*
*/adgraph/*
*/adimages/*
*/adinfo*
*/adlog.*
*/adlog/*
*/adrotator.*
*/ads.*
*/ads/*
*/ads_*
*/advert*
*/adview.*
*/affiliates/*.js
*/banner/*
*/banners/*
*/hotfreebies.html*
*/housead/*
*/kokoku/*
*/liveads/*
*/pagead/*
*/phpads/*
*/pop.cgi*
*/pop.htm
*/pops/*
*/poptest.*
*/popup/*
*/printads/*
*/redir.asp*
*/softad/*
*/sponsor/*
*/sponsors/*
*/tracker/*
*/tw/adt*
*120x240*
*120x600*
*120x90*
*160x600*
*234x60*
*336x280*
*468x60*
*728x90*
*_ad_*
*_ads_*
*_advert*
*_adx_*
*_banner_*
*_borders/*
*_popup.*
*_superad*
*a.p.f.qz.*
*a.r.tv.*
*a.tribalfusion.*
*ad-flow*
*ad.trafficmp.*
*ad_type*
*adbot*
*adclick*
*adclix*
*adclub*
*adcycle*
*adflight*
*adframe*
*adimage*
*adknowledge*
*adlink*
*adlogix.*
*admaximize*
*admex*
*admonitor*
*adpulse*
*adrunner*
*adserv*
*adsoftware*
*adswap*
*adtomi.*
*aureate*
*avenuea*
*banner.*
*banners.*
*bluestreak.*
*burstmedia*
*burstnet*
*clickxchange*
*darkblue.*
*darkbluesea.*
*dbbsrv.*
*doubleclick*
*exitpopup*
*flycast*
*focalink*
*headerpopup*
*hitexchange*
*hitlist*
*hitsites*
*houseads_*
*i.us.rmi.yahoo.*
*imaginemedia*
*intellitxt*
*jsads*
*linkads*
*linkexchange*
*linkpopup*
*linkshare*
*linksynergy*
*media.fastclick*
*paypopup*
*popieen.*
*popme.*
*popunder*
*popup_*
*popupad*
*ps.interpolls.*
*radiate*
*secure.webconnect*
*smartsize_*
*spinbox.versiontracker.*
*spylog*
*subs.timeinc.*
*toolbar.google.*
*trafic.ro/*
*us.a1.yimg.*
*us.f.yahoofs.*
*valueclick*
*view.atdmt*
*x.mycity.*
*z.about.*
*zdmcirc*

Also leave the plugins off unless you come across a site that you want to use them on, you can set it on for certain sites, right click, edit site preferences. That will get rid of flash for sites you don't want to use it. Flash is the main thing that locks up opera. I use a quick preference button in my startbar. Hopefully with the block list you won't have problems in the forums, it uses that google spy crap.
 [http://operawiki.info/CustomButtons](http://operawiki.info/CustomButtons) Pic->

---

### Post by beanco on 2007-05-09
what is a block list for opera?

I may or may not be using it. I have no idea what it is.

when iget back to the opera machine i will look

robi

---

### Post by kerry_s on 2007-05-09
> **beanco said:**
> what is a block list for opera?

I may or may not be using it. I have no idea what it is.

when iget back to the opera machine i will look

robi

If you don't know what it is than you don't have one. :) 
It's a block list to block all the nasties on sites, it's like the adblock for firefox. When you right click in opera you'll see block content, that's what it is, but instead of you manually doing all the blocking yourself there are premade lists, the list i posted is the 1 i use, it's a good list that's not to long and it does not slow down the browser, there are alot of others out there you can google opera blocklist to find them, careful with the long ones some will slow your browser down.

---

### Post by beanco on 2007-05-09
> **kerry_s said:**
> the message field shrinking is the the fit-to-width setting under, preferences, webpages, next to zoom, make sure that's unchecked.

hey that worked like a charm...


> Are you using a block list for opera? it will get rid of most of that crap.

gedit ~/.opera/urlfilter.ini
copy and paste under [exclude]

*-ad.cgi*
*-ads/*
*.2o7.net*
*.ad-*
*.ad.*



so is that long list of *junk* below the block list?

what does copy and paste under (exclude) mean?

Under what? exclude what?

thanks for your help...






> Also leave the plugins off unless you come across a site that you want to use them on, you can set it on for certain sites, right click, edit site preferences. That will get rid of flash for sites you don't want to use it. Flash is the main thing that locks up opera. I use a quick preference button in my startbar. Hopefully with the block list you won't have problems in the forums, it uses that google spy crap.


I am a bit confused but I will go through this bit again and figure it out....

I guess I will have to figure out how to make a quick preference button on my start bar

robi

---

### Post by hyper_ch on 2007-05-09
Btw, you can make a blocklist of domains in /etc/hosts and then it will apply to all services, not just one browser...

e.g.

127.0.0.1 adserver.com

---

### Post by kerry_s on 2007-05-09
> **hyper_ch said:**
> Btw, you can make a blocklist of domains in /etc/hosts and then it will apply to all services, not just one browser...

e.g.

127.0.0.1 adserver.com

No,no, Don't put it in /etc/hosts that will slow opera alot, it don't play nice with hosts file. it's best to put it right in opera it self. I was using a host file before, it took me a while to figure out that it was slowin opera down, got rid of it and bam speed. The reason is opera will wait till the sites that are blocked time out, instead of just continuing, for it it's like a nonresponsive connection. It took me alot of reading, to get opera up to the speed i want, at least 2->3sec's or less load time, i'm getting a 3 sec time on these forums where it use to take 10 sec's + to load.

---

### Post by kerry_s on 2007-05-09
> **beanco said:**
> hey that worked like a charm...






so is that long list of *junk* below the block list?

what does copy and paste under (exclude) mean?

Under what? exclude what?

thanks for your help...








I am a bit confused but I will go through this bit again and figure it out....

I guess I will have to figure out how to make a quick preference button on my start bar

robi

Yes, that is the block list. just run> gedit ~/.opera/urlfilter.ini
and it will open the file you need to copy and paste to. if you want to go to it manually open nautilus and press ctrl+h that will show you hidden files, click on .opera, which is your settings, then locate the file and open it with gedit. Here is what my whole thing looks like.

```
Opera Preferences version 2.1
; Do not edit this file while Opera is running
; This file is stored in UTF-8 encoding

[prefs]
prioritize excludelist=1

[include]
*

[exclude]
*-ad.cgi*
*-ads/*
*.2o7.net*
*.ad-*
*.ad.*
*.adbrite.*
*.ads.*
*.adtomi.*
*.advertising.*
*.banner*
*.blogads.*
*.casalemedia.*
*.click*
*.doubleclick.*
*.geo.yahoo.*
*.google-analytics.*
*.google.*/adfetch*
*.google.*cleardot.gif
*.googlesyndication.*
*.kontera.*
*.linkbuddies.*
*.overture.*
*.qksrv.*
*.roar.*
*.slickkicks.*
*.tradedoubler.*
*.trafficzap.*
*.tribalfusion.*
*/accresults.*
*/ad.*
*/ad/*
*/ad_*
*/adbot.*
*/adc_*
*/adclient.*
*/adcouncil/*
*/adframe.*
*/adgifs/*
*/adgraph/*
*/adimages/*
*/adinfo*
*/adlog.*
*/adlog/*
*/adrotator.*
*/ads.*
*/ads/*
*/ads_*
*/advert*
*/adview.*
*/affiliates/*.js
*/banner/*
*/banners/*
*/hotfreebies.html*
*/housead/*
*/kokoku/*
*/liveads/*
*/pagead/*
*/phpads/*
*/pop.cgi*
*/pop.htm
*/pops/*
*/poptest.*
*/popup/*
*/printads/*
*/redir.asp*
*/softad/*
*/sponsor/*
*/sponsors/*
*/tracker/*
*/tw/adt*
*120x240*
*120x600*
*120x90*
*160x600*
*234x60*
*336x280*
*468x60*
*728x90*
*_ad_*
*_ads_*
*_advert*
*_adx_*
*_banner_*
*_borders/*
*_popup.*
*_superad*
*a.p.f.qz.*
*a.r.tv.*
*a.tribalfusion.*
*ad-flow*
*ad.trafficmp.*
*ad_type*
*adbot*
*adclick*
*adclix*
*adclub*
*adcycle*
*adflight*
*adframe*
*adimage*
*adknowledge*
*adlink*
*adlogix.*
*admaximize*
*admex*
*admonitor*
*adpulse*
*adrunner*
*adserv*
*adsoftware*
*adswap*
*adtomi.*
*aureate*
*avenuea*
*banner.*
*banners.*
*bluestreak.*
*burstmedia*
*burstnet*
*clickxchange*
*darkblue.*
*darkbluesea.*
*dbbsrv.*
*doubleclick*
*exitpopup*
*flycast*
*focalink*
*headerpopup*
*hitexchange*
*hitlist*
*hitsites*
*houseads_*
*i.us.rmi.yahoo.*
*imaginemedia*
*intellitxt*
*jsads*
*linkads*
*linkexchange*
*linkpopup*
*linkshare*
*linksynergy*
*media.fastclick*
*paypopup*
*popieen.*
*popme.*
*popunder*
*popup_*
*popupad*
*ps.interpolls.*
*radiate*
*secure.webconnect*
*smartsize_*
*spinbox.versiontracker.*
*spylog*
*subs.timeinc.*
*toolbar.google.*
*trafic.ro/*
*us.a1.yimg.*
*us.f.yahoofs.*
*valueclick*
*view.atdmt*
*x.mycity.*
*z.about.*
*zdmcirc*

```

For the buttons just go here> [http://operawiki.info/CustomButtons](http://operawiki.info/CustomButtons) < click on the buttons you want and it will put it in your my buttons list and you can drag it anwhere you want to put it, i just prefer my start bar because it's hidden till i need it, when i want it to pop up i just click on the address bar. i like to keep my look clean.

---

