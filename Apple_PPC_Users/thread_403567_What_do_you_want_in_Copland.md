---
title: "What do you want in Copland?"
date: 2007-04-07
forum: Apple PPC Users
---

### Post by 3rdalbum on 2007-04-07
*Copland is my new PowerPC distribution*

I've just implemented a workaround to the iMac blank screens bug in Copland. I want to use this long weekend to do some serious Copland hacking to add as many useful new features to the distribution before the release of Feisty (I will migrate to the Feisty base as the release is so close).

So, this is YOUR distribution. What do you want in it? Preferably things that you currently have to do some command-line hacking for, that I can GUI-ise. Like certain hardware support. If you can think of something that really needs to be done, and can link to a HOWTO for me, I'll do my best to implement it.

I want this distribution to be really useful to Mac users, not just a stripped-down version of Xubuntu.

Thanks, and I hope to get some suggestions soon.

---

### Post by devonatron on 2007-04-07
Easy to follow instructions for setting up  airport

---

### Post by 3rdalbum on 2007-04-07
> **devonatron said:**
> Easy to follow instructions for setting up  airport

I knew someone would say that :-)  So I added the Airport Extreme driver to the distribution tonight. I haven't tested it - I don't have an AE card, but it *should* automatically load on startup.

---

### Post by ZoiaGuyver on 2007-04-07
I would def like to see more inbuilt media/building librarys. 

I mean its all good being able to apt-get the stuff but tbh i think the librarys should be there in the first place. Things like build-essential, some of the make builds and some of the gcc stuff that isnt installed as standard should def be in there. Imo i would like to see a better support for building from source than is currently in ubuntu (im a Gentoo user aswell so i guess i miss that part) apt-get is great but for some stuff like gfire (gaim xfire plugin) things like the dev libs are needed it would be nice to see some of the dev stuff included as standard. It would be nice to possibly see the EFL librarys in a distro other than Elbuntu, also some of the ibm java stuff.

As far as hardware goes i think ubuntu does most of it (especially if youve already done the workaround for the blankscreen prob), but possibly include a few more sound librarys like the alsa-oss wrapper and things like that. 

I think Copland tbh could be just what the PPC community needs. Finally a distro thats built for Mac PPC hardware.

I use various macs and would like to see the inclusion of make opts like gentoo has for optimising builds, things like being able to use make.conf to enable altivec and a G3/G4 processor optimisation much like gentoo has.

I know a lot of this is hard work but i think to make a decent distro for PPC, these are the things that are needed as tbh ubuntu imo has this as the one major weakspot for PPC users.

Ahhh almost forgot maybe a better network manager prog :P one that doesnt need to be messed about with so much to get the Wireless going. Ive heard WCID or something like that is a much better one for mac users (ill try and find the link that i read about it later)

---

### Post by Auria on 2007-04-07
This is probably something that's not part of your vision... but let's try anyway! :)  XFCE doesn't really appeal to me, i'd like a way to install gnome (even if it's not extremely easy)

Perhaps also a graphical way to setup network, if any exists... i find it ridiculous to have to configure my (very common DSL) internet connection with secret commands on the terminal, and to have to manually edit the output file afterwards because it generates invalid config files - i think i have heard of a better alternative than what Ubuntu currently uses unfortunately i can't rememer what was its name

I think it was already in your todo (or done) list, but something like mac-on-linux installed by default, that works without so many obscure terminal stuff

Oh yeah and also : is there a website for Copland? i can't seem to find aything compelling

---

### Post by fkdev on 2007-04-07
If gnash could be included by default, but built with a different rendering interface, that would be wonderful. Cairo would probably work well; users could install glitz if they want to do GL.
A more customizable install (a little like debian's expert install option) wouldn't hurt anybody.
Yaboot configuration could be made a little easier; a GUI for that could be a good idea.

EDIT: Note that if you're using the  second alpha for your gnash build, you shouldn't use cairo. In the second alpha cairo support is experimental and there is no browser plugin support. I think that has changed in CVS. In this case, AGG (which is also for 2d rendering but lacks support for stuff like glitz and is not used as much, but which had support written for before Cairo)

---

### Post by dpny on 2007-04-07
> **Auria said:**
> This is probably something that's not part of your vision... but let's try anyway! :)  XFCE doesn't really appeal to me, i'd like a way to install gnome (even if it's not extremely easy)

Perhaps also a graphical way to setup network, if any exists... i find it ridiculous to have to configure my (very common DSL) internet connection with secret commands on the terminal, and to have to manually edit the output file afterwards because it generates invalid config files - i think i have heard of a better alternative than what Ubuntu currently uses unfortunately i can't rememer what was its name

I think it was already in your todo (or done) list, but something like mac-on-linux installed by default, that works without so many obscure terminal stuff

Oh yeah and also : is there a website for Copland? i can't seem to find aything compelling

I will agree with this: I tried XFCE and found it to lack a lot of the features Gnome has.

---

### Post by 3rdalbum on 2007-04-08
Wow, lots of great comments! Thanks for the feedback!

1. From memory, build-essential is installed by default already. To be honest, I don't see a need to include more development headers; which ones would be included? It would also blow out the size of the installation... I want this thing to be as lean as possible, or it won't run on my test machine :-)

2. The alsa-oss wrapper is a great idea, and it will be included at some point.

3. Thanks for the network management suggestion. Mine works perfectly OOTB, so I'm not familiar with these sorts of programs. I'll check out WCID.

4. Gnome is easily installable through Synaptic - it'll install a default Ubuntu Gnome. The same goes for KDE or any other window manager in the Ubuntu repos.

5. I'll need someone to take on the MoL GUI configuration project; I don't think my Mac would run MoL at all. MoL is included by default though.

6. A text-based Ubiquity frontend is one of my goals, again I'd appreciate it if someone else could make it happen. I'll investigate if it can have more power too.

7. Thanks for the Gnash recompilation suggestion. This is one perfect reason why a PowerPC-specific distribution is necessary.

8. Yaboot configuration - what do you need to configure?

Great ideas everyone - keep them coming.

---

### Post by Auria on 2007-04-08
> **3rdalbum said:**
> 
5. I'll need someone to take on the MoL GUI configuration project; I don't think my Mac would run MoL at all. MoL is included by default though.


In the past after lots of trial and error with various commands i got mac-on-linux to work... unfortunately since then i wiped my hard-drive and reinstalled a fresh installation, so i lost all instructions i had... it's kinda hard to get working, the instructions are messy and outdated

(EDIT: OMG! It's been updated!! last time i checked it dated from 2004)


however, if i get instructions from many people on how they get MOL to work on their computer, i could most probably write some easy-to-use graphical interface.

Just a shame that MOL seems dead now. i don't think think i have the knowledge to maintain it myself

BTW you didn't answer my question: does Copland have a website?

---

### Post by jackoverfull on 2007-04-08
hi, i discovered this distribution first time a couple of days ago, but i was not able to find any download location.

I'm really interested in testing (and maybe helting in developing) it and can dedicate an imac g3 to this.

---

### Post by dpny on 2007-04-08
> **Auria said:**
> In the past after lots of trial and error with various commands i got mac-on-linux to work... unfortunately since then i wiped my hard-drive and reinstalled a fresh installation, so i lost all instructions i had... it's kinda hard to get working, the instructions are messy and outdated

(EDIT: OMG! It's been updated!! last time i checked it dated from 2004)


however, if i get instructions from many people on how they get MOL to work on their computer, i could most probably write some easy-to-use graphical interface.

Just a shame that MOL seems dead now. i don't think think i have the knowledge to maintain it myself

I have MOL on my Pismo. I did have to compile from source, but it was a relatively painless process.

---

### Post by spikee on 2007-04-08
please include swfdec for flash. [http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/)

---

### Post by 3rdalbum on 2007-04-09
I've got Gnash for Flash; right now it's using the OpenGL backend which is less than ideal.

Website (updated quite rarely): [http://code.google.com/p/coplandppc/wiki/MainPage](http://code.google.com/p/coplandppc/wiki/MainPage)

Personal Blog (updated more often): [http://bigbolshevik.blogs.friendster.com/a_man_and_his_penguin/](http://bigbolshevik.blogs.friendster.com/a_man_and_his_penguin/)

There is no download location at the moment, as there are a few unresolved problems with it. I think I might release it soon anyway and see if maybe it's just my hardware.

---

### Post by ZoiaGuyver on 2007-04-09
Well ive just been reading your Wiki and Blog. 

Tbh you seem to have a lot of good ideas for the build, although im unsure of the choice of XFCE as the UI. Surely if you wanna have a fast desktop that outclasses anything else for a PPC arch Enlightenment DR17 would have been better (even E16 if you want it to be a slightly more "stable" release).

 I know E17 has binarys for Debian Etch/Ubuntu Edgy from mental-ppc. Ive used them on both Edgy and and Etch. I find E17 to be faster than XFCE even with things like transparancy and flames on :P. Also E17 seems to luv the inbuilt ATI cards in the older macs and allows them with a edited xorg.conf to run things like composite (although slowly if you have a low memory).

Just a suggestion really as tbh Xubuntu has the XFCE side of things covered (not that i like it much normally switch to enlightenment anways). I know we have Elbuntu aswell but tbh thats a mouthfull :P much rather Copland E17 :lol:

Being serious though although Enlightenment isnt the easist thing to use its def the most configurable UI around and can be made to look near enough OS X. I found it to be a easy switch from OS X to E. 

E has to be about the most "eye-candy" non CPU hog UI around and is getting better with every build they release. Its stable if you use the older 32 build (supplied in the mental-ppc repo's) and not the 37 build (latest). It also has a lot of features that make Gnome, KDE and XFCE apps available. 

Add the fact its menus can be totally customised, everything in the UI can be changed to how the user wants it, plus its slick/fast and totally blows everything else away.

If you wanna see it for yourself the edgy repo's are active.

deb [http://mental-ppc.tuxfamily.org/dists](http://mental-ppc.tuxfamily.org/dists) edgy-mppc all
deb-src [http://mental-ppc.tuxfamily.org/dists](http://mental-ppc.tuxfamily.org/dists) edgy-mppc all

Oh and the they are signed

wget [http://mental-ppc.tuxfamily.org/dists/817D0754.gpg](http://mental-ppc.tuxfamily.org/dists/817D0754.gpg) -O- | sudo apt-key add -

Take a look i would def recommend it for anyone running the lower Macs with ATI Rages.

---

### Post by 3rdalbum on 2007-04-09
I have E17 on my x86 machine, and it kinda feels like there's something missing. I can't put my finger on it, and I know a lot of people love it, but it doesn't feel right. I think I had the same feeling when I used OS X.

I've used E16 on my iMac; good performance but I got the same kind of feeling.

And the latest XFCE felt just right to me.

HOWEVER, I'm seriously considering a change of DE (after the first release), find a better lightweight display/login manager, and also include Openbox for really low spec machines. XFCE has a serious bug I can't seem to squash, and if it's not sorted out in Feisty then I'll switch DE.

---

### Post by ZoiaGuyver on 2007-04-09
Something missing :-k 

Its probably the Desktop icons :lol: only kidding :D

I know what you mean, but tbh i get the same feeling with XFCE, this i spose it what linux is all about though its ppl's choices that make such a great OS :D.

I would suggest wdm as a login manager (but i know plenty of ppl who dont like it cause its pretty plain/boring :p)

---

### Post by walter_f on 2007-04-09
> **Auria said:**
> however, if i get instructions from many people on how they get MOL to work on their computer, i could most probably write some easy-to-use graphical interface.

Just a shame that MOL seems dead now. i don't think think i have the knowledge to maintain it myself

To me, Mac-on-Linux (M-O-L) seems to be pretty much alive and kicking.

M-O-L is available on sourceforge.net, now under a GPL licence:

[http://sourceforge.net/projects/mac-on-linux/](http://sourceforge.net/projects/mac-on-linux/)

Actually, M-O-L has been updated already twice this year, i.e. in January and in March, 2007.

"The reports of my death are greatly exaggerated." -- Mark Twain.

;-)

Regards to all,

Walter.

---

### Post by jackoverfull on 2007-04-09
> **3rdalbum said:**
> I've got Gnash for Flash; right now it's using the OpenGL backend which is less than ideal.

Website (updated quite rarely): [http://code.google.com/p/coplandppc/wiki/MainPage](http://code.google.com/p/coplandppc/wiki/MainPage)

Personal Blog (updated more often): [http://bigbolshevik.blogs.friendster.com/a_man_and_his_penguin/](http://bigbolshevik.blogs.friendster.com/a_man_and_his_penguin/)

There is no download location at the moment, as there are a few unresolved problems with it. I think I might release it soon anyway and see if maybe it's just my hardware.

ok, i'll look sometimes and wait for builds…

---

### Post by ssam on 2007-04-09
can the imac screen fix be pushed into ubuntu? how exactly does it work?

network manager works well for me with an original airport

swfdec can play youtube videos

---

### Post by fkdev on 2007-04-09
Setting up dual-boot linux (in yaboot) would probably be annoying to some users.
Not really that important, was just a suggestion.

---

### Post by dpny on 2007-04-09
This list may repeat some things already said, but here's my wants:

1) Full multi-media support, within what's available in PPC Linux;
2) Latest kernel/updates to fix annoying bugs, like the Powerbook sound issues;
3) Latest Samba.

All I can think of right now.

---

### Post by Auria on 2007-04-09
> **walter_f said:**
> To me, Mac-on-Linux (M-O-L) seems to be pretty much alive and kicking.

M-O-L is available on sourceforge.net, now under a GPL licence:

[http://sourceforge.net/projects/mac-on-linux/](http://sourceforge.net/projects/mac-on-linux/)

Actually, M-O-L has been updated already twice this year, i.e. in January and in March, 2007.

"The reports of my death are greatly exaggerated." -- Mark Twain.

;-)

Regards to all,

Walter.

Yes i know, as i added in an edit afterwards - it's just that last time i checked (it was only a few months ago or so) the website said "last updated: 2004" and it also stated that documentation was not up to date
but now it's alive again so great

---

### Post by anurse on 2007-04-10
I'd like to thank you for the work on Copland. I'm really looking forward to it. A easily working wireless is my one request (others have mentioned this). Regardless of requests, however, this is an impressive sounding project. Congrats.

---

### Post by kihei-blueberry on 2007-04-11
I know it might sound crazy with everybody here asking for the kitchen sink, but what I would really like to see is a mini-distro like Damn Small Linux for PPC. A well- configured Fluxbox isn't flashy, but functional and blazing fast.

---

### Post by 3rdalbum on 2007-04-11
> **ssam said:**
> can the imac screen fix be pushed into ubuntu? how exactly does it work?

Not at all, at the moment! When my virus scan is done I'll build another CD image that hopefully will work.

It's basically a program that you run on the command-line, that copies in a good Xorg and restarts XDM. The Yaboot screen has also been edited to mention it. This was only ever meant as a stop-gap measure until Feisty's improved Xorg.

---

