---
title: "[SOLVED/INFO] Getting lirc macmini driver to work on Intrepid"
date: 2009-02-22
forum: Apple Hardware Users
---

### Post by jnorth on 2009-02-22
After spending several days tearing my hair out and reinstalling/researching/rebooting/modprobing/changing HAL and UDEV, I figure the least I could do is post in case anyone else has this issue.
I do not claim to be an expert on lirc at all, though I do have quite a bit of *nix experience in general.

Symptoms:

[LIST]
[*]Lirc was working in Intrepid up until some updates sometime during the lat 3 weeks.  I did a system update and my remote no longer worked.  After the update, no irw, no /dev/usb/hiddev0, no nothing.
[*]A reinstall with all updates has same symptoms, PLUS, X/gdm grabs the input
[*]The device appears as a keyboard input instead of a HID input as it should.  You may be able to deal with this using the dev/input lirc driver, but that drops the number of available commands - since I use a Harmony remote with many functions learned, I have to have the macmini driver.
[/LIST]
Causes/Solutions that worked for me - I've narrowed it down to the following list of what I had to do from a fresh install after figuring this out.  Maybe it seems simple but it was a living hell for me.

[LIST]
[*]Apparently someone decided to arbitrarily roll out mouseemu in an update.  This was the hardest part for me to find.  This package is for touchpad functionality - this is a mac mini with no touchpad, so I don't need it - remove it, just watch your dependencies and make sure it doesn't break anything else on your install - it didn't on mine but YMMV.```
sudo dpkg --purge mouseemu
```
[*]Appleir kernel driver gets in the way.  If you use it, good luck, plus you have to use the dev/input driver which limits the amount of functions you can use.  I swear I had to have it enabled on prior kernels, but it breaks **** now.  So, let's kill it off:```
sudo echo "blacklist appleir" >> /etc/modprobe.d/blacklist
```
[*]Apparently HID devices were (accidentally???) disabled in quirks in a recent update?  I dunno, but you have to re-enable it or you'll never get a proper /dev/usb/hiddev0 device to use.  So:```
sudo echo "options usbhid quirks=0x05ac:0x8240:0x10" >> /etc/modprobe.d/options
```
[*]Now set up your lirc again according to the many other tutorials out there.  Use /dev/usb/hiddev0 for your REMOTE_DEVICE line in(or if you have others use the one that is your IR reciever, still most likely hiddev0) and macmini for your REMOTE_DRIVER line.
[/LIST]
Good luck - hope this helps someone.

---

### Post by cyberdork33 on 2009-02-23
I think this issue validates a bug report in launchpad. I would suggest that this is reported there if it already isn't (you might also want to test Jaunty).

---

### Post by jnorth on 2009-02-23
Gladly - I'm searching for that bug now, any chance you have the # offhand?  I'll find it though.

Re: testing with Jaunty, I'll give it a shot in the next week or so when I get a new usb drive that I can do testing with on the mini hardware, my girl will kill me if I take down the frontend again :)

---

### Post by cyberdork33 on 2009-02-23
> **jnorth said:**
> 
Re: testing with Jaunty, I'll give it a shot in the next week or so when I get a new usb drive that I can do testing with on the mini hardware, my girl will kill me if I take down the frontend again :)
hehe. been there.

I don't want to ask too much of you, but if you have spare time, a wiki page for the MacMini hardware could use a lot of help. If you don't want to that is fine too, I just try to ask when users with certain hardware come into the forums. Bug report is more important though :)

I don't know of a bug myself, though I know there are at least some old appleir bugs int here somewhere, but they may not be related.

---

