---
title: "ChromeOS - Trying to dualboot with ubuntu but storage seems almost full?"
date: 2016-06-08
forum: Any Other OS
---

### Post by user1397 on 2016-06-08
My brother said he was interested in seeing if I could install ubuntu alongside ChromeOS on his [new Toshiba Chromebook 2]("https://www.amazon.com/gp/product/B015806LMM/ref=oh_aui_detailpage_o08_s00?ie=UTF8&psc=1").  I looked at the available disk space, and it says it only has a little over 200MB left.  This is on a 16GB SSD.  There is nothing inside his downloads folder, which leads me to believe that all the local storage must be taken up by the OS.

It would seem to me like 16GB is a lot of disk space for a minimal OS like ChromeOS to take up.  From looking online, this doesn't seem to match what other people are saying.

Is there something I'm missing here? 

Also, I could install ubuntu on an SD card, but would that be pretty slow?  Is it worth it doing it this way?

---

### Post by TheFu on 2016-06-08
There are many things missing.

a) if he can, return that ´b´ version and get the ¨c¨ model which has 2x better CPUs which make running other OSes a joy.  The C3300 is very nice.  I have a C3350 and previously had an Acer C720. Both had nice CPUs with passmarks over 1500. The N2840 CPU is 60% too slow to be happy.  IMHO.  Intel should be embarrassed to have released that CPU.
b) I´ve never been able to dual boot ChromeOS with any other OS. The Chrome installer wipes the entire disk. It isn´t a normal Linux - take a look 
c) I´ve tried to load ChromeOS inside a virtual machine - it installed, but never got to a GUI on reboot.
d) I don´t know anything about the ¨b¨ models, but the ¨C¨ models can have a larger SSD swapped inside.  I have a 64G SSD in mine, run Ubuntu-Mate and 2 VMs happily.

[http://www.fascinatingcaptain.com/howto/install-ubuntu-on-the-toshiba-chromebook-2-in-5-steps/](http://www.fascinatingcaptain.com/howto/install-ubuntu-on-the-toshiba-chromebook-2-in-5-steps/) is a useful link. If you go this way, note that the warranty **MUST** be violated to make it work.

If you aren´t as adventurous, try crouton.  I did that for about 4 months. However, every time google pushed an update, usually weekly, the crouton setup would **get weird.**  Graphics would get funny, swapping between ChromeOS and the Ubuntu running inside a chroot would get stuck, plus a few other different issues around sound. The solution was to reboot, backup, then patch the crouton setup and chroot areas.

Probably more than you´d like to know.

The most important aspect of this is that every different model of the Toshiba Chromebook 2 line is a little different. Look for specific instructions for the ¨B¨ model, if you keep it.

---

### Post by user1397 on 2016-06-15
a) Woops, I posted the wrong link.  He actually did get the c model with the [COLOR=#111111][FONT=Arial]Celeron 3215U processor
b) I've realized this from my research, I know that you have to initially wipe your disk to get to developer mode and then you can either dual boot or use crouton
c) I've gotten chromiumOS installed in virtualbox a while ago but haven't tried it in a while
d) Even though this is a "c" model, it still only has a 16GB SSD

And yup, very well aware that warranty would be voided unless I just put everything back to stock.

And good to know about crouton, I was gonna go that route but didn't know if there were any negative sides to it. Now I know that it isn't all butterflies and rainbows.

My only real questions were about why it seems like so much storage is taken up by chromeOS on the 16GB SSD, and if installing ubuntu on an SD card is worth it speed-wise.

Thanks for your input.[/FONT][/COLOR]

---

### Post by TheFu on 2016-06-15
You cannot put everything back ¨to stock¨ - there´s some electric connection that must be scrapped off.

No need to ¨wipe the disk¨ to get into development mode. The OS isn´t touched, just the user data gets wiped.  I always login as guest, so never had **any** expectation of local data being saved.

16G is the only size SSD provided with those.  It is a trivial upgrade and well worth it.

crouton or full install - not really any speed difference noticed, but there are different hassles with each method. For example, if you need any kernel drivers, forget that with crouton.  Have to use something else, since NFS won´t work.  NFS is a way of life here, so NOT having it was a major hassle.  Audio is a hassle either way - pulse doesn´t work well and the passthru from crouton sometimes gets confused.  There are lots of other little things about crouton that drive me nuts too.

With a full install, you get to screw around with keybaord mapping, console languages, wifi drivers, power/standby/hibernate stuff and a few other things.  At least with a full install, the solutions are in our hands, not limited by ChromeOS.  Plus it is nice to have a full OS and not be limited by a special-purpose OS.

---

### Post by user1397 on 2016-06-15
Oh, I thought that electric connection thing was a limitation of the older chromebooks but not the newer ones?  Maybe not

From a lot of the guides I was reading online, it just said that if you enable developer mode you basically reset ChromeOS first before you can do anything else (that's what I meant by wipe the disk) so you lose any local files and stuff (not a big deal of course cause you can always back things up).

And yea I'll mention it to my brother to see if he wants to do an SSD upgrade.

Thanks for the suggestions, definitely sounds like crouton maybe isn't that worth it, probably gonna try to do a full install on a USB 3.0 drive

---

### Post by TheFu on 2016-06-15
I never was able to get USB3 port to boot anything. For a boot OS, the USB2 port (left side) is used.  I don´t know why.

As you can see, there are ¨gotchas¨ all along almost every path.  Why put up with this crap?  sub-3lbs, 8+ hrs battery, 4G RAM, and 1080p for $330.  I saw a Lenovo for $220 a few weeks ago with lots of good stuff, but it was 4 lbs and 768p.  Deal killers for my desires - even if it does have a proper DELETE key (which I miss more than almost anything else!). Stupid google removed wasted the DELETE with a power button.  I can do without the power key, but not a delete key.

---

### Post by user1397 on 2016-06-15
True, good to know about the USB port thing.

And yea I agree, I think the chromebook is odd in that its use case is basically the typical end user and that's it.  Like sure you can develop on it, but it doesn't support nearly all of the stuff linux/windows/macOS support.  It's not meant for gaming, not meant for development (I get that it is fine for a lot of web dev stuff), not meant for any specialized software like audio/video/photo editing, CAD, etc.  Basically just normal end users who only need a browser, email, some basic document editing, basic photo editing, and media.  The funny thing is, that's probably like 80% of computer users (totally can't back this up, just a feeling I get from my experiences helping out family, friends, random people)

---

