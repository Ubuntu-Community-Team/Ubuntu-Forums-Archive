---
title: "AC 97 onboard audio"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-13
I have AC '97 onboard audio card, It doesn't work at all and i've been at it for 2 days.....  Doesn't even see that its there i don't think (nor do i know how to check).  I think this because the little speaker has a red circle with a cross through it and clicking it gives me this:
```

No volume control GStreamer plugins and/or devices found.

```i've found a few posts relating to this and nothing worked.... someone please help.  if you need ANY INFORMATION JUST POST! Don't leave me hanging....

---

### Post by njparton on 2008-03-14
"AC '97 onboard audio card" isn't really enough information for anyone to post a useful response other than to ask you to post you're motherboard make/model and if possible the make/model of the sound chip.

Also have you got onboard sound enabled in the BIOS?

---

### Post by StOoZ on 2008-03-14
paste this in the terminal
> lspci -vvv | grep --after-context=7 audio 

and tell us what it shows

---

### Post by The Titan on 2008-03-14
> "AC '97 onboard audio card" isn't really enough information for anyone to post a useful response other than to ask you to post you're motherboard make/model and if possible the make/model of the sound chip.

Also have you got onboard sound enabled in the BIOS?

yes its enabled in the bios.  And this is the make and model of the chip i thought.  My computer is an eMachines t4060.

> 
paste this in the terminal
 	Quote:
 	 	 		 			 				lspci -vvv | grep --after-context=7 audio 			 		 	 	 
and tell us what it shows


that returns nothing.

---

### Post by njparton on 2008-03-14
You need to find out the make and model of your motherboard, "eMachines t4060" isn't any help unless someone here by coincidence has the same computer and knows what it is.

Is it listed on their website?

---

### Post by smurphy_it on 2008-03-14
paste this in the terminal
Quote:
lspci -vvv | grep --after-context=7 audio
and tell us what it shows

that returns nothing.

Probably a typo, make sure the word audio starts with a Capital A.

Like this

lspci -vvv | grep --after-context=7 Audio

BTW... that is 3 v's. after lspci.

---

### Post by StOoZ on 2008-03-14
> **smurphy_it said:**
> paste this in the terminal
Quote:
lspci -vvv | grep --after-context=7 audio
and tell us what it shows

that returns nothing.

Probably a typo, make sure the word audio starts with a Capital A.

Like this

lspci -vvv | grep --after-context=7 Audio

BTW... that is 3 v's. after lspci.

in my system (ubuntu 7.10) its lower case 'a'.
so to cover all the possibilities:
> lspci -vvv | grep --after-context=7 [aA]udio

:guitar:

---

