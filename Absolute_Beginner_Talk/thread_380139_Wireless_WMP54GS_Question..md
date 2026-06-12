---
title: "Wireless WMP54GS Question."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-03-09
Hello again, need a quick question answered...

[http://i22.photobucket.com/albums/b324/FFManiac1/Screenshot.png](http://i22.photobucket.com/albums/b324/FFManiac1/Screenshot.png)

I am trying to set up my WMP54GS card up to work with my WRT54GS router, I have followed the UbuntuGuide.org steps for installing ndiswrapper and gotten to the point when I need to manually install the .inf file.

My problem is I have two, as can be seen on the screenshot. Which do I need? or do I have to install both for my ndiswrapper to work?

Hope someone can help, have almost finished setting up my machine thanks to you very nice people :).

---

### Post by benfindlay on 2007-03-09
Not entirely sure but you could always try installing one and seeing if it works.

To remove one that doesn't work, you just type ```
sudo ndiswrapper -e [name of driver]
```

And to install you type ```
sudo ndiswrapper -i [name of driver]
```

That way you can simply do trial and error!
But my personal view is that I would try wmp54gs.inf first!

Hope this helps

---

### Post by starcraft.man on 2007-03-09
aye, did that and my hardware detects in the windows wireless manager.

I got all the way to the iwconfig section and I think I may slightly have a problem...

This is the section I was referring to...

[QUOTE=ubuntuguide.org]
    * Now you can configure your wireless card with ifconfig and iwconfig. 

    e.g. Supposing wlan0 is your wireless device. 

sudo iwconfig wlan0 essid "AP" key ababababababababab mode Managed
iwconfig

    * You sould now be able to see the MAC address of the access point and signal rate. 

[/QUOTE]

I did that and replaced wlan0 with eth1 which is the identifier for where my Wireless card is assigned and then I ran iwconfig and got this...

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Why does it say access point invalid? and where exactly am I suppose to see the mac address and signal rate?

---

### Post by benfindlay on 2007-03-09
When I got to that stage I used the GUI based network options in System>>Administration>> to configure it. Just fill in the ssid and dhcp/static options there!

Also if you install a program called wifi-radar with ```
sudo apt-get install wifi-radar
``` you can scan for wireless networks and connect through that. Again, its GUI based!

Hope this helps!

---

### Post by starcraft.man on 2007-03-09
Thanks, I like the wifi radar app but I have a small problem, my network is WPA protected for security and when I went to the WPA drop down in wifi radar it sad Driver: with a blank space to the right, what does that mean?

---

### Post by benfindlay on 2007-03-09
you need to install a program called wpasupplicant. Never used it, but there are guides to configuring it on this site I believe. I personally went with locking wireless access to my home network down to known MAC addresses. That way no-one can access it unless I approve them manually in the router! That got round the whole issue of getting WPA to work!

---

### Post by starcraft.man on 2007-03-09
> **benfindlay said:**
> you need to install a program called wpasupplicant. Never used it, but there are guides to configuring it on this site I believe. I personally went with locking wireless access to my home network down to known MAC addresses. That way no-one can access it unless I approve them manually in the router! That got round the whole issue of getting WPA to work!

Oi... I'd recommend you listen to security now podcast with Leo Laporte and Steve Gibson... [http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm) episode 11 and 13, or read other sites concerning such things... MAC address filtering is really not a secure means of locking wifi... Thanks for the help though, I think I have found out how to do it :).

---

