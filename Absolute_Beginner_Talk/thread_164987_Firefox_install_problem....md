---
title: "Firefox install problem..."
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Lord_Drakkus on 2006-04-23
Being as security minded as I am, I want the latest version of Firefox that I can get.  And no matter which version I try, 1.5.0.2 or 1.5.0.1 I keep getting the same error.  I've tried installing it via the Wiki as well as aysiu's installer script....

The primary error that I get is "Error converting from UTF-8 to STRING: Coversion from characer set 'UTF-8' to 'ISO-9959-1' is not supported".  Which is repeated about 50-100 times, and then errors out...

I'm running Breezy AMD64 and I even tried the Swiftfox athlon64 build, same error... ](*,)   I'm getting a bit upset here...  Since I can't seem to get anything to install at all that's not in Synaptic (and some things that I got through that aren't working either).

---

### Post by trent dillman on 2006-04-23
You could always try to compile from source:
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.2/source/firefox-1.5.0.2-source.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.2/source/firefox-1.5.0.2-source.tar.bz2)

---

### Post by aysiu on 2006-04-23
I don't think they make an AMD64 build of Firefox.

---

### Post by Lord_Drakkus on 2006-04-23
> **trent dillman]You could always try to compile from source:
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.2/source/firefox-1.5.0.2-source.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.2/source/firefox-1.5.0.2-source.tar.bz2)[/QUOTE]

Tried that...  here's the actual error text (From the point I *believe* the error starts)

/usr/bin/ld: jsapi.o: relocation R_X86_64_PC32 against `memset@@GLIBC_2.2.5' can not be used when making a shared object said:**
> : *** [libmozjs.so] Error 1
make[4]: Leaving directory `/home/drakkus/mozilla/firefox-bin/js/src'
make[3]: *** [libs] Error 2
make[3]: Leaving directory `/home/drakkus/mozilla/firefox-bin/js'
make[2]: *** [tier_2] Error 2
make[2]: Leaving directory `/home/drakkus/mozilla/firefox-bin'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/drakkus/mozilla/firefox-bin'
make: *** [build] Error 2

](*,)

[QUOTE=aysiu]I don't think the make an AMD64 build of Firefox.
Yes they do, although it's third party...
[http://getswiftfox.com/tr-ath64.htm](http://getswiftfox.com/tr-ath64.htm)

---

### Post by aysiu on 2006-04-23
[QUOTE=Lord_Drakkus]
The primary error that I get is "Error converting from UTF-8 to STRING: Coversion from characer set 'UTF-8' to 'ISO-9959-1' is not supported".  Which is repeated about 50-100 times, and then errors out...[/QUOTE] First of all, [you're not alone](http://www.theinquirer.net/?article=28635). Secondly, [here's a possible fix](http://mail.gnome.org/archives/gtk-list/2002-March/msg00370.html), even though I don't really understand it myself.

---

