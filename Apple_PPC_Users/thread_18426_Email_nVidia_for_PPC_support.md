---
title: "Email nVidia for PPC support"
date: 2005-03-06
forum: Apple PPC Users
---

### Post by Viro on 2005-03-06
I know about the petition for nVidia to support PPC hardware. Since that has been going on for some time, with no visible effect, I doubt it is reaching the people at nVidia. I propose we do something more.

Let all PPC users politely email  [linux-bugs@nvidia.com](mailto: linux-bugs@nvidia.com) and politely ask them for PPC Linux support. If we spread this to every PPC Linux user who wants nVidia to support the PPC platform, I'm sure we'll get loads of people.

Hopefully, if everyone is polite, we'll finally get support for PPC Linux or at least make them aware that there are loads of users who want PPC Linux support.

---

### Post by daniels on 2005-03-06
If you do this, nVidia's reaction to PPC users will just be 'oh, those annoying guys who spam linux-bugs@'.  Misusing nVidia's resources that they provide won't get you PowerPC support -- if anything, the only thing it will get you is linux-bugs being closed off, or restricted to certain known people.

---

### Post by Viro on 2005-03-06
Good point. But what would you suggest as an alternative? I agree that this could somewhat annoy nVidia, but there doesn't seem to be any other viable alternative.

---

### Post by scotty on 2005-03-06
I don't think that the vast majority of Linux users know HOW to be polite...Did you actually read some of those comments on the signatures for that petition?

Stuff life "me want nvidia drivers" just isn't going to cut any ice with nVidia.

I don't know if an email campaign will work either.

I don't suppose that anyone can compile the drivers from source?

Scott

---

### Post by toojays on 2005-03-06
Maybe one of you should set up a bounty for the particular features you want to see support for. Getting the features you want put directly into Xorg or Linux would be better than getting a proprietry binary from nvidia.

---

### Post by DJ_Max on 2005-03-06
[QUOTE=scotty]
I don't know if an email campaign will work either.
[/QUOTE]
I doubt it, unless there's money involved.
[QUOTE=scotty]
I don't suppose that anyone can compile the drivers from source?[/QUOTE]
No, both ATI & nVidia drivers are closed source.

---

### Post by Viro on 2005-03-07
Bounty sounds plausible. How does one set such a thing up? I mean, if everyone who voted on that petition contributes just $1, you've got quite a bit of money.

That leaves us with the problem of who to approach to develop the driver.

---

### Post by daniels on 2005-03-07
Unfortunately even the most skilled driver developer cannot properly write a driver for modern cards in any reasonable length of time (it will be very much obsolete by the time they finish, if ever) without the specs, which nVidia simply will not issue.

While it sucks, the only thing to do is wait.  nVidia will release the source to their driver, or release specs to the right people, when they are ready to do so.  Petitions and bounties won't change that.

---

### Post by toojays on 2005-03-08
Well a bounty isn't a panacea, but it might help, if it could attract the right people. The real issue is that for seriously difficult challenges, the bounty would need to be seriously large, somewhere in the range $5k to $500k, depending on the nature of the project. And by that time, "bounty" is probably the wrong word . . .

I've been thinking lately that the Free Software community really needs some organisation which can help to concentrate funds to organise Free Software contracts. Basically I'm thinking of something like a bugzilla, but with an additional field like "pledge $X to the person who fixes this bug".

Okay, I've drifted off topic. I just wanted to object to Daniel's comment that "even the most skilled driver developer cannot properly write a driver for modern cards in any reasonable length of time". The most skilled driver developers *can* do it. Specifically I'm thinking of benh and the ATI drivers. Not that I know what motivates him, or where he finds the time to do what he does.

I do agree that petitions are a complete waste of time in this case. But if we could collectively put our money where our mouth is . . .

---

### Post by daniels on 2005-03-08
The qualifier here is 'without the specs'.  Ben has the specs for all the Radeons, driver development kits (which contain more extended programming guides, and a sample X.Org driver), and access to development people at ATI who will answer his queries (as do a few other X hackers).  nVidia would not give you this.

---

### Post by toojays on 2005-03-08
I don't think Ben has the full specs for 9200 or newer yet. Certainly the sleep code was reverse engineered from  the OS X driver, see [this post from linuxppc-dev](http://ozlabs.org/pipermail/linuxppc-dev/2004-October/017693.html).

What I was getting at was that if we had massive gobs of cash, and could hire people to do the work, the problem of specifications would not be as great as it is now. There are plenty of examples where we *have* specs, and yet the implementation is far from perfect.

My feeling is that if there was a mechanism which made it easy for individual users to pool their funds towards *concrete* goals, we would be able to do something about the problem, rather than just whining and signing petitions.

---

### Post by meyerm on 2005-03-10
Take it all in your hands - even the hardware. :D

Please see [http://www.opengraphics.org](http://www.opengraphics.org) for a currently developed graphic card, open/free as in speach of course. The latest status is an ASIC - all specs for development will be available and perhaps even the hardware design of the chip itseld (currently there is a discussion about that on the ML).

It will not run DOOM3 (TuxRacer should work nonetheless ;-) ); but it will be PCI and AGP (-> MultiHead *g*), later PCIe, passivly cooled and - most important - it will have free drivers and BIOS for x86, Mac-PPC, standard PPC etc.  :-)

This is all not just a dream by some freaks. There is a company behind which currently creates higher end graphic cards. And of course they want to make money with it - and they see the chance that there are many companies interessted in buying an embedded design which has open source drivers. And of course a lot of geeks who will buy the PCI/AGP/PCIe graphic card (I will when the drivers are good enough...). So it could really work.

---

### Post by Viro on 2005-03-10
[QUOTE=meyerm]Take it all in your hands - even the hardware. :D

Please see [http://www.opengraphics.org](http://www.opengraphics.org) for a currently developed graphic card, open/free as in speach of course. The latest status is an ASIC - all specs for development will be available and perhaps even the hardware design of the chip itseld (currently there is a discussion about that on the ML).

It will not run DOOM3 (TuxRacer should work nonetheless ;-) ); but it will be PCI and AGP (-> MultiHead *g*), later PCIe, passivly cooled and - most important - it will have free drivers and BIOS for x86, Mac-PPC, standard PPC etc.  :-)

This is all not just a dream by some freaks. There is a company behind which currently creates higher end graphic cards. And of course they want to make money with it - and they see the chance that there are many companies interessted in buying an embedded design which has open source drivers. And of course a lot of geeks who will buy the PCI/AGP/PCIe graphic card (I will when the drivers are good enough...). So it could really work.[/QUOTE]
 How is that going to work with existing Powerbooks? Answer: it isn't.

---

### Post by meyerm on 2005-03-10
[QUOTE=Viro]How is that going to work with existing Powerbooks? Answer: it isn't.[/QUOTE]
Sure - that's true. But this thread wasn't about Powerbooks but PPC. I have a PPC myself and I'm really looking forward for this card :D

But I don't think either that Powerbooks in the future can be equipped with that chip since I don't believe that Apples jumps onto the "exchangeable graphic card for notebooks" train. However, I would be very happy if I'm wrong here :-)

---

### Post by s_p_a_r_k_y on 2005-03-24
There is this website that has gotten quite a response from websites for its submitted petitions. check out [www.linuxappeal.net](www.linuxappeal.net). There are some PPC linux petitions asking companies for drivers and software for that as well as AMD64 support for several products.

I have written several petitions and a few companies replied to me...mostly saying that they appreciate user feedback, but hopefully it will accomplish something.

---

