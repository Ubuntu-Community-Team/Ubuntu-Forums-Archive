---
title: "the proper way to remove a SINGLE font?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Ms Dainty on 2006-08-22
My eyes are red from reading the hundreds of posts on Fonts...but I have yet to find the definitive answer to removing a SINGLE font from Ubuntu safely. (Note I said "single"; therefore removing a package of fonts via Synaptic is not the answer.)

Please tell me how to remove a single font such as Comic Sans from the system. Thanks.

---

### Post by jimmygoon on 2006-08-22
Why do you want to?

Open up a nautilus window... hit Ctrl+L and type "fonts:///" and then find the one you don't want and delete it (you will probably have to reboot to see effects)

---

### Post by Ms Dainty on 2006-08-22
Because it's a pain to sift through a long font list...

Is that really kosher? Threads like [these]("http://ubuntuforums.org/showthread.php?t=203844") and webpages like [this]("http://avi.alkalay.net/linux/docs/font-howto/Font.html") seem to suggest it's not a clean way to do it.

---

### Post by Ms Dainty on 2006-08-23
One last plea for instruction before I start deleting fonts willy-nilly! ;)

---

### Post by wilberfan on 2006-08-25
Ooops.  Never mind.   Hmm... how do I delete this post??

---

### Post by jamesstansell on 2006-08-25
How about leaving the font installed but blacklisting it?

> rejectfont

Fonts matched by an rejectfont element are "blacklisted"; such fonts are excluded from the set of fonts used to resolve list and match requests as if they didn't exist in the system. Rejectfont elements include glob and pattern elements which are used to match fonts. 

Seen at [http://fontconfig.org/fontconfig-user.html](http://fontconfig.org/fontconfig-user.html)

---

### Post by sjoseph on 2007-07-22
I've tried the above technique but it doesn't let me delete a font because I don't have permissions. I am the only user so I don't get this. I'd also like to narrow down my choices.

---

