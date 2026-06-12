---
title: "Conflicting Audio Cards"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by BigMontana on 2008-01-15
My computer has an on board audio card (built into a K8V Deluxe motherboard) and also a SB Audigy ZS.  When I fire up Ubuntu, it's a toss up as to which card it decides to use.  I have since gone in and disabled the on board card in the BIOS (I think), but that hasn't stopped Ubuntu from trying to use it.

Is there anything I can do about this?

---

### Post by Lostincyberspace on 2008-01-15
Try using pulse audio.
[http://www.pulseaudio.org/](http://www.pulseaudio.org/)
It can Merge the multiple sound cards together. there are instructions on the site.

---

### Post by BigMontana on 2008-01-15
Thanks, I'll check that out, but isn't there something I could add to a startup config that says not to use a certain device?

---

### Post by rich257 on 2008-01-26
I guess it depends on why it's a problem if both sound cards are started up.  I had the problem that the order in which the cards were started varied, which meant the I couldn't be certain which sound card would be the default.  You can fix this by controlling the order of the cards, see [this]("http://alsa.opensrc.org/index.php/MultipleCards#Easy_way_to_do_this_on_Ubuntu_Edgy") article.

---

