---
title: "Third party repo vs compiling from source"
date: 2011-12-22
forum: Any Other OS
---

### Post by CharlesA on 2011-12-22
Hiya,

I'm just wondering what the benefits/disadvantages are to using a third-party repo such as [RPMforge]("http://wiki.centos.org/AdditionalResources/Repositories/RPMForge"), vs compliling a program from source.

The program(s) in question are apcupsd and maybe htop/uprecords.

Any thoughts?

Thanks! :)

---

### Post by jjex22 on 2011-12-23
Hi there! Basically thus:

third party repos:
pros
-extra packages
-potentially newer packages than current repos
-packages may be maintained for longer than current repos (plus auto update
-installation much faster and less complicated than source

Cons
-security; can you trust the repo's security - quality control?
-may well become unsupported without notice
-packages pre compiled


Source:
pros
-more packages
-always get the latest packages
-choose modules and module options
-you wont accidentally update to an unwanted version

cons
-time; for large packages such as codeblocks, or worse DE's this can be a real factor - especially dependencies
-no auto update
-security; check the download location
-you don't know about compatability until you install it.

For small packages like these, if they aren't in the repo's i'd probably source them... I've not seen htop 1.0 in repo's yet, but I've also not checked for 2 weeks, but that does seem to be a great repo for cent, so I'd be inclined t add it anyway!

On the subject of RHEL package management - Haven't had a chance to try 6 yet, is yum history now available? I assume so as it was announced for RHEL 6, Really hoping so - when that came to Fedora I was close to emailing Mark himself for an apt version!

---

### Post by CharlesA on 2011-12-23
Thanks for the breakdown. I was a bit worried when they mentioned that you'd be trusting the entire repo if you decided to install it.

I'll probably just compile those two from source since they are small programs and there are only two of them at the moment.

As for the yum history thing, is this what you meant?

```
ID     | Login user               | Date and time    | Action(s)      | Altered
-------------------------------------------------------------------------------
     7 | root <root>              | 2011-12-22 11:31 | Install        |    5
     6 | root <root>              | 2011-12-22 11:28 | Install        |    2
     5 | root <root>              | 2011-12-22 11:27 | Install        |    1
     4 | root <root>              | 2011-12-22 11:25 | Install        |   58
     3 | root <root>              | 2011-12-22 11:23 | Install        |    8
     2 | root <root>              | 2011-12-22 11:20 | Update         |   21
     1 | System <unset>           | 2011-12-22 10:37 | Install        |  610
history list

```

---

### Post by jjex22 on 2011-12-23
That's it - its a pretty basic feature, but I find it really useful in fedora, especially when you're setting up and your adding quite a few things, then you realise some things not right, you can undo your yum mods.

For example in your yum history 7 was the last thing you did, if you then noticed something had gone wrong, you can just do

```

yum history undo 7

```
to undo that 'transaction', or if you then realised that it wasn't that one which caused the problem:
```

yum history redo 7

```

you can also see what each transaction actually was by typing
```

yum history info 7

```

like I say its pretty basic, but surprisingly useful!

*Currently downloading cent 6 :)*

---

### Post by CharlesA on 2011-12-23
That's pretty awesome, actually. I don't think apt has the same thing, does it?

I did a netinstall of 6.2. ;)

---

### Post by jjex22 on 2011-12-23
Ah I'm at my Mother's for Christmas and only have the netbook, so just downloaded it for later :D I quite want to get a chance to compare it to clear os now that that's direct from RHEL too!

Um well I suppose synaptic has a history feature, which is of course useful but lets face it it's a little less impressive in a gui front end. As far as I know apt can't do this in the CLI -neither aptitude nor dselect are able to display the history as far as I've been able to find. 

i suppose it's a very small feature to rave about, but for myself I tend to test out distros in full, but if I decide I want to keep it for a bit, I tend to (where possible) install a minimal environment and build up from there, so it can be really useful if you select the wrong package, but on fedora I found I used it most when updates changed things, though hopefully this will be less common in cent as it's meant to be more stable than fedora!

---

### Post by CharlesA on 2011-12-23
Thank you for your help! :)

---

