---
title: "How do you compile a program?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Nigmah on 2007-06-23
[COLOR=DarkOrange]**I installed a repository, but that didn't really help(it was makeinstall or something along those lines)**[/COLOR]

---

### Post by eljalill on 2007-06-23
Hm. I am not sure what you are trying to do?
A repository is a website/server somewhere, where ubuntu packages are hosted, so you can't really install them. You can basically just add them to your sources in sources.list.

Generally you compile a programm in downloading the source code, unpackaging it, running ./configure in the directory of the source, than doing make and make install (that's in a nutshell), but if you are new to this, you might want to read one of the various HowTos that are on the net about this...

And more information about what exactly you are traing to install would be useful ;) .

best luck!

---

### Post by Phixion on 2007-06-23
make sure you have the package 'build-essential' installed before hand.

```

sudo aptitude install build-essential

```

---

### Post by Sweet Mercury on 2007-06-23
> **Phixion said:**
> make sure you have the package 'build-essential' installed before hand.

```

sudo aptitude install build-essential

```

Is there any reason why build-essentials doesn't come pre-loaded in Ubuntu?

It seems that compiling programs from source is pretty common in Linux...

---

### Post by HotShotDJ on 2007-06-23
> **Sweet Mercury said:**
> Is there any reason why build-essentials doesn't come pre-loaded in Ubuntu? Yes.  Because a vast majority of people using Ubuntu will never, EVER need to compile a program from source.  Space on the installation CD is limited, so things that only a small number of people will need are excluded.  Installing build-essentials later from the repositories is pretty trivial for those that need it.

---

### Post by energiya on 2007-06-23
Compiling your apps is so nice. It gives you control over what you install and it offers a performance boost as a bonus :)

---

### Post by HotShotDJ on 2007-06-23
> **energiya said:**
> Compiling your apps is so nice. It gives you control over what you install and it offers a performance boost as a bonus :)Yes and no.  I ran Gentoo for years, and while it certainly gave me more control over what I installed, there really was little to no performance boost (and I did tweak my compile-time options!).  But I agree that the ability to compile your apps is a great option to have... the operative word being OPTION.

---

### Post by energiya on 2007-06-23
> **HotShotDJ said:**
> Yes and no.  I ran Gentoo for years, and while it certainly gave me more control over what I installed, there really was little to no performance boost (and I did tweak my compile-time options!). 

Compiling some apps gave me a BIG performance boost; programs like wine, thunar, terminal, but for others I couldn't see any difference.

---

### Post by HotShotDJ on 2007-06-23
> **energiya said:**
> Compiling some apps gave me a BIG performance boost; programs like wine, thunar, terminal, but for others I couldn't see any difference.I hope you didn't understand me to be saying that on-site compiling never boosts performance.  Perish the thought!  I'm just saying for most users, it is usually (but not always!) not worth the potential headache -- especially new users.

---

### Post by energiya on 2007-06-23
> **HotShotDJ said:**
> I hope you didn't understand me to be saying that on-site compiling never boosts performance.  Perish the thought!  I'm just saying for most users, it is usually (but not always!) not worth the potential headache -- especially new users.

Headache for them and sometimes for us on the forums (well, you have the learn one way or the other). But once you get the hang of it... it becomes a nice option, like you said.

Cheers

---

### Post by Sweet Mercury on 2007-06-24
> **energiya said:**
> Compiling some apps gave me a BIG performance boost; programs like wine, thunar, terminal, but for others I couldn't see any difference.

Compiling apps boosts performance? How? You don't end up with the same binary that you would have downloaded/gotted from the repository?

I haven't seen much about compiling in an of the tutorial sites I saw. ANy resources on this I could check out?

Thanks.

---

### Post by energiya on 2007-06-24
> **Sweet Mercury said:**
> Compiling apps boosts performance? How? You don't end up with the same binary that you would have downloaded/gotted from the repository?

If you compile it with other flags (I use -march=athlon-xp -O2 -pipe -fomit-frame-pointer) and you play with the ./configure options you don't get a simillar binary. Some apps may offer you a performance boost, some might not. It depends (actualy I haven't seen many offering a "BIG" performance boost, but I found a few).

> **Sweet Mercury said:**
> 
I haven't seen much about compiling in an of the tutorial sites I saw. ANy resources on this I could check out?

That's because each app has its own options and even way of compiling. The "standard" would be ./configure && make && make install , but that's not always true. Usualy there is a README or INSTALL file.

For the regular user (and newbie) compiling could be avoided.

---

### Post by Enverex on 2007-06-24
> **energiya said:**
> Compiling some apps gave me a BIG performance boost; programs like wine, thunar, terminal, but for others I couldn't see any difference.

This is purely fabricated to be honest with you. How exactly did compiling boost performance for Wine, Thunar and the Terminal for you? (the last two should be so fast anyway it's impossible to even tell). Remember, binary packages are just programs someone else compiled, then zipped up and you installed. It's not like compiling is some secret ability that magically makes applications run faster.

It's a placebo effect, as the Gentoo devs if you want a full discussion about it.

---

### Post by energiya on 2007-06-24
Wine - speed increase when starting some apps; about 2-4 seconds, maybe more?; how and why? don't know, maybe because I disable some options. This one I checked with a timer, just to be sure it worths waiting about 15 minutes to compile.
EDIT: it was a different wine version than the binary package... 0.9.3x can't remember. Maybe that's why? :roll: I'm going to try it on the same version, just to be sure.
Thunar - before compiling, when starting it I would get a on-off from the icons, like a refresh. After compiling the icons appear instantly. Hmm... I might have a eye problem? (or my brain isn't working wright)
Terminal - using transparency it would take about 3-4 seconds for the terminal to be usuable when parallel starting (with other apps). After compiling the flickering effect doesn't go away, but it now takes about 2 seconds until I can write my commands. (don't need a timer to see this)

And yes, I know what binary packages are, but I also know it depends how the binary was compiled, with/without any patches, what compiling options. And if you say this doesn't mather, I say its "purely fabricated".

---

### Post by Enverex on 2007-06-24
Wine compiles with support for whatever you have installed on your machine, you need to make sure that ./configure --verbose doesn't show anything missing.

---

### Post by energiya on 2007-06-24
I know.
I think I used  --without-opengl --disable-win16. Not sure. Anyway, I only use it to emulate a few apps I really need and can't find an alternative in linux.

---

### Post by Sweet Mercury on 2007-06-24
> **energiya said:**
> If you compile it with other flags (I use -march=athlon-xp -O2 -pipe -fomit-frame-pointer) and you play with the ./configure options you don't get a simillar binary. Some apps may offer you a performance boost, some might not. It depends (actualy I haven't seen many offering a "BIG" performance boost, but I found a few).


That's because each app has its own options and even way of compiling. The "standard" would be ./configure && make && make install , but that's not always true. Usualy there is a README or INSTALL file.

For the regular user (and newbie) compiling could be avoided.

I hold off on the compiling fun then, for a while.

Thanks.

---

