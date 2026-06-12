---
title: "Why are we poor PPC users stuck with FireFox 1.0?"
date: 2005-05-21
forum: Apple PPC Users
---

### Post by Rxke on 2005-05-21
Not that I'm really the type of guy that always wants the newest of the newest (I wouldn't be typing this on a rev B Clamshell G3 if I was, heh...)

... But being stuck with FF 1.0 is a headache, for when you want to install an extension, you get a windoow saying to upgrade to FF >1.0.... And they only show you the x686 versions (and OSX....)

---

### Post by ssam on 2005-05-21
the fixes in firefox 1.0.4 have been backported into the firefox in the ubuntu repositories. aslong as you are using synaptic or apt or whatever, to keep to date then you are safe from the security problems.

the only trouble is that the mozilla website thinks that you are still vunerable and block you from extensions. [https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681) describes the problem.



the fix is to type
```
 
about:config

```
in the firefox addess bar, to get to the hidden settings. put
```
 
vendor

```
in the filter box. then double click on 
```
 
general.useragent.vendorSub

```
and change 1.0 to 1.0.4

sam

---

### Post by Rxke on 2005-05-21
Thanks for the workaround, greatly appreciated.

But oh but oh but... as in the bugzilla comments, why do this backporting to 1.0.2?

I thought Ubuntu was known for its up to date-ness, cutting edge, and now this nonsense...

One good reason? One?

(Jup, feeling irritated, how`d you guess? )

---

### Post by basse1989 on 2005-05-21
Ubuntu does not offer any program updates after a release.
This is for stability reasons, even though they should be able to let us update and still keep our systems up to date.

---

### Post by Rxke on 2005-05-21
Hmmm... Then why do I keep downloading security updates etc... 
I know, I`m trying to be a pain in the posterior here, but the FF upgrades are mostly securityfixes, not real upgrades...

I guess this has already been discussed to death, so nevermind. (still grumpy) ;-)

---

### Post by fdoving on 2005-05-21
[QUOTE=Rxke]Hmmm... Then why do I keep downloading security updates etc... 
I know, I`m trying to be a pain in the posterior here, but the FF upgrades are mostly securityfixes, not real upgrades...

I guess this has already been discussed to death, so nevermind. (still grumpy) ;-)[/QUOTE]
 It's to keep the stable release at it's more or less stable state. Changing stuff and adding new versions would sooner or later break something. (Like in the now unstable breezy.)
The problem must be significant for a new version of a package to qualify for the updates section.
There are various backport projects backporting software from breezy to hoary, to make newer versions of software available to users of stable releases. 
Take a look at [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

I don't know how the powerpc support is in that repository.

- Frode

---

### Post by Rxke on 2005-05-21
[QUOTE=fdoving]The problem must be significant for a new version of a package to qualify for the updates section.[/QUOTE]

I`d say this FF thingy *is* significant.

At least for the `newbie`people that don`t like to do `weird`stuff, like looking for a solution in Bugzilla, and start `messing`with their config list etc.

I personally like to tinker with my computer, but I try to use it for day-to-day work, too... And when I get confronted with something like this, I get... Slightly irritated, heehee.

I mean, FF has a *huuuuge* community of users, a lot of them programmers, so if you wait a month or so, you can be fairly sure the latest patch is stable, no? 
FF is a true posterchild for Open Source, so i think it`s a real pity potential switchers would think to themselves`why can I use FF 1.0.4 on Windows an not on (this) Linux?'

And I *do* appreciate the underlying reasoning, stability over features, but with all due respect, 5.04 isn`t very stable to begin with, compared to Debian stable, Ubuntu chose to use versions that are more up-to-date, but sometimes slightly broken, which is ok, no, great! Debian stable gives you the feeling you're stuck somewhere mid-ninetees... Ubuntu feels modern and usable. so why not upgrade a high-profile  app like FF you *know* has been tested by gazillions of users? Esp. when not upgrading makes things not work as expected...

Dang, now I`m again discussing this, despite saying I wouldn`t.  :^o

---

### Post by fdoving on 2005-05-21
I totaly understand you. 
Applications should behave as expected, that should be a goal.

I'd suggest that you open a account on [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) report problems, suggest solutions adding good reasons like "it's expected behaviour" etc. That would be a nice contribution to the ubuntu community.

The guys deciding what is significant and what is not are working hard on other sections of ubuntu too. Just saying "it would be nice to have a new firefox in hoary" doesn't do it. "It's expected behaviour".. "Extensions support breaks" etc. are (afaik) more likely to be considered significant.


- Frode

---

### Post by Rxke on 2005-05-21
The only 'problem' I have with subscribing to Bugzilla is my feeling of insignificance as a fairly newbie user, prone to talking out of his a**e.
I mean, who am i to go complaining about stuff like this? I hardly know what I'm talking about.
Case in point: the title of this topic, me sobbing about 1.0.0 while it is in fact 1.0.  4, only FF but backported (If i'm not mistaken, and I probably am...)

See? 

Say I posted my sobbing stuff there, they'd probably go: WTF RTFM + STFU n00b! :D :D

That's why I posted it here, i guess, as insignificant newbie on the friendly UbuntuForums, and not on the big and scary "Bugzilla for pro's..."
So that one of those more friendly pro's reads this and thinks, hmmm... that stupid n00b has a point... And posts about it in Bugzilla or someone where it should be posted. That pro will be taken serious, I probably will not be...

Trickle down effect...

[QUOTE=fdoving] That would be a nice contribution to the ubuntu community.[/QUOTE]

It's just that I feel I'm not into the right ballpark regarding knowledge about Linux for doing it... I frequent these boards, read a lot, and when I *do* know something, i reply. And sometimes I post questions that could be of interest to others. That's my low-level contribution, because I'm not up to higher-level stuff, so to say.

---

### Post by fdoving on 2005-05-21
Well, you could say that. 
But it doesn't help much to sitt back and wait for someone else to discover the bug and post it to bugzilla.

If a user experience a problem and post it to bugzilla it is more likely to be fixed
than if you post it here or somewhere else and hope for someone else to post it to bugzilla.

Another thing is the fact that advanced users tend to ignore what could be  show-stopper-problems for new users. Simply because the more advanced users know how to handle the problem and have probably done it a few times before.

When it comes to bugzilla, you won't be taken seriously if you post things like "The "#¤%"# thing doesn't work! FIX!" and so on. Be nice, explain the problem in detail, don't expect it to be fixed in 5 min. ask others to confirm your bugreport. That way Ubuntu will improve and you'll helping.

PS. Ubuntu-people are nice people.

- Frode

---

### Post by Rxke on 2005-05-21
[QUOTE=fdoving]PS. Ubuntu-people are nice people.

- Frode[/QUOTE]

I know!  :)  

I guess I'm still a bit hesitant to go the Bugzilla way, having been a Debian errr...  newbie, and well, a lot of those guys are not that friendly... Still feel kinda shellshocked...

Bugzilla/Ubuntu should then be more friendly I guess.

Anyhow, the issue has been posted on Bugzilly already, so in this particular case I would be carrying water to the sea, or irritate people at best.

So... morale of the story ... when one thinks (s)he found a bug, check [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) first and then these forums?

In other words, I'm yet again wasting bandwith with my stupid remarks in the wrong place, sigh...

---

### Post by fdoving on 2005-05-23
> 
Anyhow, the issue has been posted on Bugzilly already, so in this particular case I would be carrying water to the sea, or irritate people at best.

Serious comments are always welcome.
"Masters of the obvious" can irritate people.


> 
So... morale of the story ... when one thinks (s)he found a bug, check [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) first and then these forums?

Checking bugzilla first can be a good idea, yes.

You can however, find workarounds on this forum too.
The distribution fixes are announced at bugzilla. (Can be technical) 

> 
In other words, I'm yet again wasting bandwith with my stupid remarks in the wrong place, sigh...

I don't consider that a waste of time.

- Frode

---

