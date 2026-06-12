---
title: "wine on g4"
date: 2007-01-31
forum: Apple PPC Users
---

### Post by Jorge32 on 2007-01-31
hey, I just wanted to know if wine runs on powerpc, because I probably buy a G4 ibook.
It's kind of urgent for me to know, and on absolute begginer I've got no response,
so please, can anybody tell me, does wine runs on powerpc on a g4?:confused:

---

### Post by pay on 2007-01-31
Well there are no binaries for it and I'm not sure if it compiles G4. After all gentoo doesn't have a wine ppc ebuild so I guess that it wouldn't. But I maybe wrong.

---

### Post by 3rdalbum on 2007-02-01
No, Wine doesn't run on PowerPC, as Windows doesn't either.

But if the computer has Mac OS installed, there's a virtualiser you can install through apt-get that lets you run your existing Mac OS installation in a window in Ubuntu. It's called Mac-on-Linux, or MoL for short.

---

### Post by tcuzela on 2007-02-02
I can attest to Wine's dislike for PowerPC.  I'm a returning newbie to the Linux world (long time Mac fan) and have found that Linux isn't like Mac OS or Windows.  After wading through 3 dozen distros you have to make sure it's PPC compatible.  I don't know why I thought, hey it says Linux, it'll work.

I've now flucked up my apt and etc and .list and updater so bad trying to install Wine that I'm ready for a clean install just to get rid of the handful of popups...you're system can't load... or, software sources can't...  It's just like XP now with all the notifiers!

---

### Post by pauljwells on 2007-02-02
NO

you absolutely can't run wine on any ppc based computer. Wine is, put crudely, a set of utilities that 'trick' windows executables into thinking they are running on a windows machine.

It all needs to be on an x86 processor to work.

---

### Post by brackishboy on 2007-02-03
Ah, yes, the old 'x86 software on PPC' conundrum.

After hacking away at NDISWrapper for a solid hour only to realise that it was designed to work on x86... *slaps head with hand*

---

### Post by pauljwells on 2007-02-04
heh heh heh

oh yes, I learned this the hard way too ;)

I'd still buy the iBook, get a copy of VirtualPC off ebay (I just sold mine for £40) for XP (s l o w though) and find alternatives to windows stuff in either Ubuntu or OSX

If you're a gamer then get an Alienware or something...

---

### Post by Peter76 on 2007-02-04
There are some threads on the internet about running wine through qemu on PPC. I gave it a try sometime ago, but didn' have much luck ( and time ). But I think it is still worth looking into.

---

### Post by dombleu on 2007-02-05
I guess that if you are a real hardcore debugger and if you got a lot of spare time. You should be able to get wine running using a qemu virtual machine wich would allow you to run a i386 linux distro on your mac. It would nothing more than a sluggish curiosity but i've came accross a site of a man who documented online how he managed to nail a jell-o in the wall, so if it means something for you...

dom

---

### Post by grazie on 2007-02-06
> **dombleu said:**
> ... but i've came accross a site of a man who documented online how he managed to nail a jell-o in the wall, so if it means something for you...

dom
That's really funny (Jelly for us Brits). Why do I want to visit fhat site? What a weird world we live in!

---

