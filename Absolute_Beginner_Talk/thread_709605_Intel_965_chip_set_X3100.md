---
title: "Intel 965 chip set X3100"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-02-27
I have Ubuntu 7.10 and I know my graphic card drivers have been blacklisted. 

What would happen is they are taken off the blacklist?
Would anything happen to make me reinstall Ubuntu?

---

### Post by Rocket2DMn on 2008-02-27
What do you mean it's been blacklisted - is support going to be dropped for it?  I have yet to see an intel graphics card that we weren't able to get to work in Ubuntu.  Did you ever reconfigure X (see [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) if you haven't)?  Even more basic, does your card work OK right now?

---

### Post by Tom--d on 2008-02-28
My card works, just [http://ubuntuforums.org/showthread.php?t=582112]("http://ubuntuforums.org/showthread.php?t=582112") says my card has been blacklisted.

What will happen if I take it of the blacklist?

---

### Post by hhhhhx on 2008-02-28
might get some spotty visuals, shouldn't hurt the card though

---

### Post by mjwhitfield on 2008-02-28
got the same card in my Acer laptop, I use it fine with desktop effects.  You'll only run into trouble if you wanna watch video.

---

### Post by Rocket2DMn on 2008-02-28
> **Tom--d said:**
> My card works, just [http://ubuntuforums.org/showthread.php?t=582112]("http://ubuntuforums.org/showthread.php?t=582112") says my card has been blacklisted.

What will happen if I take it of the blacklist?

How about that, my Mobility Radeon 9000 is blacklisted.  However, I think that just means they aren't creating any more support for it than already exists, so you may not have full functionality.  For example, dual head doesn't work on my laptop, but I still have 3d rendering and visual effects.
Basically that post is just saying don't fill out bug reports or complain about bad performance because it won't be fixed (probably because the card is too old).  We are more than happy to help you get the best performance out of it possible though.

---

### Post by mjwhitfield on 2008-02-28
The 965 isn't that old, I expect better support will be coming soon.

---

### Post by spamzilla on 2008-02-28
> **mjwhitfield said:**
> The 965 isn't that old, I expect better support will be coming soon.

This chipset is supported by intel, but the drivers are buggy and don't work "as they should." I hear that when the 8.10 ubuntu release comes around, alot of the driver problems should be fixed and it *could* finally be unblacklisted.

As for unblacklisting the chipset, its up to you if you do it, but just remember, its been blacklisted for a reason ;)

---

### Post by mjwhitfield on 2008-02-28
I understand that.

I only use my laptop for email, browsing and BBC iPlayer, all of which work with C-F enabled.

---

### Post by Golem XIV on 2008-02-28
Your chipset is blacklisted for Compiz and what it basically means is that you can't get the cool desktop effects with it.  This can be worked around but not completely (see [this post I made a while ago]("http://ubuntuforums.org/showpost.php?p=4322948&postcount=3")).

For regular uses you shouldn't have any problems with this chipset, but don't expect games or similar graphics intensive stuff to work properly.

---

### Post by Tom--d on 2008-02-28
Thanks for all your feedback :) 

I don't play games. Just the internet, email, msn, music and some videos is all I want to do. 
I will try to unblacklist it. See what happens.

---

### Post by Tom--d on 2008-02-28
...

---

### Post by Tom--d on 2008-02-28
Ah got it working :D 

How do I customize it and what are the features?

---

### Post by Rocket2DMn on 2008-02-28
If you want to try out Compiz Fusion to see if it works, go to System->Preferences->Appearance and hit the Visual Effects tab.  Then you can try enabling CF by hitting Extra.  You can customize by going to System->Preferences->Advanced Desktop Effect Settings
To check your framerate, open a terminal and run
```
glxgears -info
``` and if you are getting more than a few hundred, that means your 3d rendering is good and CF should work fine.

---

### Post by Tom--d on 2008-02-28
I got this

```
4397 frames in 5.0 seconds = 879.242 FPS
4525 frames in 5.0 seconds = 904.863 FPS
4535 frames in 5.0 seconds = 906.720 FPS
4543 frames in 5.0 seconds = 908.535 FPS
4480 frames in 5.0 seconds = 895.856 FPS

```

I guess that is good then :D

---

### Post by Rocket2DMn on 2008-02-28
Yeah, give CF a try.  What you might want to do is click the Extra tab, let CF enable, then hit the custom tab and change your preferences from there.  I would suggest saving the configuration to a file because if you click another option like None or Extra again it will choose those pre-defined settings and you will lose your custom changes.

---

### Post by Tom--d on 2008-02-29
So.. how do you get video to work?  or is that one of the bugs?

---

