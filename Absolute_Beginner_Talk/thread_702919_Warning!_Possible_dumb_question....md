---
title: "Warning! Possible dumb question..."
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by TransDeist on 2008-02-20
I am a brand new fan of Ubuntu Linux and have installed successfully.  I love the version, but I am having a problem logging into some websites because of a Java problem.  The distribution seems to have a linux-java module installed, but I can't seem to get around the "missing plug-in" problem.  Any suggestions?

Thanks!

Larry

---

### Post by ispy on 2008-02-20
yeah, you need to enable the repos first.

go to System >> Administration >> Software Sources

enable all but source code for best results.

this allows you to get just about any program.

then, go to
Applications >> Add/Remove >> and search for the Restricted Extras for a couple other necessary things, or just search for Java and get the ones you need.

 i recommend the Restricted Extras, it simpifies things

hope this helps.

---

### Post by oedha on 2008-02-20
or....
open terminal
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras

---

### Post by ispy on 2008-02-20
that works too...

---

### Post by jcitguy78 on 2008-02-20
> **oedha said:**
> or....
open terminal
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras

thanks for the tip i just install it with no probs.

---

