---
title: "[SOLVED] any help, i like lilo and stich"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by chips24 on 2008-01-15
dvd plugins

---

### Post by SunnyRabbiera on 2008-01-15
okay...
well firstly did you install all the stuff you need for dvd playback like libdvdcss?
also gxine is a little buggy, I would use another app if i were you

---

### Post by chips24 on 2008-01-15
> **SunnyRabbiera said:**
> okay...
well firstly did you install all the stuff you need for dvd playback like libdvdcss?
also gxine is a little buggy, I would use another app if i were you

ok?

---

### Post by Seisen on 2008-01-15
Check this link out: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvds%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvds%29)

---

### Post by SunnyRabbiera on 2008-01-15
okay, well first things first.
to get libdvdcss you need to use more repositories, to get more do the following:
go to system, then to "administration" then to "synaptic package manager"
after you type in your password synaptic will load.
now to get more repositories go to the "settings" menu and then to "repositories"
next you will enable more repositories by clicking off a checkmark next to pretty much every one listed except the last one.
the next tab is where you can get third party repo's, you might as well enable them as well.
after you are done checking off all you need press ok and you are done.
reload your repository using the reload button and search for "libdvdcss"
it should be in the media repos under multiverse.

---

### Post by agentsmith23 on 2008-01-15
First:

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

Second:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


Third:

sudo apt-get install libdvdcss2

or

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb



Step three is one of those two I can't remember which one i had to use. If you are using a different platform than x86 let me know.

---

### Post by hyper_ch on 2008-01-15
actually I don't think that library is in any of the official repositories. It is, however for sure, in the medibuntu repos:  [http://www.medibuntu.org](http://www.medibuntu.org)

Fruthermore it's not just called libdvdcss but libdvdcss**2**

Once you added medibuntu repos I'd recommend to install all of that here:

```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs

```

---

### Post by chips24 on 2008-01-15
> **agentsmith23 said:**
> First:

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

Second:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


Third:

sudo apt-get install libdvdcss2

or

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb



Step three is one of those two I can't remember which one i had to use. If you are using a different platform than x86 let me know.

still dosnt work...

---

### Post by chips24 on 2008-01-15
none of this worked, sorry. still need help.

---

### Post by SunnyRabbiera on 2008-01-15
hmm, looks like apt issues.
if you need something simpler then you cant go wrong with automatix:
[http://www.getautomatix.com/]("http://www.getautomatix.com/")
automatix might make this easier, just keep in mind it can be unstable sometimes

---

### Post by Tatty on 2008-01-15
The problem with the last screenshot is that you have Synaptic open at the same time.

You can only use one package manager at a time, so close synaptic then try again.

---

### Post by chips24 on 2008-01-15
> **Tatty said:**
> The problem with the last screenshot is that you have Synaptic open at the same time.

You can only use one package manager at a time, so close synaptic then try again.

oh thank god!!!!

---

### Post by chips24 on 2008-01-15
thankyou so much, i cant thankyou enogh  ^_^

---

### Post by hyper_ch on 2008-01-15
and Automatix is not recommended for usage.

---

### Post by chips24 on 2008-01-15
well it worked!!!

---

