---
title: "wireless/network problems"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by RandomConjecture on 2006-08-09
I feel dumb, because this should be really easy to set up. I know I'm missing something simple, but can't for the life of me figure it out.

I just moved to a new apartment, which already has a wireless network set up. My roommate's computer works just fine.

I connected to her wireless network using kwifimanager (wasn't sure how to do it manually). It says that it's connected, but there is no Local IP. If I restart networking, it says there are no DHCP offers. If I ping the router, it says 'Network is unreachable'. 

I'm running Xubuntu, Breezy Badger. My network interfaces file is:

auto ath0
iface ath0 inet dhcp

(I also added iface lo inet loopback, because I wasn't sure whether I was supposed to have that or not. It didn't change anything.)


Sorry to ask such a dumb question...I wasn't entirely sure where to post it.

---

### Post by wieman01 on 2006-08-09
If you have not enabled security your "interfaces" file should look like this:
> auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid <your_essid>
Restart network (terminal):
> sudo /etc/init.d/networking restart
That's it. If you need any kind of security let us know (e.g. WEP, WPA, etc.). 

Is DHCP the right setting?

---

### Post by RandomConjecture on 2006-08-09
What exactly is an essid? I'd always just connected with kwifimanager before, and it did everything automatically. I know nothing about wireless.

The network has a key (64-bit), but I'm not sure what kind. I assume WEP, that's the usual, right?

---

### Post by wieman01 on 2006-08-09
ESSID is your wireless ID... The name of your wireless network.

Yes, should be a WEP network. Actually there is a nice "wireless networking" tool under Gnome which you can use to configure your network. You'll find it in the menu although I cannot tell you where it is as I am using KDE.

I think your wireless network administrator (your mate) should help you set it up because it sounds as if your problem are more related to the fact that wireless is new to you? No offense of course. :-)

Wireless networking with WEP is very similar to Windows... So somebody with Windows experience should be able to set it up for you (using the mentioned tool).

---

### Post by RandomConjecture on 2006-08-09
I thought that's what an essid was...just checking.

Well, I'd love to use a wireless config tool, but I'm running Xubuntu, and there isn't a graphical tool. 

I know how to setup a wireless network in Windows...and I definitely know more about wireless than my roommate!

Actually, I did setup the network with the key in kwifimanager. 

I'd love to download one of the KDE or Gnome network tools, but I  doubt there's a CAT-5 cable anywhere in this house. I s'pose I could unplug the router, but that just seems like a lot of trouble.

---

### Post by wieman01 on 2006-08-09
Ok, I got it. :-)

To enable WEP you need to have the following settings:
> auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid <your_essid>
wireless-key <your_wep_key>

Then restart the network:
> sudo /etc/init.d/networking restart
I am not sure if a 64-bit WEP encryption will be a problem. Normally we use 128-bit and I have heard that 64-bit can be a problem. Not sure though, perhaps you can try and let us know if it works out.

---

### Post by RandomConjecture on 2006-08-09
Thanks for all your help...but still no luck...

Part of what it says when I do /etc/init.d/networking restart is:

send_packet: Network is unreachable
Error for wireless request "Set Encode" (8B2A): invalid argument "<my_key>"

Any thoughts?

---

### Post by wieman01 on 2006-08-09
I am sorry... you need to drop the <>... Just put in the name / key of your network.

---

### Post by RandomConjecture on 2006-08-09
lol, I didn't actually put in the carrots!

---

### Post by RandomConjecture on 2006-08-09
Uh, here's a thought:

One of the other things it says when it restarts networking is "send_packet: Please consult README file regarding broadcast address."

I note this because it says "DHCPDISCOVER on ath0 to 255.255.255.255." 

Doesn't it usually discover on 255.255.255.0?

---

### Post by wieman01 on 2006-08-09
"DHCPDISCOVER on ath0 to 255.255.255.255" is correct in fact. That's the way DHCP connects.

What happens if you restart the computer? In case the system hangs press "crtl + c" to continue.

---

### Post by RandomConjecture on 2006-08-09
The computer restarts fine, if that's what you mean. Doesn't change the status of the network stuff.

---

### Post by wieman01 on 2006-08-10
The stanza is definitely correct. Can you post the output of these terminal commands:
> iwconfig
> ifconfig

Are you sure the network is running on DHCP?

---

### Post by pterandon on 2006-08-13
Hello, I'd like to chime in to say that this thread oughtta be stick-ied, it's so helpful. :KS    Or somehow make it higher on google's page ranking! ;) 

The only caveat I'd ad is that a hard power down & up via "reboot" was necessary to get it to work.

---

### Post by wieman01 on 2006-08-14
> **pterandon said:**
> Hello, I'd like to chime in to say that this thread oughtta be stick-ied, it's so helpful. :KS    Or somehow make it higher on google's page ranking! ;) 

The only caveat I'd ad is that a hard power down & up via "reboot" was necessary to get it to work.

Glad to hear it was helpful. And yes, for a reason unknown to me some users have to reboot their computers for this to take effect. That's the last resort if **"sudo /etc/init.d/networking restart"** does not do the job.

If you want to try out WPA or WPA2 you can try this:

**_WPA2:_**
[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

**_WPA2 & WPA:_**
[http://www.ubuntuforums.org/showthread.php?t=225290&page=11]("http://www.ubuntuforums.org/showthread.php?t=225290&page=11")

---

