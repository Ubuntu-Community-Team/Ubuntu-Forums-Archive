---
title: "no sound, sound, no sound"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by javaboy on 2005-11-18
Hello,

I am almost ready to delete windows, just having two problems.

The first one is skype only works for one call....  This is a skype bug so moving along.

My second one is that my sound only works sometimes.  At first I thought it had to do with restarting the computer, vs powering off.  Didn't make much sense, but I didn't know what else to think.  But that is not it.  It seems to be random, sometimes it works and other times it doesn't.

I am not sure what I should be looking at?  When it boots it sometimes holds up on "hotplug" which I read somewhere might actualy be caused by my computer trying to connect to a DHCP when there isn't one that that I should set the time out to 10 in stead of 60?  (maybe three problems?  I don't know how to do this?)

Anyways, my sound is the biggest problem.

Any ideas?  What should I be looking for when it works/doesn't?

Thanks.

---

### Post by kruz on 2005-11-19
this happend to me cuz i wuz lazy
get ur sound working with alsamixer
and modprobe then shutdown and hit
"save my settings" or w/e it is

that worked for me :D

---

### Post by Kapre on 2005-11-19
[QUOTE=javaboy]Hello,

I am almost ready to delete windows, just having two problems.

The first one is skype only works for one call....  This is a skype bug so moving along.

My second one is that my sound only works sometimes.  At first I thought it had to do with restarting the computer, vs powering off.  Didn't make much sense, but I didn't know what else to think.  But that is not it.  It seems to be random, sometimes it works and other times it doesn't.

I am not sure what I should be looking at?  When it boots it sometimes holds up on "hotplug" which I read somewhere might actualy be caused by my computer trying to connect to a DHCP when there isn't one that that I should set the time out to 10 in stead of 60?  (maybe three problems?  I don't know how to do this?)

Anyways, my sound is the biggest problem.

Any ideas?  What should I be looking for when it works/doesn't?

Thanks.[/QUOTE]


Javaboy - try looking into your Multimedia Systems Selector and try playing (play around ) with the combinations of your defaulr sink and default source (ESD, OSS, OSD, etc).

K

---

### Post by patrick295767 on 2005-11-19
hi, 

i try to help: 
is chmod 666 /dev/dsp 
helping ??
  
that helped in my case 'cos of permissions... 

greetz

---

### Post by javaboy on 2005-11-19
Once again thanks for all your help!  I think that I have found the problem to be a "External Amp" switch in my sound control.  I don't know why sometimes it works on boot up and sometimes it doesn't, but it seems that I am able to check that box when it is not working and I get sound.  I'll try to save the settings on shutdown, maybe it well hold.

Thanks for the help though!  Now I can delete windows for good!

Does anyone know about the hotplug issue that I discribed?  Or how to set DHCP time out to a shorter value for it doesn't hold up trying to connect to a network that doesn't exist?

---

### Post by amorangi on 2005-11-19
I've got the same problem, and despite the fact I can get over all the other idiosyncrasies of Ubuntu, these intermittent sound problems is becoming the final straw. It works, then doesn't work, works again by changing random settings (sometimes), then stops again for no reason, but it is totally random. Rebooting produces no change.

I've tried all the ideas in this thread to no avail, and the ideas in other threads. The sound sometimes starts working then after half a second descend into distortion. Sometimes the sound just clicks - no matter what setting I use in the multimedia selector the test produces clicks.

I have VIA onboard sound.

Can someone give me some idea of something to kill, uninstall, retsart or anything?  The other people who use this PC are getting angry about this issue and if I can't fix it I'll have to go back to windoze.

---

