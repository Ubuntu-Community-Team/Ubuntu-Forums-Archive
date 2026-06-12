---
title: "Sound Juicer Still Won't Show Lame Encoder"
date: 2005-08-01
forum: Apple PPC Users
---

### Post by ubonetu on 2005-08-01
Hi,

I followed the wiki manual on this but I'm afraid, as it warns, I ran sound juicer before installing and configuring lame.  See:

[https://wiki.ubuntu.com/CDRipping](https://wiki.ubuntu.com/CDRipping)

Anyone know if there's a config file I can delete or something to reset sound juicer (I already deinstalled and reinstalled it).

Thanks,
ubonetu

---

### Post by rachii on 2005-08-01
is there a .soundjuicer folder in your home directory (turn on view hidden files) should be a config file in there

---

### Post by ubonetu on 2005-08-01
Good thought.  I did a find / -name *sound-juicer* and came up with:

~/.gconf/apps/sound-juicer/%gconf.xml

but the file doesn't have a section for encoder formats or do anything when I mv it.

Thoughts?

Thanks

---

### Post by ubonetu on 2005-08-02
](*,)   Okay, now I've tried everything, even as far as reinstalling ubuntu.  Still no dice.  Anybody had similar problems?

Thank you  :smile:

---

### Post by ubonetu on 2005-08-02
:-# Okay, I found some other sources of information that helped me.  I've got it working now.

Thanks ;-)

---

### Post by halogentan on 2008-05-17
> **ubonetu said:**
> :-# Okay, I found some other sources of information that helped me.  I've got it working now.

Thanks ;-)

Could you tell us how you fixed it?  I'm having the same problem.  :(

---

