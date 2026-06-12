---
title: "What on earth does this mean?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Lord Rocket on 2007-08-15
So, I managed to fix my problems with connecting to the internet, apparently by sheer force of will (if anyone else remembers that little debacle from yesterday), and I have started to upgrade my system.

However, after following the instructions on the Wine site, I attempted to download said program and got this from the terminal, after 'sudo apt-get install wine':

[I]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

Er, I don't think so, but its been asking me that a lot. What does it mean and how do I make it go away?

As a secondary question, I had to download *far* too much stuff manually in order to listen to mp3s, largely from the Debian site. How would I go about adding that place to my repositories so Synaptic can download any dependencies automatically?

Thanks in advance.

EDIT: I am using Feisty, 64-bit, if that makes a difference.

---

### Post by sysikon on 2007-08-16
It means that Synaptic is running already. Try to close out of the Synaptic window or end the synaptic process.

---

### Post by Lord Rocket on 2007-08-16
Wow, I am super-smart. 

Thanks - that works, but now its demanding other things of me:

sudo apt-get install wine

[I]...
The following packages have unmet dependencies:
  wine: Depends: lib32asound2 (> 1.0.12) but it is not installable
        Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not installable
        Depends: ia32-libs but it is not installable
        Depends: lib32z1 but it is not installable[/I]

Attempting to apt-get any of these results in the following:

[I]...
Package lib32asound2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lib32asound2 has no installation candidate[/I]

I'm clearly still missing some repositories, or something.

---

### Post by edd07 on 2007-08-16
Yeah, and if the Add/Remove app or the update manager are running, you will get the same error.

---

### Post by Hobo Joe on 2007-08-16
Try 
```

sudo aptitude install wine

```
aptitude handles dependecies better.

If that doesn't help, you could always do this:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by sysikon on 2007-08-16
Try Hobo Joe's method and see what happens...

---

### Post by vexorian on 2007-08-16
> **Lord Rocket said:**
> So, I managed to fix my problems with connecting to the internet, apparently by sheer force of will (if anyone else remembers that little debacle from yesterday), and I have started to upgrade my system.

However, after following the instructions on the Wine site, I attempted to download said program and got this from the terminal, after 'sudo apt-get install wine':

[I]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

Er, I don't think so, but its been asking me that a lot. What does it mean and how do I make it go away?

As a secondary question, I had to download *far* too much stuff manually in order to listen to mp3s, largely from the Debian site. How would I go about adding that place to my repositories so Synaptic can download any dependencies automatically?

Thanks in advance.

EDIT: I am using Feisty, 64-bit, if that makes a difference.
I am not sure why you went directly to the wine site, you were supposed to just install wine from synaptic ...

---

### Post by Lord Rocket on 2007-08-16
Because the Wine site has useful instructions for Ubuntu beginners like m'good self, which can be found at the link Hobo Joe posted above.

'Aptitude' did exactly the same thing as apt-get, except it was kind enough to attempt to resolve the dependencies before it bombed out. I have just downloaded the 64 bit .deb directly from WineHQ, which also informs me Wine has unresolved dependencies. I am going back to the Debian site for a round of manual downloading. Woohoo.

---

### Post by sysikon on 2007-08-16
You can't install because the dependencies you need are only 32-bit.

Search packages.debian.org for lib32asound2.

---

### Post by Lord Rocket on 2007-08-16
Yeah, I did that. 
It informed me it requires libasound2, which went on alright. Attempting to reinstall lib32..., it told me that it requires libc6-i386. Attempting to install *this* revealed it requires libc6, which it turns out I have already installed (2.5 to be precise).

I am therefore giving this up as a bad job. 

Thanks to everyone who tried to help. If anyone knows of any repositories that will allow me to do this automatically, I'd appreciate it if you could direct me to them.

---

