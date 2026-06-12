---
title: "Ubuntu, why must you take fight me? (no internet)"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by mithbuntu on 2007-10-05
I was very excited to test out Ubuntu, but so far it has been one set back after another.

First my sound dies mysteriously and I can not get it back.
Second my screen goes completely black when I boot up and I decide to reinstall only to format an identically tagged drive with all my data on it.
Third I get back in and my internet stops working on the linux pc, but I know my internet is fine because I am here now with my laptop.

Anyway. I am mostly concerned with the fact I now have absolutely no internet connectively on a perfectly healthy internet set up.   I am not sure what to say other than I rebooted only to come back to a pc with no internet.  Multiple reboots only caused my sound to vanish after gaining it back from the reinstall.  :(

---

### Post by Henry Rayker on 2007-10-05
With Linux, reinstallation is rarely the method you should take. Provide some details and maybe someone can help you. Things like...what kind of sound card you have, what video card you have (for that black screen thing) and most importantly, what kind of network connection are you working with. Is it wireless, or wired?

If wired, try this:
```
sudo eth0 up
sudo dhclient
```

That might bring it up. If its wireless, we've got a whole different issue.

---

### Post by mithbuntu on 2007-10-05
I tried a few CLs to refresh/renew my dhcp and it seemed to work.  That is, my internet works again.

As for my sound?
I have a Sound Blaster Audigy 2 ZS.  I know it CAN work because the first few boots it was working fine, but then something happened.  I can't be for sure what because I am so unfamiliar with linux, but it seems to me the default sound system changed.   I have two onboard audio devices, i believe, along with my sound blaster.  I've read so many threads regarding the ZS, but none have helped me thus far.  

My video problem came about when I was trying to set up a remote server.  I really don't know what it was about, but anytime I booted up the screen showed the login for about 1 sec before going completely black.  I waited 15 minutes for it once but it never came out of it.   That's when I reinstalled.

---

### Post by mithbuntu on 2007-10-05
Resolved my problem.  Here's the CL to set the default sound card:

```

sudo asoundconf list

```

find the name of the card you want to use, then

```

sudo asoundconf set-default-card <card_name>

```

---

