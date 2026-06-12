---
title: "powerbook won't boot from DVD anymore"
date: 2006-12-25
forum: Apple PPC Users
---

### Post by wanger123 on 2006-12-25
Hi all, merry Christmas.

I have been running ubuntu ppc version on my 1GHZ powerbook for about 6 months. I decided that I would do a fresh install over Chrissie but I cannot get it to boot from the DVD drive. 

I tried holding C during boot and also shift+option+apple+delete. It tries to boot from dvd but then just boots from hard drive. It is not ubuntu specific because debian ppc won't work either.

I replaced the matshita 8123 with a pioneer dvr-k06 a few months back and I don't think I have ever booted from it.

So I guess my question is, has anyone else replaced their optical drive and then been unable to boot from it? Is it a master/slave thing?

I guess as a last resort I could put the matshita back in until I install ubuntu and replace it afterwards with the pioneer

ps I don't have any apple discs

any ideas?

cheers

wanger

---

### Post by wanger123 on 2006-12-28
Just an update. Replaced dvdrw with original cdrw and it booted first time.

Now I have to figure out how to make the dvdrw bootable

cheers

wanger

---

### Post by didg on 2006-12-28
> Is it a master/slave thing?
Maybe or it  has not the same OF name and cd: alias fails.

---

### Post by wanger123 on 2006-12-29
Another update.
 I followed the instructions from here: [http://xlr8yourmac.com/tips/Pioneer_K04L_master_mod.html](http://xlr8yourmac.com/tips/Pioneer_K04L_master_mod.html)

and soldered a bridge between pins 45 and 47 of the dvd plug and now I can boot up with it. It is also recognised as MASTER in OSX.

cheers

wanger

---

