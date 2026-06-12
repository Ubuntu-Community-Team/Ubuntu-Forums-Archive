---
title: "Network settings not being saved"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by medley on 2007-08-08
I know this has been asked 50,000 times, but the threads seem to die without resolution. Why the hell does network manager keep screwing up my wireless settings???!!!

If I configure the wireless interface with the essid, key, etc and save it, it'll tell me that the 'default gateway is invalid'. I go to that tab, enter the router IP address and the wireless interface, save and the interface config is wiped out.

This is ridiculous. What a mickey mouse piece of software. I've been wrestling with this for days. Wcid doesn't work for me (I get 'no profile found'; don't even get me started on the lack of meaningful error messages). I've been using Kubuntu for a year, and every time I have to set up a new machine with wireless I wonder why I've even bothered. I usually have to wrestle with it for a good couple of days each time.

I know my driver is OK because I did have it working once until I decided to reboot and make sure that it came up properly again. This shouldn't be this difficult. I get the settings saved (I verify in /etc/network/interfaces) and then the next time I go into network manager to fix the lack of DNS, the damn program wipes out my interface settings.

(edit)
Also, everytime I change the default gateway to my router (from 0.0.0.0 and specify wlan0 as the interface) and save it, when I come back to it, the default gateway is invariably reset to 0.0.0.0 and eth0 as the interface. Grrr!
(end edit)

Sorry for the rant; I'm fed up. I love Ubuntu when it works, but am ready to throw it out every time I go through this kind of nonsense.

Please help.

---

### Post by Hospadar on 2007-08-08
Well if you don't want network manager to wipe your settings, the easiest thing to do is simply remove it.
```
sudo apt-get remove network-manager 
```
and then just edit your interfaces file manually.

I'm not sure why it's wiping out your setting (I assume you already have it set to not automatically detect/set up networking, because that would wipe your settings for sure) but simply getting rid of it all together should take care of the problem.

For kde it might be a different program that actually handles the wireless, but i think it's network manager.  you may also need/want to disable/remove any programs like wifi-radar that scan for networks and such, there is probably some kde applet like that which you may have to hunt down.

---

### Post by medley on 2007-08-08
> **Hospadar said:**
> Well if you don't want network manager to wipe your settings, the easiest thing to do is simply remove it.
```
sudo apt-get remove network-manager 
```
and then just edit your interfaces file manually.

I'm not sure why it's wiping out your setting (I assume you already have it set to not automatically detect/set up networking, because that would wipe your settings for sure) but simply getting rid of it all together should take care of the problem.

For kde it might be a different program that actually handles the wireless, but i think it's network manager.  you may also need/want to disable/remove any programs like wifi-radar that scan for networks and such, there is probably some kde applet like that which you may have to hunt down.

Thanks for responding. Can you steer me to some help on how to edit my interfaces manually?

Thanks again.

---

### Post by medley on 2007-08-08
> **medley said:**
> I know this has been asked 50,000 times, but the threads seem to die without resolution. Why the hell does network manager keep screwing up my wireless settings???!!!

If I configure the wireless interface with the essid, key, etc and save it, it'll tell me that the 'default gateway is invalid'. I go to that tab, enter the router IP address and the wireless interface, save and the interface config is wiped out.

This is ridiculous. What a mickey mouse piece of software. I've been wrestling with this for days. Wcid doesn't work for me (I get 'no profile found'; don't even get me started on the lack of meaningful error messages). I've been using Kubuntu for a year, and every time I have to set up a new machine with wireless I wonder why I've even bothered. I usually have to wrestle with it for a good couple of days each time.

I know my driver is OK because I did have it working once until I decided to reboot and make sure that it came up properly again. This shouldn't be this difficult. I get the settings saved (I verify in /etc/network/interfaces) and then the next time I go into network manager to fix the lack of DNS, the damn program wipes out my interface settings.

(edit)
Also, everytime I change the default gateway to my router (from 0.0.0.0 and specify wlan0 as the interface) and save it, when I come back to it, the default gateway is invariably reset to 0.0.0.0 and eth0 as the interface. Grrr!
(end edit)

Sorry for the rant; I'm fed up. I love Ubuntu when it works, but am ready to throw it out every time I go through this kind of nonsense.

Please help.

Also, why, when I do 'iwconfig' does it show the essid as "default" rather than what I specified in network manager? In fact, if I check the essid in network manager, it shows the correct essid (which is NOT 'default'). Also in /etc/network/interfaces, the settings are correct for wlan0. Where else might the incorrect settings be coming from??!!

---

### Post by gigaferz on 2007-08-27
i had a similar problem, the settings for wlan0 are  in /etc/network/interfaces, i just added auto wlan0"

well it didnt work...it worked on edgy.....

---

