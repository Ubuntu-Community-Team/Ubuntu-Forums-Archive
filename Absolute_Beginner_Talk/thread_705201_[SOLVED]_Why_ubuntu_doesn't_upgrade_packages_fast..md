---
title: "[SOLVED] Why ubuntu doesn't upgrade packages fast."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by kozer on 2008-02-23
I want to know why ubuntu doesn't upgrade its packages fast as artch,for example,do.I am an ubuntu user and im very dissapointed about this.Many people go to onother linux because of this.Can anyone know why this is happening?Sorry if my english are bad...:).And sorry if this is not in the proper section...

---

### Post by psyBSD on 2008-02-23
Arch linux does not have a separate 'stable' branch. And therefore, all updates are pushed immediately to the users.

Debian (and it's relative Ubuntu) behave in a different way, they have an unstable branch where updates are pushed to immediately. A 'testing' branch where the new release is being stabilized and a 'stable' branch which 'just works'.

When you take a look at Ubuntu's testing branch (eg, Hardy Heron), you'll see that the software over there is newer then what you've seen in gutsy. In this branch, new software is tested and stabilized before it will be delivered to the public. (When Hardy is released)

New software generally comes with bugfixes, but developers can't test it on every platform and OS. To make sure it works with ubuntu, it will first be tested before it is released.

I hope I've answered your question :)

---

### Post by kozer on 2008-02-23
and this is not going to change?i mean ubuntu have pre-released updates but not all programms update fast enough in there(eg drivers).I love ubuntu but i want to have and the latest programms too...And its pitty to loose users because of that.

---

### Post by FrozenFox on 2008-02-23
Er, ubuntu has an 'unstable' branch right up your alley.. please see distrowatch.com for a link to ubuntu hardy heron.. if you want constant updates, thats what hardy will get you.. there's typically about 10+ a day that I've seen. Most people do NOT want the most bleeding edge software because it is just that -- bleeding edge and thefore classified 'unstable' and has problems occasionally. Giving everyone not ready to deal with it bleeding edge software is a terrible idea that would drive people away from linux FAR more than it would attract them. But if that's your cup of tea, download and install ubuntu hardy heron. I'm a bleeding edge guy myself. But it is an enormous mistake to assume that in order for your system to not suck, it needs to be bleeding edge up to date. It's suitable for some users who can deal with problems, but the normal ubuntu distro, gutsy at the time of this message, is more than sufficiently up to date (and -stable-) for most peoples' needs.

---

### Post by SpiderGorilla on 2008-02-23
*In the interest of not keeping ahold of knowledge...*

If you really really want to, you can do the following and it'll push updates more often (but it will also break your system more often):
[COLOR="Red"]
**_(Please note that this is *NOT* recommended!!!)_**[/COLOR]

Go to System >> Administration >> Synaptic Package Manager

Go to Settings >> Repositories

Click the tab "Updates"

ADD a check to "Pre-released updates"

You can also change the frequency of your update cycle.

Once again, I seriously do **NOT** recommend this! Stick with what the community has tested and proven to work. This is the best way to maximize your Ubuntu experience!

---

### Post by kozer on 2008-02-23
And if i want constant updates when hardy is released then i have to try the new alpha of 8.10(when this is out?).But in this point of view i think you are right..Its better for average users to heve a more stable system..

---

### Post by FrozenFox on 2008-02-23
Right.. hardy's being actively updated now, but when it's released it will slow down more or less as Gutsy is now to make way for the new testing branch, whatever they call 8.10. I'd agree with the previous poster, unless you are patient and ready to deal with occasional problems and breakage, it's best to stay in the current stable branch and understand that just because there aren't 45 updates a day does not mean your setup is ancient or that newer is necessarily better. It's logically contradictory, in general anyway, to want both bleeding edge and rock solid stability in any OS. It's quite rare for something completely new to be without problems because it -- well, hasn't been tested yet! :)

---

### Post by p_quarles on 2008-02-23
> **kozer said:**
> and this is not going to change?i mean ubuntu have pre-released updates but not all programms update fast enough in there(eg drivers).I love ubuntu but i want to have and the latest programms too...And its pitty to loose users because of that.
No, it won't change, because Ubuntu's development model is a staggered release. Following a final public release, only security and bugfix updates are released. That's the chosen development model.

Arch and Debian Testing/Unstable are better options for users wanting a rolling release. 

You may also be interested in the backports repositories for Ubuntu. These will give you updates to some, but not all, applications as newer versions are released.

---

### Post by kozer on 2008-02-23
and another question(a little of topic)I want to buy a bluetooth stick.Iheard that almost everything is supported by ubuntu,but is there any chance to buy something that doesnt work?

---

### Post by FrozenFox on 2008-02-23
There's always a chance that something won't work. But I'd suggest making a new topic asking about bluetooth. Even better, if you include the name of a model or item you are considering if you have any in mind, or ask for suggestions.

---

### Post by kozer on 2008-02-23
thank you for your answers and sorryy for so many questions..Iwill open a new topic..

---

### Post by FrozenFox on 2008-02-23
No need to be sorry, that's what the forums are here for. :) but it would be helpful if you could mark this thread as solved via at the top of the page going to thread tools and setting this post as solved.

---

