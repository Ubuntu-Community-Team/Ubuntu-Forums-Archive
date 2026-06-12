---
title: "wireless: had it, then lost it!"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2007-09-10
OK, this is a strange problem.  I installed Feisty on my laptop, and was able to connect to my wireless network on the first try.  I then brought my laptop to school, and tried to connect to the network there, and I can't click on "Connect" when selecting "Connect to Other Wireless Networks".  The box is greyed out.  Both my home network and my school network don't require a WEP key, but they don't broadcast the network name (i.e. you have to type in the name, etc.).  

Thanks for your help!

---

### Post by mikeyphi on 2007-09-10
Have you tried "Enable roaming mode" in the Network settings GUI?

---

### Post by limberlegs on 2007-09-10
Yeah, roaming is enabled.  It's weird, because everything was working just fine at home.  The router in my office is event the same brand! (Linksys).

I'm guessing it might have something to do with the network card holding on to the old IP address, but I'm not really sure.

Any thoughts?

---

### Post by mikeyphi on 2007-09-10
Have you tried to put the ESSID in manually?

---

### Post by limberlegs on 2007-09-10
Yeah, tried that too.  It doesn't allow me to click "connect" either.

---

### Post by limberlegs on 2007-09-10
OK, this is weird.  I am at home now, and I can connect to the wireless network just fine.  The process goes as follows:

I log in, and click on the network icon in the top right corner.

I click on "Connect to Other Wireless Network"

I type in the name of my network, and click connect, and everything is just fine.

When I was at school earlier today, I did the exact same thing, and the "connect" button remained grey and wouldn't allow me to click it when I typed in the network name.  

Any thoughts?

Thanks for your help!

---

### Post by limberlegs on 2007-09-11
OK, one thought just occurred to me.  I think the router in my office uses wireless-G, and my laptop is wireless-B.  Would this cause these problems?

Also, how do I have the computer automatically connect to a list of preferred networks?  For instance, I don't want to have to manually connect to my home network every time I boot up the computer.  Likewise, if I ever get it working in the office, I would like to just have it connect after booting up.

Any help is greatly appreciated!

---

### Post by LT1Caprice57L on 2007-09-11
That *shouldn't* cause any issues, but shouldn't and won't are 2 different things.

My Linksys 802.11b card in the desktop won't communicate with my Linksys 802.11g router, but WILL communicate with my Apple 802.11n router.  Irony, eh?  The laptop's wireless "card", a LAN-Express 802.11g, works with everything I've tried to connect it to.

You didn't hit the WLAN switch by mistake did you?  I know that seems stupid, but I just spent 5 minutes trying to figure out why my apple router "dropped out" and didn't come back...to look down and find it was the WLAN switch on the laptop which was the culprit.

EDIT: Mine does connect to a list of preferred networks, always has since I installed Ubuntu.

---

### Post by limberlegs on 2007-09-11
Yeah, I am pretty sure the WLAN switch was on.  I had it working perfectly at home, but when I got to the office, it didn't work at all.  

I'm also not sure why the network list isn't sticking with each subsequent log in.   I have read about other wireless network managers for ubuntu that might work better.  Could this be the problem?  Anyone want to suggest a better wireless network manager than the one that comes preinstalled with ubuntu?

Thanks for all of your replies!

---

### Post by limberlegs on 2007-09-11
OK, I'm in my office now, and I am no longer having the greyed out box problem.  I can type in whatever network I want, and I can click "connect."  But I still can't connect to the network.  I have confirmed that it is indeed a linksys wireless b router in my office, almost identical to my router at home (which works perfectly).  

Could this possibly have something to do with my IP address not refreshing?

---

### Post by limberlegs on 2007-09-11
UPDATE: OK, this is odd. I changed the office router settings so that the SSID is broadcasting, and now I'm able to connect to the router.  I still had to type in the name of the network; it didn't detect it automatically (like it should, if I have "roaming" enabled, right?)

Is there any reason these things are so sporadic?  Is there a better way to monitor what is actually going on?  I feel like I'm doing some sort of computer voodoo to get things working...

---

