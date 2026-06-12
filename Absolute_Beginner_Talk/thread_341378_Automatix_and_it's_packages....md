---
title: "Automatix and it's packages..."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Fingerz91 on 2007-01-18
Hey All!

I've download most of my Linux programs via Synaptic and Automatix, but I just have one question.... does Automatix update it's packges (eg songbird) so when the first 1.0 release comes out, I can install it from there?

---

### Post by davebgimp on 2007-01-18
Automatix itself is often updated, so as long as it's in your sources list that's taken care of. In many cases, Automatix installsfrom the Ubuntu repositories, just automating the task for you. Other repos i would assume are managed with Automatix updates.

---

### Post by cstudent on 2007-01-18
Not necessarily. Automatix uses apt-get to install a lot of the packages from the Ubuntu repos. However, it does use wget to download some packages to install. It does this with Frostwire, for example. If Frostwire were to update their .deb, you would not automatically get an update for it. The Automatix people would probably update their software to install the new Frostwire version, but you would have to run Automatix and tell it to reinstall Frostwire.

---

### Post by davebgimp on 2007-01-18
> **cstudent said:**
> Not necessarily. Automatix uses apt-get to install a lot of the packages from the Ubuntu repos. However, it does use wget to download some packages to install. It does this with Frostwire, for example. If Frostwire were to update their .deb, you would not automatically get an update for it. The Automatix people would probably update their software to install the new Frostwire version, but you would have to run Automatix and tell it to reinstall Frostwire.

Thanks for clarifying.

---

### Post by Fingerz91 on 2007-01-24
Sorry.

What I meant to ask was, do the packages installed via Automatix get updated? For example, when the next Flash Plugin comes out, will Synaptic see that I have it installed and update it to the new one, or will I have to uninstall and reinstall via Automatix?

---

### Post by cstudent on 2007-01-24
> **Fingerz91 said:**
> Sorry.

What I meant to ask was, do the packages installed via Automatix get updated? For example, when the next Flash Plugin comes out, will Synaptic see that I have it installed and update it to the new one, or will I have to uninstall and reinstall via Automatix?

Again, it's dependent on how Automatix installed the software. Anything it installed using apt-get from the Ubuntu repositories will get updated through Synaptic. Anything else installed via wget will not. I haven't used Automatix for awhile now, so I'm not sure how it installed flashplayer. I would go to the Automatix website and post your question on their forum. They can certainly tell you which packages would not update automatically.

---

