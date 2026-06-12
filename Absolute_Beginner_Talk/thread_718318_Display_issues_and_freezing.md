---
title: "Display issues and freezing"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by beefyco on 2008-03-08
I'm new to the whole Linux scene just this week. I just got a new job doing software testing so I figured I'd act like I knew something about computers. Anyway, I installed Ubuntu 7.10 on both my desktop (fairly quick P4 3.2ghz, 3 gb ram) and a REALLY old laptop that I just got for free and put a new motherboard (dell inspiron 2600).
I like it..I think.
I love the look and the efficiency of it all. However, I feel like I'm running Vista or something because I'm having so many problems (Sorry, it's probably mostly user-errors, that was a little rash)
OK so here's my laundry list:

1. When I install the 'restricted drivers' for my ATI x300, the desktop effects won't work anymore, so I decided not to install them (this may be causing the other problems I'm not sure)
2. Ubuntu randomly freezes with no rhyme or reason (using firefox, editing display settings, etc.) not linked with any program that I can see. I can only hard reset my computer and then it all comes back with a smile like nothing happened (and I keep forgiving it because I just love that orange background smile it gives me)
3. On the laptop, whenever I boot Xubuntu, it loads and correctly displays the loading screen, but then as soon as it gets to login, the monitor freaks out and looks like i just dropped it off a desk and it broke. It still works fine with XP. (horizontal sync issues maybe? I'm not sure how to edit that before booting? maybe something else?)
4. Back to the desktop, whenever I suspend the computer using ubuntu, it won't come back for any keystrokes or mouse movement, then I have to push the power button on my computer. When I do that, all that comes up is what looks like an infinite loop of garbled text (like pre-OS command prompt stuff) I couldn't really tell you what it says other than it looks like it's very confused between 2 or 3 messages.
5. This isn't really a bug issue or anything, but on a side-note, anybody know what a good OSX emulating dock is for ubuntu as well as maybe an expose for ubuntu? I think I've seen them on youtube, but I haven't found it yet.

OK I guess that's all I can think of for now
Please help this poor newbie. I want to have faith in linux like all my computer buddies tell me I should. I love how it works WHEN it works, but I'm having issues. help.:confused:

---

### Post by Ecclesia on 2008-03-08
I'm sorry that you're having issues with freezing.  That's not supposed to happen with Linux, and it seems to be a relatively new issue for a large number of people related to video drivers.  I had some issues with my NVidia card, but don't have any experience with ATI, so I can't really help you there.  Many people report that they are able to keep their computers from crashing by disabling Compiz desktop effects.  So, you probably want to try that to see if this helps.  Try searching the forums for crashes with ATI cards.  There are a few (quite long) threads on problems people have with crashes. 

And of course - the expose effect that you're looking for is a compiz plugin.  To have access to this, you need to install the compiz config settings manager (just search for it in Synaptic).  It will pop up in your System -> Preferences menu.  You can then use the "scale" plugin and configure it how you like.

---

### Post by Ecclesia on 2008-03-08
Oh, on your laptop - you said it's really old - what are the specs?  It might not run Xubuntu.  I find that older machines do much better with other distros.  Depending on its age you might want to try elive, puppy linux, or DSL.  Or maybe Debian proper.  I'm sure there's probably a slackware based distro that would do well on it too (maybe zenwalk?  I don't have any experience with it though...)

---

### Post by beefyco on 2008-03-09
the laptop is a dell inspiron 2600... I got ubuntu 5.10 (breezy) running on it, but it's incredibly slow. It only has maybe 128mb of ram so that's a big issue. I'm getting more asap. Any advice on the suspend issue? it's really sucking

---

### Post by Ecclesia on 2008-03-10
No thoughts on the suspend issue... I don't use suspend myself.  That's one of the issues with Linux hardware support so far as I can tell.

With so little ram on your laptop you might want to try a different distribution.  I love using Ubuntu on newer computers, but it's unbelievably slow on older machines (I'm not sure why).

DSL (Damn Small Linux), Puppy, Vector, etc might be a better choice.  I was using elive with an older machine for a while and that seemed to run fairly well and had some nice features.

---

### Post by beefyco on 2008-03-12
ok so heres what's goin down: I got ubuntu 5.10 (not xubuntu) to run with a clean install (no windows). I hear the xubuntu runs a LOT faster because of the xfce or something like that, so I'm going to attempt a clean install of that (luckily I just got this laptop and have nothing important on  it yet). The ubuntu problem on my desktop persists and I'm sad to say I'm on windows right now. The suspend is a big issue for me because my computer's next to my bed and I need to suspend it at night to save power and get sleep :) ...also the freezing doesn't happen as often, but every once in a while it still does. I'm assuming its the desktop effects, but I hate to get rid of them because they're so cool looking. (and I'm just that shallow) any more advice from anyone on both making it more stable and the standby/suspend feature? I'm apparently not the only one with this issue, but I have yet to find a workable solution (tried s2ram but it wouldn't install?)
thanks again

---

### Post by Tatty on 2008-03-12
I hope the 5.10 was a typo, thats a reallly old version :D

In regards to the freezing, try disabling powernowd... go to system->administration->services then scroll down and find something along the lines of "CPU Frequency Scaling powernowd", and uncheck it.

If the freezing stops then it was due to a bug caused by powernowd and nvidia drivers not getting on too well...  

AFAIK there is no actual fix for this other than disabling the frequency scaling.

---

