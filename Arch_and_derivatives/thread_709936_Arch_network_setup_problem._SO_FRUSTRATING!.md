---
title: "Arch network setup problem. SO FRUSTRATING!"
date: 2008-02-27
forum: Arch and derivatives
---

### Post by Misbah on 2008-02-27
Ok, so I followed the beginners install guide to get a clean base install of arch. When i went to ping google as it said to, I got the unresolved host error. I referred myself to the wireless network setup guide. This is what I did starting from "Configure the System" in the beginners guide, concerning networking stuff.

under rc.conf I changed my hostname to Hostname="MisbARCH"
I had an additional lo="lo 127.0.0.1" entry that wasn't in the beginner's guide exampl, I left it alone.
I commented out the original eth0=" 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255" and added eth0="dhcp" (this was later changed to wlan0=dhcp after i got the rt2500 drivers installed and wlan popped up inder iwconfig, and upon network start in boot it said 'eth0 no such network device recgonized)
under interfaces I left it alone, but again, I had the additional interface lo interfaces=(lo eth0).
I commented out gateway="default gateway 192.168.0.1" as it said to since I was using DHCP.

under /etc/hosts I changed the listing to read:
127.0.0.1 localhost.localdomain localhost MisbARCH

I know it's kind of silly but I wasn't sure if localhost/localdomain were place holders for info I was supposed to enter, I had no values for those to put in, so I left it alone.

This was when the guide told me to ping, and I returned unresolved host. went to the wireless setup guide.

did hwdetect --show-net and it gave back:
mac80211 rt2500 eeprom93cxb rt2500pci rt2X00pci rt2X00lib rt2X00pci cfg 80211

From my ubuntu install, I know the ralink rt2500 works for my linksys card. so then I:
pacman -S wireless tools
it gave back current local invalid using default C local, up to date, want to install anyways, blah blah, yes yes. Then:
pacman -S rt2500
gave back same as above, installed.

iwconfig and ifconfig -a showed my wlan0

then under rc.conf I set wlan0="dhcp" and INTERFACES=(lo wlan0)

under conf.d/wireless I set
wlan_wlan0="wlan0 essid longhorns key 1234567890" (used the real key ofcourse, not passphrase i presume) and WLAN_INTERFACES=(wlan0)

on boot, when it says starting network, it just times out. I've tried disabling WEP on my router and deleting the "key 1234567890" portion of the wlan_wlan0= value, no fix. what am I doing wrong? I know you guys prob want iwconfig and ifconfig-a and other code outputs, but this is on a seperate desktop with obviously no internet access, so let me know what you need to help me in terms of out put and i'll do it the old fashion way, careful writing down and typing.

what the hell is 'lo' anyways? should i be disabling that. I just want it to work, the arch install was going so smoothly..

---

### Post by fwojciec on 2008-02-28
I'm assuming that "wlan0=dhcp" from your post is, in fact, wlan0="dhcp" (with quotation marks around the "dhcp" part, right?  Second thing -- I think you're supposed to keep the ROUTES=(!gateway) uncommented -- I couldn't find anything about this in your post.

Here is what my set up looks like, for reference -- /etc/rc.conf:
> ath0="dhcp"
INTERFACES=(ath0)
gateway="default gw 192.168.1.1"
ROUTES=(!gateway)
Note that I don't have the "gateway" line commented out and the info in it is correct (the IP address of the router).  Make sure that you have the exclamation mark in the following line though.  Here is /etc/conf.d/wireless:
> wlan_ath0="ath0 essid mmmmmmmm key xxxxxxxxxxxxxxxxxxxxxx"
WLAN_INTERFACES=(ath0)

If that method doesn't work for you you can always try setting wireless up using the [network profiles](http://wiki.archlinux.org/index.php/Network_profiles) method.

EDIT:  You can safely get rid of all the "lo" interface references from /etc/rc.conf -- lo is started directly by initscripts now.

---

### Post by Misbah on 2008-02-28
thanks for the reply, under my rc.conf I have the quotations in the proper place, just typed it incorrectly

wlan0="dhcp"

as for the gateway/routes thing, this is what I did in terms of commenting out:

# gateway="default gw 192.168.0.1"
ROUTES=(!gateway)

I didn't comment out the ROUTES line, because I believe the ! means it's disabled, and it is supposed to be disabled unless using a static IP (according to page 11 of the beginners installation guide). I only commented out the gateway line because it said on the same page that 'if using a static ip set the gateway address to your router's IP. Some DHCP users comment this line out with a #, while others claim it's necessary to set the gateway address with their configuration.'

That's why I commented it out, granted I haven't tried defining my gateway ip which I believe is " 	Default Gateway:  	98.195.200.1" according to my router, or that may be my router's gateway to the ISP? thats the only place in my linksys utility where it says gateway. the routers IP address itself is 192.168.1.1 and is listed as "local IP" under basic setup and "IP address" under local network, the subsection of status in the router utility. I figured I didnt have to define it because ubuntu picked it up.. but then again, arch does ONLY what it tells you to. I'll give it a shot and uncomment it, see what it does. Also to disable lo should i do this:

# lo="lo 127.0.0.1"
INTERFACES (!lo eth0)

(comment it out and ! the lo interface) or just delete it all together from the INTERFACES define section. I appreciate the help. I really want to become an archer.

---

### Post by fwojciec on 2008-02-28
You can safely remove all the references to lo from /etc/rc.conf (also from the INTERFACES line).

As for the routes/gateway -- I guess I would be one of those people who recommend against commenting the gateway line out...  I only have a vague memory of this -- but I remember having a similar problem with network timing out when I went to visit my parents a while back.  Long story short, I needed to set the address of their router correctly in the "gateway" line in spite of the fact that I was trying to connect using dhcp.  In your case the address there should be "192.168.1.1" -- or whatever the address you use to access your router is.

---

### Post by Misbah on 2008-02-28
Well what I did was I just commented out lo="lo 127.0.0.1" ( i started experimenting before I read your post) and commented out INTERFACES=(lo wlan0) and made a new INTERFACES=(wlan0) above it. I'm lazy, and forgetful, this way I can undo my changes with out having to remember.

I did a few combinations:

original setup - boot with gateway commented, ROUTES still at !gateway

boot with gateway uncommented, gateway set at 192.168.1.1, but ROUTES still having !gateway. No go.

boot with gateway uncommented, gateway defined as 192.168.1.1, and removed the ! from ROUTES. No go. It did take much longer to time out, but also gave an additional FAIL on boot/shutdown for some process called SIOCD something, was too fast to see. Figured that's definitely the wrong direction if I'm incurring more ARCH wrath.

I don't know WHAT is wrong. I've played around with it so much I think I understand the logic of it, and I'm sure I'm doing everything right. The hardware is detected, proper drivers, the light on the back of my pci adaptor turns on indicating transmission when it attempts to connect.. I'm thinking it's either something deep (router settings not correct enough or conflicting with arch?) or something stupidly shallow like mispelled ssid or key. the key is only 10 digits because I'm using 64bit wep. but even when I disabled security and removed the key, it didn't work, so I dont know. Really frustrating though, may go on craigslist and find an arch user in the linux forums in the houston area.. because it has me confounded.

Even though i used DHCP, can i define all the settings for arch? maybe it'll work then.. im always assigned the same IP anyways from my router, who knows. I dont really want to use net profiles because as an arch newbie it seems.. harder.. and like I have more room for error. Also it said this way was the preferred way if you only connect to one network, this is a desktop at home that is rarely used so.. it'll only be connecting to one network. AAAAAAAAAAAAAAAAAAAAGHHHHHGHGHH!](*,):mad::confused::???:

The router is set to channel 8, basic key, I type in the key instead of using the s:wirelesspassword thing because I'm not even sure what that is, the only thing i can think of is my timezone set on ARCH doesnt match the routers because I couldnt find the file containing time zones when i was setting up arch under /usr/share/zoneinfo.. just didnt exist on my fresh install with all packages selected..but I doubt that has anything to do with it. Should I use my passphrase instead of the key? Does the key have to be in quotes? I'm not sure if im even connected to the router and just being denied internet access or what, i dont think thats the case, because i cant not only ping websites, cant ping anyone else on the network , the router, myself, or anything.


:cry:

---

### Post by fwojciec on 2008-02-28
One more idea -- I find that sometimes when I make changes to network configuration I have rmmod/modprobe the kernel module for my wifi card before I'm able to connect...  But this might be specific to my card (atheros chipset).

If you can't sort it out my suggestion would be to post on Arch forum -- you're more likely to find someone who has the same hardware that you do so you'll likely get better help.  Good luck in either case.

---

### Post by Misbah on 2008-02-28
my linksys card reads as using the ralink chipset, but I'll try that anyways. Thank you for the help though, I hope I get this sorted out. I posted on the arch forums too, no responses yet, but that usually gets active during the day. we'll see. if not.. i dunno. this thing is too far to hook into the router with ethernet. i'll just have to beat it into submission, or abandon my arch attempt.

---

### Post by Jessehk on 2008-03-01
> **fwojciec said:**
> You can safely remove all the references to lo from /etc/rc.conf (also from the INTERFACES line).

Isn't lo the loopback interface?I don't know as much as I'd like about networking, but I'm pretty sure it's required. [http://en.wikipedia.org/wiki/Loopback#Virtual_Internet_Protocol_Network_Interface](http://en.wikipedia.org/wiki/Loopback#Virtual_Internet_Protocol_Network_Interface)

Like I said, I don't have too much experience (that will hopefully change eventually), but I do know how to configure Arch to connect to a gateway (your router) to connect to a DHCP server and get an IP address.
Please post the networking portions of **/etc/rc.conf** and I'll see if I can fix it for you.

---

### Post by fwojciec on 2008-03-01
> **Jessehk said:**
> Isn't lo the loopback interface?I don't know as much as I'd like about networking, but I'm pretty sure it's required.

Loopback interface is now started by the initscripts directly so it no longer needs to be defined in rc.conf.

---

### Post by Jessehk on 2008-03-01
> **fwojciec said:**
> Loopback interface is now started by the initscripts directly so it no longer needs to be defined in rc.conf.

That's good to know. :) When did that happen?

---

### Post by fwojciec on 2008-03-01
> **Jessehk said:**
> That's good to know. :) When did that happen?

About four months ago -- [http://projects.archlinux.org/git/?p=initscripts.git;a=commit;h=24e468641b51e5e0a05e631d62ad706b5c0a2dd7]("http://projects.archlinux.org/git/?p=initscripts.git;a=commit;h=24e468641b51e5e0a05e631d62ad706b5c0a2dd7")

---

