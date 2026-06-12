---
title: "[SOLVED] Add/Remove won't add anything"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Moonwings on 2008-01-16
Everything I attempt to add that is listed in the Add/Remove window (which I got to from the Applications menu) says:
"xyz cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

That includes Liferea which was specifically recommended in the Ubuntu official Training manual which I'm working my way through.
I also tried at least 20 other things and every one of them says the same thing.

Perhaps related (or not), when I went to a web site in Firefox which required a flash player plugin to run, FF told me I needed another plugin. So I clicked to add a plugin. It gave me 2 choices. One was Adobe Flash Player (installer). I tried that one and it said "cannot find flash-plugin nonfree".  So then I tried the other option that said "Gnash SWF player" and then got the error: "cannot find mozilla-plugin-gnash"

So, I'm batting zero when it comes to installing anything.
Suggestions anyone?

I am running Ubuntu 7.10 on a Gateway AMD64 laptop.

---

### Post by Sef on 2008-01-16
Make sure that the top right box in Add/Remove is set to 'All Available Applications'.    Try that and post if you still have problems or not.

---

### Post by SunnyRabbiera on 2008-01-16
maybe a more advanced package manager would suit you, try synaptic

---

### Post by Moonwings on 2008-01-17
I did open the synaptic package manager and did a search for Liferea.
It didn't find anything.
I suspect I have something screwy in my setup somewhere. Maybe it isn't looking in the right places for the software?
I'm pretty sure I was set up to look at all applications.
Is there a reason why Liferea would be incompatible with Ubuntu 7.10?   I figured it should work since the wiki training manual said to install it.

Thanks

---

### Post by mcduck on 2008-01-17
First, make sure you got all the repositories enabled (in System/Administration/Software Sources).

Are you running 64-bit or 32-bit version of Ubuntu? Some packages might no be available for 64-bit version.

Alsi, try running 'sudo apt-get update', and if you get any errors post the whole output here. You could also post your repository list here so we can check that it's OK. Just run 'cat /etc/apt/sources.list' and post the output here.

---

### Post by Moonwings on 2008-01-17
Thanks mcduck!  That was it!
When I opened the Software Sources window I discovered that none of the items on the Ubuntu Software tab were checked!  So I checked all but source code (and followed the suggestions that I also stumbled across in):
[http://ubuntuforums.org/showthread.php?t=618985]("http://ubuntuforums.org/showthread.php?t=618985")

and that solved the problem!!!

Many thanks for taking the time to help a newbie :)

---

