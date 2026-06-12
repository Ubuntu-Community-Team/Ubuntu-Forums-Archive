---
title: "Which Version?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by sanicki on 2007-02-27
I need to build a ghost to install on 75+ machines. I'm sold on Ubuntu, but want to make the upgrade to Feisty easy for myself when April rolls around. Should I build my ghost on Herd 4 of Feisty and work around the bugs or stick with Edgy (or even Dapper?) and tweak it to mirror what's included in Feisty?

On another note, many of my users will be working off-site. I considered mounting their home directories to our server briefly, but with varying bandwith it's more trouble than it's worth. Now I'm looking at rsync to at least make sure a copy of their home directories live local. Anyone have a similar setup and want to impart some knowledge?

Thanks in advance.

---

### Post by bodhi.zazen on 2007-02-27
I am sure you will get various opinions here ...

I say in for a dime, in for a dollar.

Either stay with LTS (Dapper) for stability or Feisty Herd 4 for bleeding edge :)

Although I like Feisty, I would strongly consider Dapper for stability ...

Or wait for the release of Feisty ??

---

### Post by milton1 on 2007-02-27
Unless you are in need of something not found except in the most recent release, for that many machines I would recommend using dapper and wiating to upgrade until the next LTS release arrives. Otherwise, you are setting yourself up for a potential truckload of grief, trying to tweak 75 boxes to work with less stable systems.

---

### Post by sanicki on 2007-02-27
Gotta give my users Suduko by default. (Kidding.)

We ghost about every 6 months so I thought I'd stay a few months behind the latest, which is why I learned on Edgy. My rollout is early April so I can't wait for Feisty official, but I want it to be an easy transition.

Sounds like you guys are saying Dapper for LTS or Fiesty, so am I boned sticking with Edgy? From what I've read, version updates aren't always so smooth which is why I was considering building on Herd 4 instead of sticking to my self-imposed "few months" rule.

---

### Post by bodhi.zazen on 2007-02-27
I think Edgy may work, but why go it ?

It will be outdated by Feisty in short order if you want cutting edge.

Again, I would favor stability if such a large project and again steer you to Dapper.

Is there some new feature you need ?? If not, why sacrifice stability ?

IMO running on a personal desktop is one thing, a larger project is obviously different ...

---

### Post by sanicki on 2007-02-27
I may be being short-sighted, so I appreciate the input. I need to offer my users the greatest in functionality and eye-candy (it's part of the sell to abandon Redmond) so I figured stick with the latest version. So I educated myself on Edgy. I honestly am not sure what I give up by going Dapper.

The majority of the computers are laptops, so -even in Edgy- I have to install Network Manager. Since it's by default in Feisty I figured 'Why wait?'

My other issues (for example: support for Verizon and T-Mobile aircards, of which I only have VZ working currently...and tethered Blackberry as modem, also not working yet) I don't know if I lose moving back to Dapper.

Essentially time is short and I have too many options.

---

### Post by joeschmotz on 2007-02-27
hi i decided today to install ubuntu on my home pc.  Will I be able to just install an upgrade in April, or will I have to install the whole operating system over again?  Also, are there instructions for installing windows xp under ubuntu?  Can you run some xp apps on ubuntu?  I have some xp programs I would still like to use.  Are there any games available for Linux?  thanks!

---

### Post by spoot on 2007-02-27
> **sanicki said:**
> I may be being short-sighted, so I appreciate the input. I need to offer my users the greatest in functionality and eye-candy (it's part of the sell to abandon Redmond) so I figured stick with the latest version. So I educated myself on Edgy. I honestly am not sure what I give up by going Dapper.

The majority of the computers are laptops, so -even in Edgy- I have to install Network Manager. Since it's by default in Feisty I figured 'Why wait?'

My other issues (for example: support for Verizon and T-Mobile aircards, of which I only have VZ working currently...and tethered Blackberry as modem, also not working yet) I don't know if I lose moving back to Dapper.

Essentially time is short and I have too many options.
Another thing to consider is how often you (or your users) are going to update the whole bunch after you install it. If you can do it every 6 months, go the Edgy route (I would certainly not put an unfinished release such as Feisty at the moment on 75 production laptops). Since the LTS versions support upgrading straight to the next one, you can avoid the 6 month upgrade cycle and make it a lot less frequent.

On the other hand, wireless is probably behind in Dapper, but I'm really not sure of that. Perhaps someone else can fill you in on that.

@joeschmotz: Please make a new thread if you are going to ask a new question, you have a better shot at getting an answer that way.

---

### Post by sanicki on 2007-02-27
All,

Much thx for the input. I think I'll stay Edgy as I'm most comfortable with it and won't have a problem (at least not in the short term) updating every 6 mos.

---

### Post by whizbaby on 2007-02-27
It is possible to have an installation with packages from different distros (I don't actually remember how I did it, it was on debian sarge. I think apt-get lets you do that). So simply install dapper (or edgy) and then needed/desired packages from feisty (or any future release). Dependances are resolved and installed, too.

---

### Post by spoot on 2007-02-27
> **whizbaby said:**
> It is possible to have an installation with packages from different distros (I don't actually remember how I did it, it was on debian sarge. I think apt-get lets you do that). So simply install dapper (or edgy) and then needed/desired packages from feisty (or any future release). Dependances are resolved and installed, too.
It is possible yes, but I think you'll need to set up a /etc/apt/preferences file to say you want Edgy first unless manually specified different. Synaptic also has an option to prefer Edgy packages. If you do not set this Edgy preference in either program apt will pick the higher version, and that means you're simply doing the manual upgrade to Feisty.

Anyways, mixing up repository versions is somewhat of an advanced topic ;)

---

