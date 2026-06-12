---
title: "Firefox Installation Directory"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by MarkoGT3 on 2008-04-14
Hmm, after searching the forums I could not get a decent answer, so here goes:

I've just installed java and am configuring it for Firefox using step by step instructions from java's website.

My instructions are:
1. Go to the plugins sub-directory under the Firefox installation directory
cd <Firefox installation directory>/plugins

I can't find my Firefox installation directory. I have tried:

/usr/lib/mozilla-firefox/plugins
and
/home/usr/.mozilla/firefox/plugins

...but neither work. 

Stupid question, but how much of that am I supposed to replace? I know I replace "usr" with my user name, but am I supposed to replace "lib" with something? This may be my mistake.

Anyway thx in advance!

---

### Post by PeterJS on 2008-04-14
That's the hard way. Why not just install the [sun-java6-plugin](apt://sun-java6-plugin) package and let the package system do all the heavy lifting for you?

---

### Post by stchman on 2008-04-14
I agree with poster #2 install the plugin and Java applets work like a charm.

BTW, the Firefox program is located in /usr/lib/firefox/

Your setting for each profile are in ~/.mozilla/firefox/

That is all.

---

### Post by MarkoGT3 on 2008-04-14
You guys make me feel really stupid.

Lol, but really, thanks! That took like 5 seconds and works FLAWLESSLY.

Now I don't have to load vista for my java apps! I'm FREEEEEE!!!!!! :guitar:

---

### Post by stchman on 2008-04-14
> **MarkoGT3 said:**
> You guys make me feel really stupid.

Lol, but really, thanks! That took like 5 seconds and works FLAWLESSLY.

Now I don't have to load vista for my java apps! I'm FREEEEEE!!!!!! :guitar:

I have been Windows free (besides DX9/10 gaming) for over a year now and loving it.

---

