---
title: "Wine Internet Explorer problem"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Ryupower on 2006-10-28
Hi guys!
I have a problem with running internet explorer in Wine. - all I get is a blank window!

OK,
-I installed wine
-I installed IE ( with ies4linux )

When running it showed me a blank window, and it wanted to install gecko on my ubuntu

- I downloaded and installed gecko.

So, then I try to wine it again. But it STILL gives me a blank window!

Anyone know what's up with that?

---

### Post by land0 on 2006-10-28
I have always had issues in the end with installing IE(any version) using just the IE setup.exe file. After much digging I stumbled across this gem [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page) this works every time for me. It installs many of the dependencies IE needs to work correctly. I hope this helps.

---

### Post by Ryupower on 2006-10-28
That's what I used....but it still gives me the blank screen! :(

( *edited first post* )

---

### Post by Ryupower on 2006-10-29
Bump.
I looked up info on this and it didn't help me much, spaces, for instance, aren't my problem...

---

### Post by Kalinda on 2006-10-29
Hmm.. I think it's because Internet Explorer is broken on newer versions of wine... except with the IE for Linux thing.. IE6 works great using Wine 0.9.8, but we have the newest version in the repo (and adept updater won't stop pestering me to update wine ](*,) )

I need to use IE to watch streaming media in the WMP plugin, which doesn't seem to work in the IE4Linux thing.. so has anybody gotten it to work in the newest Wine version?

---

### Post by land0 on 2006-10-29
I installed the channel(repository) provided by winehq which is. 
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
So the version number of wine I am using is 0.9.23~winehq0~ubuntu~6.06-1 (dapper).

Then installed IE using IE4linux.  

I hope this helps

---

### Post by Ryupower on 2006-10-29
thanks, I'll try that version of wine

---

