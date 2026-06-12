---
title: "Pidgin 2.2.2 Released!"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-25
Here the changelog:

    * General changes
          o Various bug and memory leak fixes 
    * Windows-specific changes
          o Updated gtkspell to include a patch to share Aspell dictionaries among all the input fields to avoid excessive memory usage.
          o Updated libxml2 to 2.6.30
          o Bonjour protocol now appears even if Bonjour for Windows isn't present (displays message indicating Bonjour for Windows must be installed if you try to log in and it isn't installed).
          o libpurple now looks for a default prefs.xml in the CSIDL_COMMON_APPDATA directory (e.g. \Documents and Settings\All Users\Application Data\purple\prefs.xml) similarly to how this is done on other platforms. 


As always:
Download the source code:
then:

> ./configure
make
sudo make install


Have fun!

---

### Post by d-_-b on 2007-10-25
how do u download the source code?

---

### Post by Maestro23 on 2007-10-25
> **d-_-b said:**
> how do u download the source code?

Website: [http://www.pidgin.im/download/](http://www.pidgin.im/download/)

Installing Software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Kosimo on 2007-10-25
I couldn't get it working.
Somebody did it?

---

### Post by myoungf1 on 2007-10-25
I was able to download the source and install it with no problem.  Make sure to uninstall 2.2.1 first before doing the install of 2.2.2.  On a side note I now can get into the yahoo chat rooms as I did in Feisty.  For some reason the upgrade to gutsy broke the fixes that were put in place to enable yahoo chat and the security features that yahoo put in.

---

### Post by Maestro23 on 2007-10-25
> **myoungf1 said:**
> I was able to download the source and install it with no problem.  Make sure to uninstall 2.2.1 first before doing the install of 2.2.2.  On a side note I now can get into the yahoo chat rooms as I did in Feisty.  For some reason the upgrade to gutsy broke the fixes that were put in place to enable yahoo chat and the security features that yahoo put in.

Yeah, works for me also.  Good deal man. Thanks to the OP for the heads-up.:guitar:

---

### Post by bardic on 2007-10-25
bardic@bardic:~/pidgin-2.2.2$ make
make: *** No targets specified and no makefile found.  Stop

could someone else me what I'm doing wrong? I did ./configure and then I type in make and I get that reply...

---

### Post by ridetheteapot on 2007-10-25
does anyone know how to get this to compile with network manager? i have all the nm related libs but this no network manager support.... no pot of gold either ;)

---

### Post by philinux on 2007-10-25
When it's got webcam support I might be interested :rolleyes:

---

### Post by syxbit on 2007-10-25
firstly, you don't need to uninstall pidgin 2.21.
secondly, to make sure you can compile, it's best to get the dependencies by typing this
'sudo apt-get build-dep pidgin'

---

### Post by Kosimo on 2007-10-25
> **syxbit said:**
> firstly, you don't need to uninstall pidgin 2.21.
secondly, to make sure you can compile, it's best to get the dependencies by typing this
'sudo apt-get build-dep pidgin'

That's what I was looking for. Something where missing. Gonna try it again

---

### Post by Old Pink on 2007-10-26
Guys, this may hit the repositories, there's no real reason to upgrade via. compiling. 

Think about it, they do small Firefox upgrades in the repositories, like 2.0.0.6 to 2.0.0.8, there's no reason why they shouldn't do Pidgin 2.2.1 to 2.2.2 especially when it's just a bug fix.

[http://ubuntuforums.org/showthread.php?p=3638060#post3638060](http://ubuntuforums.org/showthread.php?p=3638060#post3638060)

---

### Post by syxbit on 2007-10-26
they don't really do bug fixing, they do security fixes.
quite different.
i don't think we'll see it.
it's not like it's hard to compile anyway

---

### Post by bb10 on 2007-10-26
> **syxbit said:**
> they don't really do bug fixing, they do security fixes.
quite different.
i don't think we'll see it.
it's not like it's hard to compile anyway

In fact, it IS a security fix.

[quote=pidgin.im]2.2.2 is here. We fixed another remote crash that affects versions 2.1.0 through 2.2.1 of Pidgin, so you should upgrade right away. See our security advisory for details.[/quote]

:)

---

### Post by syxbit on 2007-10-27
nice catch. i swear that wasn't there the day 2.2.2 came out..
well, i guess they might do it (i still kinda doubt it.)
as far as i can remember, the only outside app to get updated was firefox (and thunderbird)
still, just update it yourself. no point in waiting

---

### Post by kostkon on 2007-10-27
Even if it does not appear as a security update you can get it from [*getdeb.net*]("http://www.getdeb.net/").

---

### Post by Mrs Twaddle on 2007-10-27
it's not in get deb

---

### Post by kostkon on 2007-10-27
> **Mrs Twaddle said:**
> it's not in get deb

It is for Gutsy.

---

### Post by genbuntu on 2007-10-27
so shall I or shall I not uninstall the previous version ? Will it save the previous settings for e.g. I've setup different statuses for different accounts ...

---

### Post by myoungf1 on 2007-10-27
> **genbuntu said:**
> so shall I or shall I not uninstall the previous version ? Will it save the previous settings for e.g. I've setup different statuses for different accounts ...

Yes it will save your previous settings either from installing from source, getdeb, or the repositories.  I have installed twice now, from source, on top of old versions and all my settings where present after the new install.

---

### Post by syxbit on 2007-10-27
if you're worried about settings, just backup ~/.purple

---

### Post by Mrs Twaddle on 2007-10-27
> **kostkon said:**
> It is for Gutsy.

i can't find it, the only thing i can find related to pidgin for gutsy is the music tracker..
I think i need to go back to bed :confused:

---

### Post by kostkon on 2007-10-27
> **Mrs Twaddle said:**
> i can't find it, the only thing i can find related to pidgin for gutsy is the music tracker..
I think i need to go back to bed :confused:

What the hell?! Where did it go?! You are right; now, I cannot find it either!

---

### Post by creativex7 on 2007-11-01
This pidgin is a peace of ****. They promised msnp14 into the 2.2.2 (personal messages, now playing opt-s) and i've compiled and just could say **** you pidgin... sry...

---

### Post by Grafen on 2007-11-01
How can I compile Pidgin with d-bus support? :confused:

---

