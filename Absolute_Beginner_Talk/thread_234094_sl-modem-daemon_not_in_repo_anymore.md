---
title: "sl-modem-daemon not in repo anymore?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Sunnz on 2006-08-11
I am following this tute:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)


to install my modem... I am up to "Modems supported by ALSA drivers (snd_atiixp_modem, snd_via82xx_modem, snd_intel8x0m)" part...

It said that I can install sl-modem-daemon package, but I can't find it? All repo has been enabled in synaptic (except for CDs.)

---

### Post by rowanparker on 2006-08-11
It worked perfectly fine for me.

Although I do have some debian repos in me sources.list:> Edit:Removed entry in sources.list, see further posts for reasoning.
Don't know if that's got anything to do with it.


If not, you can download it [here]("http://packages.ubuntu.com/dapper/misc/sl-modem-daemon").
Rowan.

---

### Post by az on 2006-08-11
> **Sunnz said:**
> I am following this tute:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)


to install my modem... I am up to "Modems supported by ALSA drivers (snd_atiixp_modem, snd_via82xx_modem, snd_intel8x0m)" part...

It said that I can install sl-modem-daemon package, but I can't find it? All repo has been enabled in synaptic (except for CDs.)
Do *NOT* used debian repos.  Ever.

sl-modem-deamon is in multiverse:
[http://packages.ubuntu.com/dapper/misc/sl-modem-daemon](http://packages.ubuntu.com/dapper/misc/sl-modem-daemon)

---

### Post by rowanparker on 2006-08-11
> **azz said:**
> Do *NOT* used debian repos.  Ever.
Why not may I ask?

---

### Post by az on 2006-08-11
> **rowanparker said:**
> Why not may I ask?

Because Debian and Ubuntu are not binary-compatible.

You can backport a package by compiling it from source.  But don't try to mix debian and Ubuntu binary repositories.  The package manager nor the package maintainers do not take into account installing a package on a different distro.

---

### Post by rowanparker on 2006-08-11
Oh, ok.

Well the only reason the were in my repos was because I needed something from them (can't remember what) and I do think i compiled it from source.

Rowan.

---

### Post by Sunnz on 2006-08-12
> **azz said:**
> Do *NOT* used debian repos.  Ever.

sl-modem-deamon is in multiverse:
[http://packages.ubuntu.com/dapper/misc/sl-modem-daemon](http://packages.ubuntu.com/dapper/misc/sl-modem-daemon)
Thanks.

---

