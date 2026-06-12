---
title: "[SOLVED] Gnomad2 won't start after upgrade to Gutsy"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by orbital on 2007-10-26
Gnomad2 was working fine before the upgrade, but now I only get the following error:

```
gnomad2: error while loading shared libraries: libmtp.so.5: cannot open shared object file: No such file or directory

```

I've tried uninstalling and reinstalling it with no success. Any ideas?

---

### Post by orbital on 2007-10-28
Bump.

---

### Post by MegaJim on 2007-10-28
You need to make sure you have the libmtp package installed.

```
sudo apt-get install libmtp6
```

alternatively, you could try neutrino, a similar application that doesnt require that package

```
sudo apt-get install neutrino
```

---

### Post by orbital on 2007-10-28
```
sudo apt-get install libmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmtp

```

What to do now?

---

### Post by MegaJim on 2007-10-28
Oops, sorry there was a typo in that code.

The package you need is called libmtp6, try installing that

---

### Post by orbital on 2007-10-28
> **MegaJim said:**
> Oops, sorry there was a typo in that code.

The package you need is called libmtp6, try installing that

```
libmtp6 is already the newest version.

```

So it's installed. Any ideas?

---

### Post by MegaJim on 2007-10-28
You could try reinstalling libmtp6.

You could also try removing/renaming the gnomad2 config file, or you could try out neutrino in the mean time

---

### Post by orbital on 2007-10-28
> **MegaJim said:**
> You could try reinstalling libmtp6.

You could also try removing/renaming the gnomad2 config file, or you could try out neutrino in the mean time

I tried re-installing libmtp6, but it didn't have any effect. I also tried Neutrino, but I couldn't get it to connect to my Creative Zen. I also removed the config file, no effect.

Please any more ideas?

---

### Post by MegaJim on 2007-10-28
Neutrino is really old, I don't think its able to communicate with the zen.

---

### Post by orbital on 2007-10-28
Bump, still need help...

---

### Post by orbital on 2007-10-31
Help please?

---

### Post by xc3RnbFO8P on 2007-10-31
Have you tried to install 

libmtp5  and  libmtp-dev in Synaptic Package Manager ?

---

### Post by orbital on 2007-10-31
> **Ringi said:**
> Have you tried to install 

libmtp5  and  libmtp-dev in Synaptic Package Manager ?

I installed libmtp-dev, and it didn't help.

When i try to install libmtp5 with Synaptic I get the following:

```
libmtp5:

Package libmtp5 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```

Is there a way to install this package some other way?

---

### Post by xc3RnbFO8P on 2007-10-31
[http://ftp-master.debian.org/~ajt/new/libmtp_0.2.3-1_i386.html]("http://ftp-master.debian.org/~ajt/new/libmtp_0.2.3-1_i386.html")

[http://people.debian.org/~rafael/libmtp/]("http://people.debian.org/~rafael/libmtp/")

[http://gnomad2.sourceforge.net/]("http://gnomad2.sourceforge.net/")

Have seen this?

---

### Post by zzztownsend on 2007-10-31
I found that after ugrading to gusty the new version of rhythmbox can PLAY from my creative zen touch (but not write/transfer to). Because of this gusty by default has Rhythmbox down as the default application for a removable media player. So when I started Gnomad2, rhythmbox had already connected to the zen. This (presumably) caused some kind of clash and Gnomad2 wouldn't work.

I fixed the problem by changing the default application for media players under 'Removable Devices and Media' in the Preferences (Admin??? - sorry I'm at work at the moment on an XP box!!) Menu to Gnomad2

Hope this helps. I have generally found that the libmtp6 with gutsy has been much more reliable than libmtp5 with feisty. Well done to those clever chaps.

Cheers
Matt

---

### Post by orbital on 2007-10-31
I installed Gnomad2 from source and it works.

---

### Post by xc3RnbFO8P on 2007-10-31
> **orbital said:**
> I installed Gnomad2 from source and it works.

When you installed from source, was there something missing or you need to add.

---

