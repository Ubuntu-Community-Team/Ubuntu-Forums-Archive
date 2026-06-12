---
title: "Feisty Firefox"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-12-13
Is there a way i can safely remove "Feisty Firefox"? I am running Gutsy Gibbon. Thanks all

---

### Post by mp4215 on 2007-12-13
Do you mean the previous relase of Ubuntu "Fiesty Fawn"? Or do you mean you want to remove the internet browser "Mozilla Firefox"?

If you upgraded to Gutsy it means that all of the Fiesty packages were upgraded to Gutsy ones.

---

### Post by oscarthefish on 2007-12-13
I would like if possible to remove Firefox and then start using The Opera browser

---

### Post by eriqjaffe on 2007-12-13
You should be able to remove Firefox and install Opera through Synaptic.

At least, I **think** Opera is in the repo's.

---

### Post by oscarthefish on 2007-12-13
Thanks for the replies folks!

---

### Post by stchman on 2007-12-13
> **oscarthefish said:**
> I would like if possible to remove Firefox and then start using The Opera browser

You can use Opera and leave Firefox on your system.  If you just HAVE to remove Firefox then so this:

```

sudo apt-get -y autoremove firefox
```

Make sure you remove the residual config files in synaptic.

I don't believe that Opera is in the repos, but you can get Opera for [www.opera.com](www.opera.com) as there is an Ubuntu .deb install file.

---

