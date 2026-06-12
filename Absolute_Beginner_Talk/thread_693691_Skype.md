---
title: "Skype?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by baztard on 2008-02-11
Hi all,

This problem is not so much of skype, but i've noticed it whilst installing skype...

I've downloaded skype-debian_1.4.0.118-1_i386.deb and tried to run it with debian-view, but it keeps saying that "another update service is on and you can't continue until its off", even though I have switched off all the possible apps that could disturb this process.

Can I install it manually or any other way than with debian-view?

P.S. Has anyone already tried the beta skype version with video calls? How was it?

---

### Post by hyper_ch on 2008-02-11
I'd recommend to install skype from the medibuntu repos.

---

### Post by jaytek13 on 2008-02-11
There could be a stray process. If you type "top" at the command line it will bring up a list of current running processes. You would look for anything that says "update manager" or "synaptic" and see if you spot something. If so, you can press 'k' and then enter in the PID (process ID) # and it should kill it stray process.

---

### Post by baztard on 2008-02-11
Sorry, but I am highly iliterate at ubuntu and medibuntu repos sounds like wind in the air for me, could you plz explain?

Cheers.

---

### Post by baztard on 2008-02-11
jaytek, i've mentioned that i already have tried this option without satisfactory result.

thnx anyway.

---

### Post by billgoldberg on 2008-02-11
install medibuntu repo:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

then

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then press this:

[apt://skype-static]("apt://skype-static")

---

### Post by sfd609 on 2008-02-11
Hi, I'm following the same steps but I get a firefox error message when I press apt://skype-static.  Any ideas?

---

### Post by billgoldberg on 2008-02-11
It works in epiphany, but you can now just install it using synaptic (system -> administration -> synaptic package manager)

or by doing this:

sudo apt-get install skype

---

### Post by hyper_ch on 2008-02-11
> **billgoldberg said:**
> It works in epiphany, but you can now just install it using synaptic (system -> administration -> synaptic package manager)

or by doing this:

sudo apt-get install skype

but first:

```

sudo apt-get update

```

---

### Post by billgoldberg on 2008-02-11
the update was in the second code

---

### Post by aktiwers on 2008-02-11
[apt:skype](apt:skype)

---

### Post by mikewhatever on 2008-02-11
> **baztard said:**
> Hi all,

This problem is not so much of skype, but i've noticed it whilst installing skype...

I've downloaded skype-debian_1.4.0.118-1_i386.deb and tried to run it with debian-view, but it keeps saying that "another update service is on and you can't continue until its off", even though I have switched off all the possible apps that could disturb this process.

Can I install it manually or any other way than with debian-view?

P.S. Has anyone already tried the beta skype version with video calls? How was it?

What's wrong with Skype for Ubuntu? There is a version for Feisty Fawn which installs and works great.
There are several threads about Skype beta here. I've not tried it,so can't recommend.
[http://ubuntuforums.org/showthread.php?t=606217&highlight=skype](http://ubuntuforums.org/showthread.php?t=606217&highlight=skype)
[http://ubuntuforums.org/showthread.php?t=689936&highlight=skype](http://ubuntuforums.org/showthread.php?t=689936&highlight=skype)

---

### Post by ferdostar on 2008-02-11
Skype beta works great for me on macbook second generation and Ubuntu Gutsy, I had to install the iSight and the mic, so I recommend it!

---

