---
title: "Cannot for the life of me connect to the internet!!!"
date: 2007-06-14
forum: Apple Intel Users
---

### Post by user1397 on 2007-06-14
In OS X, I cannot connect to my home network.  I have a core duo macbook, with airport express, and trying to connect to my linksys wireless-g router, which I have set up with WPA2 wireless security.

I have literally tried everything, from the network diagnostics, to restarting my router and modem, to pressing the "renew DHCP lease" 
button in the system preferences...I just don't know what to do.

Does anyone know the terminal command for renewing the DHCP lease?

It was working fine till about a week ago, and no amount of restarts of any device, including the macbook, has made the internet work.

Any suggestions?

---

### Post by Torajima on 2007-06-14
If it stopped working a week ago, what happened a week ago? Did you have a thunderstorm or power outage? I like to think Linksys is better than the cheaper routers, but I've had both Dlinks and NetGears lock up after a power outage, forcing me to use a paper clip on them and re-enter all their settings.

But if other devices are working fine with the router, it could well be a Mac problem. There are two different places to enter internet settings... WEP or WPA passwords have to be entered up at the menu bar (under the wifi icon), and other internet settings need to be entered under System Preferences.

And if you try to connect with Safari and it fails, it should walk thru the process of repairing your connection.

---

### Post by user1397 on 2007-06-14
> **Torajima said:**
> If it stopped working a week ago, what happened a week ago? Did you have a thunderstorm or power outage? I like to think Linksys is better than the cheaper routers, but I've had both Dlinks and NetGears lock up after a power outage, forcing me to use a paper clip on them and re-enter all their settings.

But if other devices are working fine with the router, it could well be a Mac problem. There are two different places to enter internet settings... WEP or WPA passwords have to be entered up at the menu bar (under the wifi icon), and other internet settings need to be entered under System Preferences.

And if you try to connect with Safari and it fails, it should walk thru the process of repairing your connection.Thanks for the reply.

Nope, no power outages or anything, it just randomly stopped working, though I've had this problem before several times throughout the year, and it always seems to fix itself somehow, like one day it'll start working again.

But it has never been non-functional for this long.

I have checked that the passwords match up both in the menu bar and in the system prefs, and I have tried the network diagnostics in safari many times, correctly following all the steps.

Any other suggestions?

---

### Post by Torajima on 2007-06-14
> **ubuntuman001 said:**
> 
Any other suggestions?

Have you confirmed it is an OSX problem? Is your wireless working in Ubuntu? Is your wired connection working?

---

### Post by user1397 on 2007-06-14
> **Torajima said:**
> Have you confirmed it is an OSX problem? Is your wireless working in Ubuntu? Is your wired connection working?It must be an OSX problem, or an airport problem, because my ethernet works fine with my windows computer, and my wireless works fine with my windows laptop.

I wanted to try an ubuntu live cd with my macbook, and had hoped that I could use the internet while using the live cd...

Thanks for staying with me.

---

### Post by Torajima on 2007-06-14
Under your Network Prefs, do you have your location set to automatic?

If so, and you took your laptop to work or a coffee shop, your settings might have been changed.

You should create a new location, and enter the neccessary settings there (save when done).

Another thing to try would be to set up your mac laptop and windows laptop side by side and try to figure out exactly where the settings differ.

---

### Post by user1397 on 2007-06-14
> **Torajima said:**
> Under your Network Prefs, do you have your location set to automatic?

If so, and you took your laptop to work or a coffee shop, your settings might have been changed.

You should create a new location, and enter the neccessary settings there (save when done).

Another thing to try would be to set up your mac laptop and windows laptop side by side and try to figure out exactly where the settings differ.I have it set to automatic, and yes I did take it to a friend's house recently, which might have messed everything up.

Either way, setting up a new location doesn't work.

I did notice that on my windows laptop the security setting is set to WPA-PSK which means pre-shared key, yet in my macbook, I only have the options of WPA2 Personal and WPA2 Enterprise.  I'm going to see if WPA2 Enterprise is the one, as I have it set to personal right now.

thanks again.

edit: hmm, apparently enterprise has nothing to do with home networks :)

it has to be personal, but it just doesn't work.

Also if I have not pointed this out before, it *looks* like it connects, because I click on my network and it turns black, signaling that it is connected, and all bars are there.  So I guess it is connecting but maybe it isn't renewing the DHCP number.

Is there some kind of terminal command that could help us diagnose this problem?  (mac commands should be similar or exactly like linux commands according to my understanding)

---

### Post by Torajima on 2007-06-14
> **ubuntuman001 said:**
> I
Also if I have not pointed this out before, it *looks* like it connects, because I click on my network and it turns black, signaling that it is connected, and all bars are there.  So I guess it is connecting but maybe it isn't renewing the DHCP number.

It could be your DNS Servers. Have you entered them manually, or do they get supplied via DHCP?

If your DNS servers are wrong, you could well be connected, but not be able to access the web.

You could try the command below in the terminal, and see what happens. Substitute the address of your router for "192.168.1.1"

[COLOR="Navy"]ping -c 10 192.168.1.1[/COLOR]

---

### Post by user1397 on 2007-06-14
> **Torajima said:**
> It could be your DNS Servers. Have you entered them manually, or do they get supplied via DHCP?

If your DNS servers are wrong, you could well be connected, but not be able to access the web.

You could try the command below in the terminal, and see what happens. Substitute the address of your router for "192.168.1.1"

[COLOR=Navy]ping -c 10 192.168.1.1[/COLOR]I don't exactly know what DNS servers are, but I do know that everything is configured via DHCP.

I tried that command, this is what I get:

```
$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1): 56 data bytes
ping: sendto: No route to host *(this line is repeated 10 times)*

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 0 packets received, 100% packet loss
$
```

---

### Post by Torajima on 2007-06-14
> **ubuntuman001 said:**
> I don't exactly know what DNS servers are, but I do know that everything is configured via DHCP.

Under Network Settings choose Airport and then TCP/IP. There should be a box for DNS servers. Is there anything listed there?

> I tried that command, this is what I get:

```
$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1): 56 data bytes
ping: sendto: No route to host *(this line is repeated 10 times)*

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 0 packets received, 100% packet loss
$
```

Is your router at 192.168.1.1? If not, you need do a ping using your own router address. If that indeed is the correct address, your Mac isn't seeing the router at all.

---

### Post by user1397 on 2007-06-14
> **Torajima said:**
> Under Network Settings choose Airport and then TCP/IP. There should be a box for DNS servers. Is there anything listed there?



Is your router at 192.168.1.1? If not, you need do a ping using your own router address. If that indeed is the correct address, your Mac isn't seeing the router at all.
No, there is nothing listed in that DNS servers box.

That indeed is my router's address, so I guess it isn't seeing my router at all like you say...but what the hell?  I have restarted my router many times (by unplugging the power chord, waiting 10 seconds, and plugging it back in), but still no go.

Thanks you so much for constantly being helpful.

---

### Post by Torajima on 2007-06-14
> **ubuntuman001 said:**
> No, there is nothing listed in that DNS servers box.

That indeed is my router's address, so I guess it isn't seeing my router at all like you say...but what the hell?  I have restarted my router many times (by unplugging the power chord, waiting 10 seconds, and plugging it back in), but still no go.

Thanks you so much for constantly being helpful.

Well, if your PC laptop can access the router there is nothing wrong with your router (thus no reason to reboot router).

I would guess that either something is wrong with your airport card or you have mistyped a setting somewhere. You could always turn off WPA for the time being (on both router and Mac) and see if you connect. If you can connect while it's off, you know that your settings for WPA must have been wrong.

---

### Post by user1397 on 2007-06-14
> **Torajima said:**
> Well, if your PC laptop can access the router there is nothing wrong with your router (thus no reason to reboot router).

I would guess that either something is wrong with your airport card or you have mistyped a setting somewhere. You could always turn off WPA for the time being (on both router and Mac) and see if you connect. If you can connect while it's off, you know that your settings for WPA must have been wrong.
Somehow, it works now!

All I did was I closed the lid in frustration, so it went in standby mode, then after a while I opened it and it started working. I still see that nothing is in the DNS servers box, so I guess it had nothing to do with that.

Everything's working normally now.

Thanks for all your help, I really appreciate it.

---

### Post by wieman01 on 2007-06-15
Should you have the same problem again, do this from command line:
> sudo gedit /etc/resolv.conf
Then add this line:
> nameserver 192.168.1.1
...assuming that 192.168.1.1 is your router's IP address.

For some reason this frequently happens if you switch between various DHCP networks. Sometimes the DNS settings aren't updated, so although the connection to the router is fine, DNS would fail.

---

### Post by user1397 on 2007-06-15
> **wieman01 said:**
> Should you have the same problem again, do this from command line:

Then add this line:

...assuming that 192.168.1.1 is your router's IP address.

For some reason this frequently happens if you switch between various DHCP networks. Sometimes the DNS settings aren't updated, so although the connection to the router is fine, DNS would fail.Ah, thanks for the info, I appreciate it.

---

### Post by user1397 on 2007-07-06
Yo, I'm getting this problem again...I tried to type in the mac os x terminal the command you said: ```
sudo open /etc/resolv.conf
```(i put "open" because that is the default command for opening text files on a mac, using the program "textedit")
but it doesn't work.

when i execute that command, i get: ```
open[409] No such file: /etc/resolv.conf
```which is weird because when i cd to /etc, and i type ls, i see that file there...

---

### Post by user1397 on 2007-07-08
bump

---

### Post by cyberdork33 on 2007-07-08
It looks like you are looking for support with OSX... You may have better luck somewhere else.

---

### Post by user1397 on 2007-07-08
> **cyberdork33 said:**
> It looks like you are looking for support with OSX... You may have better luck somewhere else.well, i just wanted to see if any willing os x users would help; I'm trying all my resources at the moment to identify this problem...

basically, if you don't want to help, then don't; and if you do, then be my guest...

---

### Post by user1397 on 2007-07-08
> **wieman01 said:**
> Should you have the same problem again, do this from command line:

Then add this line:

...assuming that 192.168.1.1 is your router's IP address.

For some reason this frequently happens if you switch between various DHCP networks. Sometimes the DNS settings aren't updated, so although the connection to the router is fine, DNS would fail.I finally succeeded in doing this, though I had to resort to using vim, but it finally worked.

thank you very much!!!

---

### Post by cyberdork33 on 2007-07-08
> **ubuntuman001 said:**
> well, i just wanted to see if any willing os x users would help; I'm trying all my resources at the moment to identify this problem...

basically, if you don't want to help, then don't; and if you do, then be my guest...

I wasn't telling you to go away. I was offering some advice since nobody seemed to be able to help you.

---

### Post by user1397 on 2007-07-08
> **cyberdork33 said:**
> I wasn't telling you to go away. I was offering some advice since nobody seemed to be able to help you.i know, i know...no hard feelings.

---

