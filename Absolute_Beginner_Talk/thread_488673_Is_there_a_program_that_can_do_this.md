---
title: "Is there a program that can do this?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Puppy fam on 2007-06-30
As you already know, if a program is not in synaptic, you have to go off into the internet and try and find a .deb of the program. If you can't a .deb then there is a big process you have to do with another file type, which I don't really understand how to do (I have to refer to the: "how to install anything in Ubuntu" page). So is there a program that would take another file type, and make it into a .deb or another file type? I think that this is impossible, but I just wanted to make sure.

Thanks,
-Puppy fam

---

### Post by chamberlain2006 on 2007-06-30
Well, yes and no.  There *is* a program called checkinstall, but that just takes the last command and changes it.  There's no real gain.  You can also create a proper .deb file, but that is also difficult.  Really, usually there's only 3 or 4 commands needed to install a .tar.gz or .tar.bz2.  (Which I assume is what you are talking about).  Anyway, if you need help installing your problem I would be happy to help.

---

### Post by Malibu Illusion on 2007-06-30
You're talking about tarballs (.tar.gz) and compiling from source.  The process isn't long or overly complicated, you just have to type:

```
./configure
make
sudo make install
```

Into the CLI in most cases, and may have to manually resolve some depandancies.

---

### Post by r4ik on 2007-06-30
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Same thing other words some time's helps,

If not just ignore,

Good luck !

---

### Post by Puppy fam on 2007-06-30
ok thanks!

---

