---
title: "Safe to add Source to Synaptic?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-01-19
Hi there.

I feel a bit awkward about this post because it feels a bit like telling tales, but Id rather be safe than sorry so here goes:

I have been trying to get into using Gambas as a development language, and it turns out that the Synaptic version is rather older than the latest final version. While asking about this on a Gambas development forum I received this bit of advice, and Id like to run it past you to check that it is actually safe! (*I told you it felt like telling tales!*)

It turns out that the latest version comes as a download that needs to be compiled etc, so I asked if there was anywhere I could get the release as a .deb file. I got this response:

Post ref: [http://forum.stormweb.no/index.php/topic,370.0.html]("http://forum.stormweb.no/index.php/topic,370.0.html")
> 
Add this to your apt source.list
deb [http://xoomer.alice.it/pixel](http://xoomer.alice.it/pixel) gutsy gambas
the do
sudo apt-get update
sudo apt-get install gambas2

It should work.

I hope no-one thinks its rude to ask about this advice in this way, but I'm still pretty new to Ubuntu, and I don't want to trash my system or allow myself to be hacked in some way juts because I didn't ask a question!

Thanks

Max

---

### Post by Nolander on 2008-01-19
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list
```
then add:
> deb [http://xoomer.alice.it/pixel](http://xoomer.alice.it/pixel) gutsy gambas
to the bottom of ur list and run
```
apt-get update
apt-get install gambas2
```

-nolander

---

### Post by meindian523 on 2008-01-19
1]Depends on whether you trust xoomer.alice enough to install packages from them.
2]If you trust them enough,it's ok but you should also ask for the repo signing keys so that you ensure that any packages you take from them are not modified "in transit"

---

### Post by viciouslime on 2008-01-19
Adding a source to synaptic is indeed a way to potentially break your system. Basically, by doing it, whoever owns that repository could create malicious packages and your system will download and install them for you automatically...

If you're really serious then about security, you should NEVER add a third party repository. However, in reality, most people in the world are not malicious and third party repositories are fine. It's much like downloading ANYTHING for windows, any program you download and install on windows could contain malware/viruses/malicious scripts, etc. In ubuntu, so long as you stick to using only the default repos, this will never be the case, however when you start using third-party repos, you basically lower the level of security to something like that of windows. As far as installing program is  concerned anyway.

I have never used the particular repo that you have mentioned, however, it looks like it'll be safe and so long as you've backed up everything in your home directory, reinstalling ubuntu, if it were to trash your system, is so easy it's got to be worth trying...

---

### Post by meindian523 on 2008-01-19
> **Nolander said:**
> ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list
```
then add:

to the bottom of ur list and run
```
apt-get update
apt-get install gambas2
```

-nolander

OP is asking whether it's safe to add the repo,not how to add it!

---

### Post by MaxVK on 2008-01-19
Thanks guys. I know it a security risk to do these things, but with Synaptic running a little behind the latest releases of some things... well, you know what I mean.

Yes, I have backups of everything anyway, but I just wanted to get an idea about this sort of thing. Its not likely to become a habit in any case, but when it comes to development environments, having the latest stable release it something I like to keep up with.

Thanks all.

---

### Post by MaxVK on 2008-01-19
> **meindian523 said:**
> .... you should also ask for the repo signing keys so that you ensure that any packages you take from them are not modified "in transit"....

Repo signing keys. Right. And what would I do with them once I got them? (And for that matter what *are* they?)

---

### Post by Lord Illidan on 2008-01-19
To be as safe as houses, might as well get the sources from Gamba's website and compile them yourself.

---

### Post by MaxVK on 2008-01-19
Yes, thats the whole point. Iv had a few nasty experiences trying to compile things myself (Iv not actually succeeded once!), so I asked if there were any already that were already compiled.

---

### Post by meindian523 on 2008-01-20
> **MaxVK said:**
> Repo signing keys. Right. And what would I do with them once I got them? (And for that matter what *are* they?)

Those are .asc keys which are available with most repos and you add them as trusted keys to your Synaptic,once you download them through Synaptic,Synaptic automatically checks whether the packages have been modified before installation.
About what are those keys:
[http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)

A repo signing key is a private key owned by the repo owner as detailed in the link above which is used to sign each and every package in the repo.If the packages you download are modified in transit,the signing no longer remains valid and is broken and Synaptic doesn't install those packages preventing infection by malware.

---

### Post by Paulmd on 2008-01-20
> **MaxVK said:**
> Thanks guys. I know it a security risk to do these things, but with Synaptic running a little behind the latest releases of some things... well, you know what I mean.

Yes, I have backups of everything anyway, but I just wanted to get an idea about this sort of thing. Its not likely to become a habit in any case, but when it comes to development environments, having the latest stable release it something I like to keep up with.

Thanks all.

It's not synaptic that's behind, it's the default repositories(read Ubuntu Development team, if you're so inclined). Synaptic after all only downloads what's available from the repositories mentioned in the sources.list file.

---

### Post by MaxVK on 2008-01-20
Thanks meindian523. Ill chase those up and check them out.

---

