---
title: "'ifconfig wlan0 up' gives 'no buffer space' error"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by RostokMcSpoons on 2008-01-06
Hi,

I'm trying to get my TP-Link WN321G Usb Wifi connection to work... I've already got the rt73 driver installed, but when I try and start it using the ifconfig command, I always get this 'no buffer space' error.

I'm an absolute noob, so I've got no idea what's wrong  :(
I've searched t'web and found nothing that seems a guaranteed fix, or even vaguely pertinent (though I'm sure that's as much due to me not knowing what I should search for :/

Anyway... I'm running a clean install of 7.10 on an A64 3700+ with a newly formatted 120gb hd, and 1gb ram, and unless I can get wifi working, my linux experiment will be very short-lived!  So I'd welcome some help :)


edit:  ok, I've made some progress... I found a 'solution' that talked about installing an rt73usb.bin file into the lib\firmware directory.  I followed the instructions but discovered it was already there.  But just to see what happened I also did this:

sudo rmmod rt73.usb
sudo modprobe rt73usb

Strange that I accidentally used rt73.usb instead of rt73usb in the rmmod, but it still worked!  
Anyway... the happy upshot of this is the 'ifconfig wlan0 up' command completed successfully :)
The problem I now have is that in Network Tools I have 'wlan0' which isn't showing any details... but 'wlan0:Avahi' has settings (MTU etc etc).   Is that wrong?  
I still have no active internet, but I'm not sure if my security is the problem ... my WEP key is in the form 'EC3ED...' presumably that's Hex rather than ASCII?  I've tried with WEP disabled in the router, no joy so far.
Can I also ask what commands can I run to scan for access points?

Any help you can provide is much appreciated :)

---

### Post by seachnasaigh on 2008-01-07
hit a terminal and type at the prompt
```
ifconfig -a
```

See what you get. Your wlan0 should have an IP if it's connected to your router.

Yes, your WEP key looks like hex rather than ASCII. You should be able to put that in your config for that interface by prepending "0x" to the key to specify that it's hex. For example, if your key is e34fc1012 you'd type 0xe34fc1012 in the box for the wep key.

I wouldn't turn off the WEP encryption on your router to solve the problem if I were you. It's not necessary; I run a hex key encrypted WEP on my home router and it works just fine with Ubuntu.

Good luck!

--ckr

---

