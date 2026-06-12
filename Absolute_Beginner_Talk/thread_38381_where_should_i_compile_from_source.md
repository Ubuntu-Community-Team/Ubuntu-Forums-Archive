---
title: "where should i compile from source?"
date: 2005-05-31
forum: Absolute Beginner Talk
---

### Post by wowbuntu on 2005-05-31
Dear Ubuntulovers

Where should I compile from source?

I've heard I shouldn't do this in any 
directory other than the home. Is this true?

Must I install all source packages in my home partition?

Its not advisable to do any source compiling or make thing in any folder under root (except home), right?

Please advise.

Take care
Wowbuntu

---

### Post by Alexander Kirillov on 2005-05-31
[QUOTE=wowbuntu]Dear Ubuntulovers

Where should I compile from source?

I've heard I shouldn't do this in any 
directory other than the home. Is this true?

Must I install all source packages in my home partition?

Its not advisable to do any source compiling or make thing in any folder under root (except home), right?

Please advise.

Take care
Wowbuntu[/QUOTE]
 For starters, if you are a beginner, it is not really recommended that you compile software form source at all. But if you must: it does not really matter where you are doing it - you can do it in your home directory (this is what most people do); another option is setting up some temporary directory just for this purpose.  However, after building, you will need to install it (usually by typing "make install'); at this moment, the binaries and other files will be copied to appropriate locations  (such as /usr/bin). You will need to be root (or have root privileges, by using sudo) to do that.

---

### Post by jobezone on 2005-05-31
When installing it systemwide, isn't it better for binaries, etc. to go into /usr/local/ ? This way, if in the future one installs a package of this compiled application, it won't overwrite some of it, and leave other things intact, ending up with a mixed application? It's a bit too late, but if I remember correctly, one does:
```

./configure --prefix=/usr/local/

```
to choose to install it in /usr/local when running "make install".

Like I said, it's late, too late to test it. Tomorrow I'll be sure.

---

### Post by poofyhairguy on 2005-05-31
[QUOTE=wowbuntu]
Where should I compile from source?
[/QUOTE]

DO you have to do it? I personally find alienizing rpm files works better than building from source.

---

### Post by bored2k on 2005-05-31
[QUOTE=poofyhairguy]DO you have to do it? I personally find alienizing rpm files works better than building from source.[/QUOTE]
 I second that. My main problem with compiling from source is that it gets me Michael Corleone angry. I hate it their READMEs. They just say  "./configure, make, make install" instead of "./configure, take your loved ones to a safe place, come back, install a gazillion packages, verbally express your love for the twinkies in a way only a Sith Lord would be proud, install some more, run make and pray it works, then hit the final step."

---

