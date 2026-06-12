---
title: "about to uninstall the whole mess...."
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by graham4 on 2008-01-05
Got a new tower with feisty Fawn 7.04  Fine so far.  Tried to find a modem and hit the wall.  I am on dial up, and after most quit laughing, one fellow advised an external serial modem.  Fine, got that.  Actiontec EX560LKU   Hooked this modem up, finally found the place to at least enter my ISP number, and....and...um...where is whatever it is you hit to even try to dial ?  
    The tan blank screen is nice, but is not much help.  I see reference to 'device manager', but can't find it.  The more I look at the threads here, I wonder if this system is not more trouble than it is worth.  Ant help would be appreciated, but at this point I am thinking my old clean copy of 98se is looking real good now....

---

### Post by Fixman on 2008-01-05
You can use the network-manager (the computers icon on the taskbar) but if you have dial-up connection I really reccommend you not to use Ubuntu, but to use another Linux Operative system that doesn't need very mutch network (like PCLinuxOS).

---

### Post by lisati on 2008-01-05
Have a look on the System->Administration menu for "Network" (not to be confused with "network tools") - once it starts there should be an option for tinkering with your modem settings.

---

### Post by graham4 on 2008-01-05
ummm.about what I figured-I got suckered.  Oh well.  Thanks fixman.  I have had enough abuse-it just isn't worth it.  
   lisati-thank you too.  I will look, but apparently a moot point now.  Looks best to just trash ubuntu and go another route.  Thanks again

---

### Post by ~LoKe on 2008-01-05
Hardy Heron is expected to have much better dialup support.

---

### Post by Keith_Beef on 2008-01-05
> **graham4 said:**
> Got a new tower with feisty Fawn 7.04  Fine so far.  Tried to find a modem and hit the wall.  I am on dial up, and after most quit laughing, one fellow advised an external serial modem.  Fine, got that.  Actiontec EX560LKU   Hooked this modem up, finally found the place to at least enter my ISP number, and....and...um...where is whatever it is you hit to even try to dial ?  
    The tan blank screen is nice, but is not much help.  I see reference to 'device manager', but can't find it.  The more I look at the threads here, I wonder if this system is not more trouble than it is worth.  Ant help would be appreciated, but at this point I am thinking my old clean copy of 98se is looking real good now....

I've been on ADSL for the last two years, but was on dial-up for the previous ten years.My recollections are a bit dim, but may help you.

You need a PPP dialler, such as gnome-ppp, kppp or wvdial.

You need to connect the modem to a serial port, and know how Linux sees the port.

Linux will see it as /dev/ttyS*n* where *n* is a digit (usually 0 <= *n* < 4).

I think you test this by watching the modem's front panel lights while you send it a "wake-up" command from the AT command set, something like this:
```
echo "ATZ" > /dev/ttyS0
```

The dialler programs generally like to use /dev/modem, so link to your serial port to the modem, If the serial port is /dev/ttyS0 you'd do this:
```
ln -s /dev/ttyS0 /dev/modem
```

Then within the dialler program, you need to set up the number to dial and a few parameters like your username and password to log in to the ISP.

Try [googling]("http://www.google.com/search?q=linux+dial-up+modem+howto&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") for more nformation, and I'm sure you'll find something useful.


Beef.

---

### Post by bigken on 2008-01-05
why dont you run ubuntu in windows using vmware or virtual pc :)

---

### Post by sleepingdragon on 2008-01-05
I had a solution using kppp, it certainly worked well for me. 

On the command line, use **sudo pppconfig** to set up a new connection. Make note of the "Provider Name" you create, this will be important later. As mentioned earlier, your external modem should be found in */dev/ttyS0*

Make sure kppp is installed and then you can run:

**kppp -c *provider name* &**

e.g.,

**kppp -c btinternet &**

I was able to use this in an autostart item to launch on start-up. You should also find an option in pppconfig to create a *persistent connection*, just in case you lose the connection, that option will reconnect you automatically.

Hope some of that helps. If you get stuck, give me a holler and I'll see if I can assist some more.

---

