---
title: "[SOLVED] VLC 0.9.6 wma problem"
date: 2008-12-10
forum: Arch and derivatives
---

### Post by Dr Small on 2008-12-10
WMA's just randomly quit working, so I just upgraded VLC to see if it would fix the problem. It didn't. Anyhow, the error that I received before and after the upgrade is this:

```
[00000371] dmo decoder error: DecOpen failed
Win32 LoadLibrary failed to load: wma9dmod.dll, /wma9dmod.dll, /usr/lib/win32/wma9dmod.dll, /usr/local/lib/win32/wma9dmod.dll, /usr/lib/codecs/wma9dmod.dll, /usr/local/lib/codecs/wma9dmod.dll
```

Looks like it is missing a wma decoder, but I don't have any idea how to get it back. Anyone else have some suggestions?

---

### Post by kostkon on 2008-12-10
> **Dr Small said:**
> WMA's just randomly quit working, so I just upgraded VLC to see if it would fix the problem. It didn't. Anyhow, the error that I received before and after the upgrade is this:

```
[00000371] dmo decoder error: DecOpen failed
Win32 LoadLibrary failed to load: wma9dmod.dll, /wma9dmod.dll, /usr/lib/win32/wma9dmod.dll, /usr/local/lib/win32/wma9dmod.dll, /usr/lib/codecs/wma9dmod.dll, /usr/local/lib/codecs/wma9dmod.dll
```

Looks like it is missing a wma decoder, but I don't have any idea how to get it back. Anyone else have some suggestions?
I'll ask the obvious: do you have the *w3codecs* installed?

---

### Post by Dr Small on 2008-12-10
> **kostkon said:**
> I'll ask the obvious: do you have the *w3codecs* installed?
w3codecs isn't in the repositories, but I'm installing *codecs* to see if that will help. Strange thing is, WMA's have worked fine in the past.

---

### Post by kostkon on 2008-12-10
> **Dr Small said:**
> w3codecs isn't in the repositories, but I'm installing *codecs* to see if that will help. Strange thing is, WMA's have worked fine in the past.
I meant *w32codecs* (or *w64codecs*) from the [*Medibuntu* repo]("http://medibuntu.org/").

Strange that VLC is looking for these codecs. I always thought it uses only its own and never tries to use any external ones.

I suppose the devs changed their policy in the new version.

---

### Post by Dr Small on 2008-12-10
> **kostkon said:**
> I meant *w32codecs* (or *w64codecs*) from the [*Medibuntu* repo]("http://medibuntu.org/").

Oh, haha. Well, Arch doesn't have w32codecs, but installing the package *codecs* solved the problem in short order!

> **kostkon said:**
> 
Strange that VLC is looking for these codecs. I always thought it uses only its own and never tries to use any external ones.

I suppose the devs changed their policy in the new version.
I thought so too, but perhaps this new policy change is to help them, so their product can be used internationally (aka, Ubuntu) and not infringe on any copyright rules.

Either way, installing codecs worked, and now WMA's work again. :) Thanks for the tip in the right direction!

Dr Small

---

### Post by kostkon on 2008-12-10
> **Dr Small said:**
> Oh, haha. Well, Arch doesn't have w32codecs, but installing the package *codecs* solved the problem in short order!

Oooops! My mistake! It's late here, that why... I should be sleeping instead of answering posts :oops::oops:
> **Dr Small said:**
> I thought so too, but perhaps this new policy change is to help them, so their product can be used internationally (aka, Ubuntu) and not infringe on any copyright rules.

Either way, installing codecs worked, and now WMA's work again. :) Thanks for the tip in the right direction!

Dr Small
:p:p

---

### Post by Dr Small on 2008-12-10
> **kostkon said:**
> Oooops! My mistake! It's late here, that why... I should be sleeping instead of answering posts :oops::oops:


Don't fret it. If you wouldn't have tipped me off, I may not have solved the problem tonight ;)

---

