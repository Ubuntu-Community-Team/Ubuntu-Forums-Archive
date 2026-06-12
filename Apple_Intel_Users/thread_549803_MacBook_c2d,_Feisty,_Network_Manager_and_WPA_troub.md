---
title: "MacBook c2d, Feisty, Network Manager and WPA troubles"
date: 2007-09-13
forum: Apple Intel Users
---

### Post by kry10 on 2007-09-13
Hi, everyone:

I just got a new MacBook, installed Feisty on it and, for the most part, it's working great. However, I am having problems connecting to my wireless network via WPA.

I installed the MadWiFi drivers with apparent success. The network manager shows about eight different networks in my neighborhood (except for mine, as I don't broadcast my SSID). It even discovered a couple of wide-open networks, which I could connect to and surf without problems.

Next, I tried to connect to my network. I clicked on the NM icon, and selected Connect to Other Network. I enter my SSID, select "WPA Personal" as Wireless Security, and enter my passphrase. The icon then animates and indicates that it's trying to connect to my network, but never succeeds.

So, after checking through the wiki, I find some suggestions about using wpa_supplicant. I created a configuration file then started it using the following command:

sudo wpa_supplicant -iath0 -c /etc/wpa_supplicant.conf -Dmadwifi -w -d

BTW, at this point, my wired connection is still, well, connected (this technique doesn't work if I start with it unplugged). Then, I unplug the cable. wpa_supplicant shows a bunch of debugging information and indicates that it's connected to my WAP. Great. However, NM says that I'm connected to one of the other open networks, not mine. However, I'm clearly connected to my WAP, as I can access my internal network, etc.

So, I can get connected to my access point, but only via a command prompt, and Network Manager shows the incorrect network. Not  the elegant solution I was hoping for :)

Does anyone have any suggestions on how I should proceed from here? Thanks in advance!

Mark

---

### Post by cyberdork33 on 2007-09-13
> **kry10 said:**
> I just got a new MacBook, installed Feisty on it and, for the most part, it's working great. However, I am having problems connecting to my wireless network via WPA.

Firstly, hiding your SSID does nothing to help security, and instead usually just creates connection problems. It is very easy to determine your SSID even without it being "broadcast".

Doing things manually bypasses n-m, so just disable it as it will probably just end up disconnecting you every so often since it is confused.

---

### Post by kry10 on 2007-09-13
> **cyberdork33 said:**
> Firstly, hiding your SSID does nothing to help security, and instead usually just creates connection problems. It is very easy to determine your SSID even without it being "broadcast".

Yeah, I know, but I'm paranoid :) In any case, I tried turning SSID broadcasting back on, and it still wouldn't work

> **cyberdork33 said:**
> Doing things manually bypasses n-m, so just disable it as it will probably just end up disconnecting you every so often since it is confused.

That may be my only alternative at this point. Too bad, as I really like the NM applet - if it could work, it'd make traveling with my notebook so much easier.

I have a Live CD of the latest Gutsy. Maybe I'll try that out tonight when I get home. Thanks!

---

