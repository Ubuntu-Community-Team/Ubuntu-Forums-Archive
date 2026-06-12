---
title: "[INSTALL] - Error APT Config in Ubuntu 7.10"
date: 2007-12-09
forum: Apple PPC Users
---

### Post by smonteru on 2007-12-09
During installation of [http://cdimage.ubuntu.com/ports/releases/gutsy/release/ubuntu-7.10-desktop-powerpc.iso]("http://cdimage.ubuntu.com/ports/releases/gutsy/release/ubuntu-7.10-desktop-powerpc.iso") there is an error during the APT config. A message says that the mirror is incorrect and suggests to change that mirror. I have no choice, i must exit the installation because i can't change the mirror or skip to next stage.

I repeated the installation three times but the problem is the same. The internet connection is ok.

Now i'm downloading the "alternate" version at this url: 

Can you help me? Where is the problem? 

Thank you very much!

---

### Post by mzero on 2007-12-12
same problem here; i tried to install ubuntu 7.10 ppc (20071016) on a iBook g4 a couple of times.
at 82% it says 

The specified Ubuntu archive mirror is either not available, or does not have a valid Release file on it. Please try a different mirror.

there is neither a choice available to select another mirror nor is it possible to cancel the installation, to do that i had to killall ubiquity or someting similar.

i then found this: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095")
but the suggested solution still doesn't work for me :( , no matter what i do the message always shows up.
i eventually gave up trying to install it, i would much appreciate if someone could give me some hints on this

---

### Post by smonteru on 2007-12-13
I've downloaded another ISO and i've installed Ubuntu. 
But i see too difference between Ubuntu for Intel and PPC, like Skype (i can't install on PPC).

PPC is dead for Linux... :(

---

