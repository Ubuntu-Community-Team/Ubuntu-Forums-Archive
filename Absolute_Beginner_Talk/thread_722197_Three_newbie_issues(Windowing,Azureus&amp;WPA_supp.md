---
title: "Three newbie issues(Windowing,Azureus&amp;WPA_supplicant)"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Zarok on 2008-03-12
Ok, I just installed Ubuntu on my Asus Eee PC and it works quite well with this. I just ran into a few random problems setting my stuff up.

1. Windowing. If I have one window on top of the other, and I click the one below it, it turns active. I want it to move to the top of the previously top window too. I can't find where I could set this up so clicking would bring it on top - I can only find an option that moves it on top if I point at it for a certain period of time. ALT+TAB changes it like I want to ofc, but I'd like to do it with a click also.

2. Azureus. If I use Firefox's open file in : Azureus, it always opens a new Azureus client. I want it to add the torrent to an already running client if I have one, not open a new one every time. I can't find an option that would allow only 1 instance of Azureus at a time.

And finally

3, Connecting to a WPA AP with WPA_supplicant. I configged WPA-supplicant, added my network info there, I created a script to run on startup that runs it, but... I can't manage to automate dhclient for it, so it doesn't get an ip address automatically.  I also tried using /etc/network/interfaces to run the wpa_supplicant with 
auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -c /etc/wpa_supplicant.conf -w -Dmadwifi -iath0 -dd
post-down killall -q wpa_supplicant
, doesn't work, it runs the wpa_supplicant like it should, but doesn't get the ip.

I made a script wlanboot.sh that runs on startup via the rc.local file, that runs
#!/bin/sh
wpa_supplicant -c /etc/wpa_supplicant.conf -w -Dmadwifi -iath0 -dd
dhclient ath0
but it just won't acquire the IP, I have to do it manually after every reboot with sudo dhclient ath0 to get the ip address.

So. If you could help me with these three problems, I could really start enjoying this rather than struggle with configs, pretty much everything other than those 3 problems I managed to solve myself and got everything running like I want to. :)

---

### Post by handydan918 on 2008-03-12
1) The desired behavior you describe is the default for KDE....

2)Can't help. Don't know Bittorrent clients well enough.

3) Have you tried adding 'sudo' to your script? I think there is a way to make a script run with root privileges without manually entering a password, too....myabe someone else can weigh in here.

---

### Post by Joeb454 on 2008-03-12
You can run things as sudo by editing the /etc/sudoers file. Though I would highly recommend against doing this unless you have experience in using vi/vim etc. As it can easily break your system (I know - I've done it)

---

### Post by Zarok on 2008-03-12
> **handydan918 said:**
> 1) The desired behavior you describe is the default for KDE....

...but doesn't the basic ubuntu run gnome? Ah well, I actually found alot of benefits that the windows system is like so that it doesn't automatically put windows I click on top, unless I click taskbar or alt+tab. So that's ok, I actually like this better after a while :)
[QUOTE=handydan918]
3) Have you tried adding 'sudo' to your script? I think there is a way to make a script run with root privileges without manually entering a password, too....myabe someone else can weigh in here.[/QUOTE]
Yup, that didn't help. A friend also suggested adding kill NetworkManager before the dhclient, didn't help either sadly. I think the problem might be the delay wpa_supplicant has before it connects to my AP, I think it DOES run the dhclient, but the wpa_supplicant takes a while to connect for some odd reason, so dhclient times out before the AP is connected. I looked at the debug info for the wpa_supplicant, for some odd reason it skips my Wlan with SSID mismatch message a few times, and then eventually gives a :
Try to find WPA-enabled AP
0: 00:13:49:fe:a1:ab ssid='Jensen' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
selected based on WPA IE
selected WPA AP 00:13:49:fe:a1:ab ssid='Jensen'
. The start on my wpa_supplicant.conf is:
 network={
ssid="Jensen"

So it DOES have the right SSID setup. Wonder why it skips it due to SSID mismatch a few times until it gives that and connects?

---

