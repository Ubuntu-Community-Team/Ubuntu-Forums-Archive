---
title: "Lost network access"
date: 2007-05-23
forum: Apple Intel Users
---

### Post by Seamyst on 2007-05-23
I'm running Feisty and Tiger on a partitioned MacBook.  Everything was fine yesterday morning, as far as Internet connectivity was concerned - I use Feisty for the most part and was able to check my email, view daily comics, etc.  I took it to work and changed the network settings to the saved configuration for work... but it wouldn't let me online.  I rebooted a couple of times, playing with the settings, but no dice.  Booted into Tiger and I could get online just fine.  Obviously it's not a network issue.  Brought it back to my room after work, switched to the appropriate configuration, and still no connectivity with Feisty.

I have no clue what's wrong - I'm on a campus ethernet network (dorm and general) and up until work yesterday it was working fine in Feisty.  I didn't install any updates (they were already all installed) or make any changes or anything.  Feisty is still running fine in other respects, as far as I can tell.

Any ideas on what went wrong?  Is it with my computer or something I need to take up with Computer Services?

---

### Post by ronocdh on 2007-05-23
> **Seamyst said:**
> I'm running Feisty and Tiger on a partitioned MacBook.  Everything was fine yesterday morning, as far as Internet connectivity was concerned - I use Feisty for the most part and was able to check my email, view daily comics, etc.  I took it to work and changed the network settings to the saved configuration for work... but it wouldn't let me online.  I rebooted a couple of times, playing with the settings, but no dice.  Booted into Tiger and I could get online just fine.  Obviously it's not a network issue.  Brought it back to my room after work, switched to the appropriate configuration, and still no connectivity with Feisty.

I have no clue what's wrong - I'm on a campus ethernet network (dorm and general) and up until work yesterday it was working fine in Feisty.  I didn't install any updates (they were already all installed) or make any changes or anything.  Feisty is still running fine in other respects, as far as I can tell.

Any ideas on what went wrong?  Is it with my computer or something I need to take up with Computer Services?
Well, I wouldn't say it's your computer, given that your connectivity works fine in OS X. So we can certainly rule out a hardware failure. FWIW, my wireless often goes out on campus in Feisty; sometimes it's solved by changing my internet connection settings to the saved set for the wireless in my apartment, then changing them back, but sometimes I just give up and reboot into OS X.

I don't think I have ever, ever had DHCP-enabled ethernet fail on me. I assume you're using the same cable and wall port for Ubuntu as you would OS X.... Man, that's a toughie. Don't give up yet! I'd give it a couple days, trying to work it out. Do you know anyone else in the dorms running Ubuntu? There's gotta be at least one more, no? ;)

---

### Post by Seamyst on 2007-05-23
Came back from my other job and I find it's working fine in my room..... I'd left it running Tiger while I was away, and booted immediately into Ubuntu.  I don't have a clue what happened, but I'm not complaining.

I'm probably the only person in the dorms right now who's running something other than Windows - summer break, there's only about fifteen of us on campus now.  I only know of maybe two or three others who are at all familiar with Linux, and they've gone home for the summer.  Oh well, it works now!

---

### Post by ronocdh on 2007-05-23
> **Seamyst said:**
> Came back from my other job and I find it's working fine in my room..... I'd left it running Tiger while I was away, and booted immediately into Ubuntu.  I don't have a clue what happened, but I'm not complaining.

I'm probably the only person in the dorms right now who's running something other than Windows - summer break, there's only about fifteen of us on campus now.  I only know of maybe two or three others who are at all familiar with Linux, and they've gone home for the summer.  Oh well, it works now!
Right, summer. I go to a quarter school: we've got two to three weeks left in the spring quarter! =)

Glad it's working again, and damn it, that happens to me all the time with wireless. Ubuntu acts up and I have to lie to it and tell it I love it and that I don't care how much we fight, it's just important that we spend time together, and every altercation actually helps us understand and grow closer to one another. But really sometimes I just want to snap my laptop over me knee and relegate Ubuntu to homelessness, drifting in the ether with which it so obstinately and sporadically refuses to communicate wirelessly.

BTW, hasn't it ever occurred to you guys that "ethernet" is a **great** title for wireless communications? Funny, that.

---

### Post by Seamyst on 2007-05-30
I still can't get online at work.  To elaborate: we use DHCP in the dorms, so it automatically assigns me an IP address.  The inn where I work is on a different network (though still on campus), so I have to use an assigned IP address and everything.  I have both of these settings saved as different locations, so it should just be a matter of switching locations and hitting the apply button, right?  Wait for it to switch over, then I should be able to go online.  I can do this in Tiger (where I am now), but not in Feisty.  I don't get any error messages, or messages saying it can't connect, or anything like that - but when I open Firefox, it just says "Loading [address]..." and stays like that for as long as I keep FF open.  

I've tried switching several times between locations, making random changes in my IP settings and changing them back to what they're supposed to be, booting into Tiger to make sure I AM getting connected, and nothing works.

---

### Post by ronocdh on 2007-05-30
> **Seamyst said:**
> I still can't get online at work.  To elaborate: we use DHCP in the dorms, so it automatically assigns me an IP address.  The inn where I work is on a different network (though still on campus), so I have to use an assigned IP address and everything.  I have both of these settings saved as different locations, so it should just be a matter of switching locations and hitting the apply button, right?  Wait for it to switch over, then I should be able to go online.  I can do this in Tiger (where I am now), but not in Feisty.  I don't get any error messages, or messages saying it can't connect, or anything like that - but when I open Firefox, it just says "Loading [address]..." and stays like that for as long as I keep FF open.  

I've tried switching several times between locations, making random changes in my IP settings and changing them back to what they're supposed to be, booting into Tiger to make sure I AM getting connected, and nothing works.
OK, thanks for the extra info. Let me generate a hypothetical situation just to confirm I've the facts right. Let's say you're in your room in Tiger. DHCP via ethernet works. Then you boot into Ubuntu. It works there, too, right? Then you pick up, go to your job at the inn, plug in, but no luck there: Ubuntu and DHCP via ethernet are not playing nice. But then you flip into Tiger. How about then? Works?

I do not think you should have two different settings in Network Manager if you're on the same network; DHCP should be able to handle this. Obviously something isn't getting flushed in Ubuntu, so your computer is freaking out thinking that it should have an older IP address when it doesn't. So, if you have it working in your dorm in Ubuntu, try shutting down the computer completely, till its cold and dead, then taking it to the in, plugging in, and booting up into Ubuntu. Does it work then?

It's a really weird problem indeed, and I'm interested in figuring it out. No wireless on campus anywhere?

---

### Post by Seamyst on 2007-05-30
> **ronocdh said:**
> OK, thanks for the extra info. Let me generate a hypothetical situation just to confirm I've the facts right. Let's say you're in your room in Tiger. DHCP via ethernet works. Then you boot into Ubuntu. It works there, too, right? Then you pick up, go to your job at the inn, plug in, but no luck there: Ubuntu and DHCP via ethernet are not playing nice. But then you flip into Tiger. How about then? Works?

I do not think you should have two different settings in Network Manager if you're on the same network; DHCP should be able to handle this. Obviously something isn't getting flushed in Ubuntu, so your computer is freaking out thinking that it should have an older IP address when it doesn't. So, if you have it working in your dorm in Ubuntu, try shutting down the computer completely, till its cold and dead, then taking it to the in, plugging in, and booting up into Ubuntu. Does it work then?

It's a really weird problem indeed, and I'm interested in figuring it out. No wireless on campus anywhere?

Your hypothetical scenario is correct, but for one thing - DHCP is used in the dorms only.  (We have two networks on campus, I guess - one for the dorms, which is DHCP, and the other for all the other buildings, which is static IP.)  I have a static IP address, gateway, etc, which I use for the inn.  This is why I have two settings in Network Manager, so I don't have to keep inputting all the settings when I switch to the inn, I can just switch settings.

We have a couple of wireless hotspots, but it's not campus-wide yet - and no wireless in the inn as of yet (though supposedly we're getting it this summer).

---

### Post by ronocdh on 2007-05-30
> **Seamyst said:**
> Your hypothetical scenario is correct, but for one thing - DHCP is used in the dorms only.  (We have two networks on campus, I guess - one for the dorms, which is DHCP, and the other for all the other buildings, which is static IP.)  I have a static IP address, gateway, etc, which I use for the inn.  This is why I have two settings in Network Manager, so I don't have to keep inputting all the settings when I switch to the inn, I can just switch settings.

We have a couple of wireless hotspots, but it's not campus-wide yet - and no wireless in the inn as of yet (though supposedly we're getting it this summer).
Oh, this makes much more sense! OK, well yes, hypothetically having multiple saved locations would do you perfectly well. Have you tried switching to your inn settings while still in the dorm (thus losing internet connectivity), shutting down, then moving to the inn, plugging in, and booting up (with inn settings active)? I think this would work if your system is having trouble "switching." Try this and let's see whether it works at all, then we'll work on not having to do it. ;)

Sorry for "biting your head off" before... I had seen way too many trolls on that thread and I wasn't reading names anymore. :oops:

---

### Post by Seamyst on 2007-05-30
I'll have to wait until tomorrow to do that, but yeah, that sounds reasonable.  (Lucky me I work here two days in a row this week, and so don't have to wait several days to try it out.)

And don't worry about the other comment - I figured the poster was a troll himself until I saw it was you, then I just figured you were having an off time or something.  :)

---

### Post by Seamyst on 2007-05-31
It didn't work.  I changed the settings over to the inn while I was still in the dorm, let it run for a few minutes then shut it down.  At work, I booted up into Feisty - but no connection.  I switched it to DHCP and back to static IP, booted into Tiger and then back into Feisty, but nothing worked.  I can get online just fine in Tiger, of course, so it's not a network/port/settings issue.

I'm completely stumped.

---

### Post by Seamyst on 2007-07-25
Well, I feel really stupid.  I'd had to nuke and pave the hard drive before this in order to get my partitions set up properly (especially the shared partition).  When I was setting up Feisty again, I mistyped the Gateway number (x.x.x.10 instead of x.x.x.1).  After I saw what I'd done, finished banging my head against the desk and changed the number, it worked fine.

Thanks for your help, though!

---

