---
title: "Failed Gutsy Upgrade - slow session boots"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-19
OK,
I did an attempt to upgrade to Gutsy and it looks like it failed because my kernel numbers are the same - isn't Gutsy supposed to be 22 or something? Mine's still at 16 and 15. 

I've been having problems even before the upgrade with slooooow session booting. Sometimes it's just the booting that is slow, other times it's slow only after I sign in going to my desktop.

Is there any Cleaning up command I can run that will undo any half-finished installs hanging in my system?
Of course, I'd love help with my booting issues - I've googled and tried other stuff already, like going into my wireless settings.

I appreciate any help,...

Many Thanks, ...Frank B.

---

### Post by starcraft.man on 2007-06-19
First thing that comes to my mind is why did you try to upgrade to Gutsy while its still in Tribe testing? I don't think that qualifies it as being ready for desktop use really... I should give it a try some time.

I somehow doubt that will fix the problem. Has it always booted slow like this? Have you installed any applications of note before it happened? Have you installed graphics drivers? In the end if the boot is really long maybe the Root system has simply had important files damaged or otherwise afflicted. Can you simply do a Feisty reinstall and see if this continues to be the case?

Other than that, I don't have any advice... your description is somewhat vague.

---

### Post by Brightbelt on 2007-06-19
Well, just to clarify, my reason in doing the Gutsy upgrade was not to attempt to fix the boot problem really.  Call it idiotic curiosity. This is an older, experimental Pent 4 laptop for me anyways.

But let me fast forward to possible solutions...I think I'd like to do a Feisty reinstall, but there's one obstacle. I use a D-link Wna-2330 Wireless Adaptor card as my wireless because it will do WPA. So I've got my Bcm4306 disabled. 

The point is that I actually took this laptop in the shop to have a computer fellow configure the D-link for me. I have no idea how he configured it. I'm getting better at all this and actually configured an old scanner from a French Ubuntu site recently.

Is there a way I can copy the folder that would have the D-Link configuration in it? I know that's simplistic but I thought it was worth asking.

Many Thanks for helping,...Frank B.

---

### Post by starcraft.man on 2007-06-19
I see, a suggestion is if you do a lot of testing (I do an unbelievable amount now a days), use a VM like Virtual Box or VMware. That way you can test and delete while not losing your stability. It's the best option IMO.

As for the wireless, sorry, not my thing. I just use plain ethernet on my home PCs and I don't do anything special with em. There are a lot of guides for ndiswrapper and I do believe that dlink works better than most of the cards/routers. If you really want help with that before doing it, wait for someone else to answer >.>.

---

### Post by Brightbelt on 2007-06-19
Well Thanks for your response, Starcraft. Actually, upon re-evaluating, I may stick with my system. Consider these facts:
1 - the boot problem was there before my attempt to upgrade.
2 - my kernels show no trace of Gutsy
3 - there's no way of knowing if my boot situation has in any way been affected by my attempt to upgrade...
4 - The only problem is the update manager won't work....I can't seem to update anything. 

Is there a way to reinstall the update manager?

Thanks for helping, Frank B.

---

### Post by Brightbelt on 2007-06-19
Well, I may not have fixed the Update Manager, but I used it successfully. The problem was it would pop up an advisory window suggesting I click 'Partial Updates', because of "A possible failed attempt at an upgrade". 

But when I chose partial updates, the manager would just close out. So I just ignored the window - x-ed out and did the updates anyways. And I'm still here.

Who knows, huh.  It's a day-by-day thing with Linux....

Many Thanks, Frank B.

---

### Post by ramjet_1953 on 2007-06-20
In Synaptic Package Manager, just click on the button "[COLOR="Blue"]Mark All Upgrades[/COLOR]" and then click on "[COLOR="Blue"]Apply[/COLOR]"

It should now finish all of the upgrades.

Regards,
Roger :cool:

---

### Post by Brightbelt on 2007-06-21
Thanks Ramjet!!! Frank B.

---

