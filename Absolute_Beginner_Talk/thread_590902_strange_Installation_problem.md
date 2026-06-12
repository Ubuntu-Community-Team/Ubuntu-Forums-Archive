---
title: "strange Installation problem"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Mr.Kuchinawa on 2007-10-25
Hi. I use ubuntu daily, and I'm very happy with it. However, I'm having a rather strange problem with installing it on my fujistu siemens lifebook c (pentium 3 machine). When i try to install it from the livecd, it loads and after a minute or two, it shuts down. I've tried the normal install option and the safe graphichs mode. I've tried with kubuntu, freespire and LinuxMint, all with the same result. It runs win2000 good (well, as far as that's possible..)

The machine should be powerful enough. I think the RAM's upgraded to around 300mb.

What should I do? Please notify me if this information is too vauge.

---

### Post by RomeReactor on 2007-10-25
Hi. Have you tried performing the installation using the Alternate CD?

[Ubuntu 7.10 Gutsy direct download]("http://no.releases.ubuntu.com/gutsy/ubuntu-7.10-alternate-i386.iso")

[Ubuntu 7.10 Gusty BitTorrent download]("http://no.releases.ubuntu.com/gutsy/ubuntu-7.10-alternate-i386.iso.torrent")

---

### Post by paul.matthijsse on 2007-10-25
and if the alternate cd isn't a solution, try to boot with the following arguments:
linux irqpoll noapic acpi=off

needed that before to install fedora on a fujitsu siemens laptop. (x)ubuntu installs fine though...

Paul.

---

### Post by Joeb454 on 2007-10-25
Like paul.matthijsee said, Xubuntu will run fine and dandy on that, depends if you want to use Gnome (normal Ubuntu) or KDE (Kubuntu) specifically though.

---

### Post by Mr.Kuchinawa on 2007-10-25
Thanks for good replies. BSD works, so I'm going to try that out on this computer for at least a couple of days. Anyway, can somebody explain to me the main differences between linux and bsd?

I'm running pc-bsd now btw.

Edit: What's so special about the alternative version?

---

### Post by paul.matthijsse on 2007-10-25
> **Mr.Kuchinawa said:**
> Edit: What's so special about the alternative version?Quote from the download site:
"This CD does not include the Live CD, instead it uses a text-based installer."

So instead of running the live cd (often rather slow), it goes straight into install mode.

---

### Post by Mr.Kuchinawa on 2007-10-25
> **paul.matthijsse said:**
> Quote from the download site:
"This CD does not include the Live CD, instead it uses a text-based installer."

So instead of running the live cd (often rather slow), it goes straight into install mode.

Thanks. Does it exist an alternative version for linux mint? Can't seem to find it

---

