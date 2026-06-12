---
title: "Aw geez, old iBook having a fit with date &amp; time on 7.10"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by lordfly on 2008-04-25
Disclaimer: Newbie Ubuntu user, been trying to install ubuntu on fiance's old and broken iBook for a few weeks now. Started with 7.10 alternate ppc install. Installed, but hangs.

So, I'm still on 7.10, so I don't know if Hardy will fix this issue (I doubt it, but it's downloading now).

Ubuntu throws a fit when the iBook's clock is broken.

Easy enough, right? Just fix the clock!

Well, doing the old "sudo date" etc stuff doesn't work. It doesn't stick.

This version of the iBook (g3, Dual USB) does not have a battery on the CMOS. Instead it has some weird circuitry I had to reset. Well, according to the machine, it's reset, but you can't really tell because it thinks it's Dec 31, 1903.

Doing the trick described at

[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

Does nothing. It doesn't stick on reboot.

Anyone have any tips? Does Hardy fix this problem with it hanging on wrong dates?

---

### Post by piano08man on 2008-04-25
Are you using Mac OS as well?  Is the clock right there?

Speaking from my mac tech experience, I know that it can sometimes take a week of use or so before the ibook will actually have enough juice in its capacitor to keep the date and time correct.  It's usually an issue if the machine hasn't been used in a while.  There is not a PRAM battery in an iBook but somehow it stores the information within a small capacitor of sorts.  Hope that helps.

---

### Post by stream303 on 2008-04-25
> **lordfly said:**
> This version of the iBook (g3, Dual USB) does not have a battery on the CMOS.

Was it this document from Apple about resetting the PMU - I see it covers a lot of ibook models and found the docs for your specific ibook:

[http://docs.info.apple.com/article.html?artnum=14449](http://docs.info.apple.com/article.html?artnum=14449)

maybe try again?

---

### Post by lordfly on 2008-04-25
> **piano08man said:**
> Are you using Mac OS as well?  Is the clock right there?

Speaking from my mac tech experience, I know that it can sometimes take a week of use or so before the ibook will actually have enough juice in its capacitor to keep the date and time correct.  It's usually an issue if the machine hasn't been used in a while.  There is not a PRAM battery in an iBook but somehow it stores the information within a small capacitor of sorts.  Hope that helps.

From my limited understanding of Macs, this one came with OS 9, and had a (very broken) install of Tiger - the fiance ravaged the OS when she was transferring her files, so much so that entire sections of the OS were missing. It was a miracle it booted. The clock was wrong there, as well, but the OS is long gone in lieu of my botched ubuntu experiment.

I just finished installing Hardy, but now it boots and gives me a black screen.

---

### Post by VCF on 2008-04-25
> **lordfly said:**
> From my limited understanding of Macs, this one came with OS 9, and had a (very broken) install of Tiger - the fiance ravaged the OS when she was transferring her files, so much so that entire sections of the OS were missing. It was a miracle it booted. The clock was wrong there, as well, but the OS is long gone in lieu of my botched ubuntu experiment.

I just finished installing Hardy, but now it boots and gives me a black screen.

Before it starts booting at the yaboot screen hit tab and then type: Linux nosplash video=ofonly

I'm running Hardy right not on an iBook G3 900mhz and it works really well (but I did install from a alpha release, things may have broken on the live CD since then):(

---

