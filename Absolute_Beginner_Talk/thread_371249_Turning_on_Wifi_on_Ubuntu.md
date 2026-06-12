---
title: "Turning on Wifi on Ubuntu"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by drusepth on 2007-02-26
Hey, I installed Ubuntu 6.10 Edgy, and everything works and all, but somehow my Wireless got turned off sometime last night.  I can't seem to turn it back on.  I've tried Fn+F2, but nothing happens.  I've tried it on AC power and battery power.  I was tweaking some of the settings this morning, can anyone think of any settings that would have turned off WiFi?  Or how to turn it back on?

Other than this, Ubuntu is working grreaat for me.  :D

---

### Post by kpkeerthi on 2007-02-26
Its not very clear from your post what wireless manager you are using. I presume that you are using the default tool that came with Ubuntu. You can try go to System -> Administration -> Networking and see if the Wireless adapter is 'enabled'. Also make sure that correct interface (/dev/eth1, for instance) is selected by clicking the Properties button.

---

### Post by drusepth on 2007-02-26
I'm sorry I wasn't very clear.  You were correct in assuming I'm using the default tool that came with Ubuntu.  I go to System > Administration > Networking, and that's where my problem lies.   The only choices I have are Wired Connection and Modem Connection.  The wired connection is checked, which is how I'm online at the moment.  This is what it looks like:
Screenshot:  [http://img.photobucket.com/albums/v400/ChronoInc/net1.png](http://img.photobucket.com/albums/v400/ChronoInc/net1.png)

Yesterday, I was at my brothers using his wireless internet.  I had Wifi on and the little Wifi light on my Dell Inspiron 1501 notebook was on.  When I went to Network Settings then, Another option popped up, showing the choice of connecting to a wireless network.  But last night, I was running low on battery, and either I turned it off with FnF2, or it turned itself off automatically because of low battery power.  I switched back to the location profile I made while I was at his house, but that didn't work either.

I clicked the properties button, and this is what I get:
Screenshot: [http://img.photobucket.com/albums/v400/ChronoInc/net2.png](http://img.photobucket.com/albums/v400/ChronoInc/net2.png)
EDIT: The other choice besides DHCP is Static IP Address.

---

### Post by tjtansey on 2007-02-26
Highlight your wireless connection then open the properties for it and do the setup.  It should look like this.  Let me know if this helps.

---

### Post by drusepth on 2007-02-26
That's what I'm trying to say.  I have no wireless connection to highlight.  It's gone.  

I figured it was gone because my wireless won't turn on.

---

### Post by tjtansey on 2007-02-26
From console run this command:
sudo /etc/init.d/networking restart
That will restart all network interfaces.  If your wlan is a pcmia card, make sure it's plugged in.  I know the last was a duh, but I've forgot before:lolflag:

---

### Post by CCBalla10 on 2007-02-26
> **drusepth said:**
> That's what I'm trying to say.  I have no wireless connection to highlight.  It's gone.  

I figured it was gone because my wireless won't turn on.

actually try this....

  sudo depmod -a
  sudo modprobe ndiswrapper
 
**IF YOU USED NDISWRAPPER TO INSTALL YOUR WIRELESS CARD DRIVER**

then to have it load on start-up try this
 
sudo ndiswrapper -m

let us know if this worked for you...

---

### Post by drusepth on 2007-03-02
[quote="CCBalla10"]let us know if this worked for you...[/quote]
I found another fix for it before reading your replies.  To anyone interested, this works great:
[http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

---

### Post by tjtansey on 2007-03-03
Good for you!  While we each have figured what works best for us it doesn't work for everyone.  Putting up a link to what did work for you just helps someone in the future that runs into same difficulty as you.

---

