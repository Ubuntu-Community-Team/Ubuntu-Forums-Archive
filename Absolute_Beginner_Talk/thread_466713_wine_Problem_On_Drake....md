---
title: "wine Problem On Drake..."
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by john wagner on 2007-06-07
**Yep, here I am....again!**  LOL

Thanks, in advance!  I have a problem installing Wine....
I'm running Dapper Drake 6.06, got the libraries etc...  Went to Wine HQ and installed
the correct Wine.  Did the install instructions, and this is what I get:

[COLOR="DarkRed"][SIZE="1"]W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
[/SIZE][/COLOR]
Okay.....  I thought the public key was the open agreement thingee???
I tried reloading all the documentation libraries, reloading Wine etc...  But same thing each time.  I KNOW I'm doing something wrong, but.....  Heh.

thanks
john

---

### Post by zvacet on 2007-06-07
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]

so you need to type this

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
 gpg --export --armor 58403026387EE263  | sudo apt-key add -

---

### Post by john wagner on 2007-06-07
> **zvacet said:**
> [B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]

so you need to type this

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
 gpg --export --armor 58403026387EE263  | sudo apt-key add -

Thanks!  After I do that, I get this...

[COLOR="Red"]gpg:  WARNING:  nothing exported
gpg:  no valid OpenPGP data found[/COLOR]

Nothing happens then...  Sigh.   had it working on my LAST install of 6.06....  Had to re-install my system for various noobie reasons.  Sigh.

john

---

### Post by zvacet on 2007-06-07
Sorry for not been so clear in answering your question.All you need to do is to type first command and hit enter.After that second command and that´s it.Maybe it will be helpfull in the future.Sorry again.

---

### Post by john wagner on 2007-06-09
> **zvacet said:**
> Sorry for not been so clear in answering your question.All you need to do is to type first command and hit enter.After that second command and that´s it.Maybe it will be helpfull in the future.Sorry again.

That's what I did....  Still no wine for me, sigh....  Guess I should just stick to beer.

Thanks for the attempt tho.

john

---

### Post by Nythain on 2007-06-09
if you are trying to install from thier repository here's the gpg key info
```

[I]wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

[/I]

---

### Post by john wagner on 2007-06-09
> **Nythain said:**
> if you are trying to install from thier repository here's the gpg key info
```

[I]wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

[/I]

Okay, from your posting in the other help me with wine thread (heh), I did the whole step by step thingee you laid out for all the noobies.

After winecfg, I get this:

[COLOR="Red"]:~$ winecfg
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
[/COLOR]

I tried looking for the libraries using the advanced search on add/remove, didnt find squat.
How do I get the appropriate libraries?

thanx!
john

Hmmm, interesting what it does to : ] (without the space....) and : ) etc......

---

