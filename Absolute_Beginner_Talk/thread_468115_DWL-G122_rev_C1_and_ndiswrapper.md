---
title: "DWL-G122 rev C1 and ndiswrapper"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by tranzit on 2007-06-08
Hello everybody
Several weeks ago i installed ubuntu on my PC (7.04-desktop-i386), but i can't make internet to work. The best thing i have done is this:
copied dr71wu.inf and dr71wu.sys files from windows xp
added some native ubuntu drivers to blacklist (because they didn't support wpa):    
[LIST]
[*]sudo gedit /etc/modprobe.d/blacklist
[*]blacklist rt73usb
[*]blacklist rt2570e
[*]blacklist  rt73usb
[/LIST]
then i installed windows drivers:
[LIST]
[*]ndiswrapper -i DR71WU.inf
[*]ndiswrapper -l
[*]dr71wu : driver installed
[*]device (07D1:3C03) present
[*]sudo modprobe ndiswrapper
[/LIST]
but after restart in network manager now wireless connection is available :(. Then trying to do something with iwconfig i get:
[LIST]
iwconfig
[*]lo no wireless extensions.
[*]eth0 no wireless extensions.
[/LIST]
So now i'am stuck.

---

### Post by ayenack on 2007-06-08
You don't need ndiswrapper with this card it should work right out of the box. Try removing ndiswrapper and then configure it from System>Administration>Network. Put in the name of your network the password type and network password and that should do it.

Best of luck. ayenack.

My mistake C1 rev may not work out of the box. Check this [site]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73") I think it may have the answer. I think you need the RalinkRT73 Drivers. Check it out might help.

---

### Post by tranzit on 2007-06-09
Default ubuntu driver doesn't support wpa ([http://img180.imageshack.us/img180/5641/screenshotth0.png](http://img180.imageshack.us/img180/5641/screenshotth0.png)). I also tried native drivers but with no luck just some partition formats ;). But thank you ayenack for your reply.

---

### Post by ayenack on 2007-07-31
Hey tranzit not sure if you sorted out your problem with the DWL-G122 rev C1 or if you're still trying to use the card but if you are take a look at [this post]("http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73") I had to set up the exact same card the other day (rev C1) and this got me through the set up in no time very good.

Best of luck. ayenack.

---

### Post by pytheas22 on 2007-08-08
ayenack,

What did you do to make it work?  No matter how hard I try, I can't get this card to connect to my WPA network.

I followed the instructions in that post ([http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)), blacklisted the default drivers included in Feisty and compiled the legacy rt73 driver to replace them.  But the rt73 driver doesn't work for me; it doesn't recognize my card at all.  I think it's because I have an SMP kernel.  Are you using anything besides a regular 32-bit kernel?

---

### Post by ayenack on 2007-08-10
Hello pytheas22.

Can you do these things for me and paste the results on this thread. From terminal.

iwconfig

ifconfig

lsusb

sudo gedit /etc/network/interfaces (blank out your WPA/WEP password from this file)

The reason I ask this is so that I can be sure that you have the driver installed and I need to see what's going on with your internet connection and your interfaces.

Thanks. ayenack

It's entirely possible that your SMP kernel is the problem. Also if you have the 64BIT version of Ubuntu this could also cause problems. I think but am not sure that some of these are documented on the post that you used to install the driver. You did unplug your wired network during the install?

---

