---
title: "Kernal panic"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-10-01
A Fresh install of ubunto from both a later live and more recent alternate cd both leave the following problem after updates are retrieved and the latest kernal is then rebooted to

Kernal panic-not syncing:vps:unable to mount root fs on unknown block(0,0)

Trouble is even booting to the prior kernal is not happening now either and im only able to gain access at all via the "recovery mode" of the previous kernal........

I reformatted with both the Ubunto live cd and gparted`s own cd during the 2 different try`s....Dont want to do it a third time....NOT in one day:-? 

If it`s not one pc it`s another;) .....

TIA

---

### Post by bulldog on 2006-10-01
I missed your postings,it's awfull quite here..........:D 

But do it a third time,I don't mind at all.

---

### Post by xpod on 2006-10-01
Awa an chase yer tail....;) 
Got the previous one booting so dont know what was going on there but the new one is still the same.......Just noticed a few "pro`s" on and thought id see if they in their wisdom knew what to do..

I`ll wait till an expert comes along......thanks anyway;)

EDIT...and it`s "quiet"...shssssssss

---

### Post by bulldog on 2006-10-01
Yep do so,fine by me :D

In the mean time try to reinstall the stubborn kernel and see if it brings you somewhere.

---

### Post by bodhi.zazen on 2006-10-01
Try this:

```
sudo aptitude install initrd-tools
```

---

### Post by xpod on 2006-10-01
LOl....Thats why it`s been so quiet m8 as ive been banging my head of the wall and google all evening and was determined i was`nt going to start a thread.....

Good day anyway m8...you know im only pulling your leg...s;)

EDIT...ok missed them....Im sure i tried the reinstalling of the kernal after following a similar thread over on the installation forum....
Will try again......

---

### Post by bulldog on 2006-10-01
I should start a topic like,

Kernel Panic and I want help now!!!!!!!!!!!

Otherwise I go back to windows!

---

### Post by white on 2006-10-01
I had this same problem on an older P3 machine, I found out the hd was dying. Don't know if that helps any.

---

### Post by bodhi.zazen on 2006-10-01
[list=number][*]How did I know I would find you in the Panic mode ? :lol:
[*]Ever notice how no one talks to us anymore? Guess we've lost the touch.[/list]

Quite, my baby is sleeping.......  =;

---

### Post by bulldog on 2006-10-01
> **bodhi.zazen said:**
> [list=number][*]How did I know I would find you in the Panic mode ? :lol:
[*]Ever notice how no one talks to us anymore? Guess we've lost the touch.[/list]

Quite, my baby is sleeping.......  =;

Well 'they' never talked to me so.............

ssssshhhht

---

### Post by xpod on 2006-10-01
strangely enough that thought had entered my head too when i was`nt getting any kernal to boot but the "2.6.15.23.386" is still ok now it`s just the "2.6.15-27.386" thats not booting......

If i go to it in synaptic it`s already installed so cant be picked to install again and if i mark it for removal first it sure looks like it`s getting rid of more than just that kernal.....the "linux.386" image for example....THATS not good is it?

EDIT:STop posting while im writing!!:mrgreen:

---

### Post by bodhi.zazen on 2006-10-01
It's OK with me, I have the voices to keep us occupied........ 8-[

---

### Post by bodhi.zazen on 2006-10-01
> **xpod said:**
> strangely enough that thought had entered my head too when i was`nt getting any kernal to boot but the "2.6.15.23.386" is still ok now it`s just the "2.6.15-27.386" thats not booting......

If i go to it in synaptic it`s already installed so cant be picked to install again and if i mark it for removal first it sure looks like it`s getting rid of more than just that kernal.....the "linux.386" image for example....THATS not good is it?

EDIT:STop posting while im writing!!:mrgreen:

"Go for it", can hardly be worse.... :)

---

### Post by xpod on 2006-10-01
Ok i CAN re-install....never checked:neutral:

---

### Post by xpod on 2006-10-01
Okay folks.....it has sort of worked this time,But i get the below message as soon as the desktop comes up.....
I think the hd theory could still be right as i just seem to have had numerous wee issues this last week or so with problems at boot up and having to force reboots more than is normal....(even for moi)


[ATTACH]16665[/ATTACH]

Not sure about starting that service as all available ones in the "services" are already chosen

---

### Post by bodhi.zazen on 2006-10-01
What happens when you```
sudo /etc/init.d/dbus start
```

---

### Post by xpod on 2006-10-01
Looked good...started ok,just to reboot now?

---

### Post by xpod on 2006-10-01
Well it was`nt so simple.
Kept stopping at a couple of different places..."syslogd" or "volume enterprise management"......Got it to boot eventually just by rebooting persistantly but then FF would`nt start so i got Swiftfox just to check and rebooted again and so far it seems ok......but it`s more than just a cranky install as mentioned.

Hd`s had so many re-install`s in it`s few months with moi that it`s run it`s course me thinks........
Got to make do with these old heaps till after the year im afraid but i might get a new drive for it as i was considering a spare for something else anyway:mrgreen: ..just need to get it for this now.
Goodnight folks.....thanks as ever;)

---

### Post by gn2 on 2006-10-01
> **xpod said:**
>  but i might get a new drive for it as i was considering a spare for something else anyway

Aha! Perhaps the ultimate backup strategy?

If the old machines are toiling a bit it could be something as simple as dust build up, or bad connections.

It's not the first time I've resurrected a PC with a can of compressed air and pulling out, cleaning connectors and re-inserting all the data cables.

---

