---
title: "can't download flashplugin-nonfree"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by HDave on 2007-11-18
Strange error here.  Was trying to install the Ubuntu restricted extras to get flash.  But it hung up trying to download flash from adobe.  I thought it was synaptic or something else so I've been reading up on it all evening.  

Here's where I am at.  Running Gutsy on my laptop...brand new install.  Basically if I try to do a 

```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz

```
 
It hangs after 5,469 bytes.  

Furthermore, if I go to Adobe's website and click right on the "install_flash_player_9_linux.tar.gz file the downloads window says "Starting..." and again it hangs.  If I repeatedly try to download I can add another 5,469 bytes each time. 

I have seen several other people on the forums with this problem, but no resolution.

I have Ubuntu running in a VM on this laptop (when I boot from Windows) and it downloaded and installed just fine!!!)   :confused:

ANYONE???

---

### Post by duruttye on 2007-11-19
Have you tried to install it from automatix?
I just looked, it does have some codecs. Flash too.
getautomatix.com

---

### Post by Nano Geek on 2007-11-19
That link works fine for me. Do you want to try it again?

---

### Post by duruttye on 2007-11-19
Works for me, too.

---

### Post by HDave on 2007-11-21
I just tried the link again from my laptop via my verizon wireless card and it worked.

I think the problem was the download being blocked either my my ISP or my router at home...thanks for your help everybody.  Will try again when I get back home and update this thread...

---

### Post by HDave on 2007-12-16
After I was able to download the plugin from my dial-up modem, I figured it was my ethernet connection.  When I again failed to download it from my wifi, I realized that is must be my router.

I have since found other websites besides adobe that didn't work.

Why my router hiccups on the web sites and not others I have no idea.  Why it hiccups when my (dual-boot) machine was running Ubuntu and was fine when I was running Windows I also have no idea. 

For no good reason I did a firmware upgrade and reboot the router and the switch.

Been working for 2 straight weeks now.  

Hmmmm.......

---

### Post by ajmorris on 2007-12-20
> **duruttye said:**
> Have you tried to install it from automatix?
I just looked, it does have some codecs. Flash too.
getautomatix.com

Could you please not suggest the use of automatix, it is not supported here, and users wishing to use it should seek help from the automatix site.

---

### Post by Nano Geek on 2007-12-20
> **ajmorris said:**
> Could you please not suggest the use of automatix, it is not supported here, and users wishing to use it should seek help from the automatix site.He's not asking for help, he's providing it. 

Apparently you don't like Automatix, but it has helped me and I doubt it will harm his system.

---

### Post by ajmorris on 2007-12-20
> **asjdfwejqrfjcvm msz34rq33 said:**
> He's not asking for help, he's providing it. 

Apparently you don't like Automatix, but it has helped me and I doubt it will harm his system.

I was not saying he was asking for help, i was merely telling him for future reference that AutomatiX is not supported here. And whether it has helped you in the past, it is no supported because it is known to break systems from the simplest of installs.

---

### Post by Nano Geek on 2007-12-20
> **ajmorris said:**
> I was not saying he was asking for help, i was merely telling him for future reference that AutomatiX is not supported here. And whether it has helped you in the past, it is no supported because it is known to break systems from the simplest of installs.OK then, it is suggested that the OP uses Automatix with the fair warning that it has damaged some users installs in the past.

---

