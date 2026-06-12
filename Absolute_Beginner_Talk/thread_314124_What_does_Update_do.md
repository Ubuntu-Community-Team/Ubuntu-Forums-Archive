---
title: "What does Update do?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2006-12-07
Seems a simple question with an obvious answer but....

Does update scan all of my existing applications and hardware and look for updates for them?

Do my repositories have to be up to date?

I'm having sound problems which I've nailed down to my sound card that Ubuntu dosen't like.  In Windows, I would have popped on to the net and looked for up-to-date soundcard drivers.  Does autoupdate do that job for me, ie find and install any drivers required for my current hardware configuration?

Thanks. :)

---

### Post by Josh1 on 2006-12-07
Well doing an update probably won't fix your sound card issues, have you searched around on the forums & google for *nix drivers yet?

---

### Post by 23meg on 2006-12-07
Given that you keep the default set of repositories, you'll only get security updates for the software that's already installed. It doesn't have anything to do with your hardware configuration.

Have you started a separate thread for your sound problems?

---

### Post by Phosphoric on 2006-12-07
> Given that you keep the default set of repositories, you'll only get security updates for the software that's already installed. It doesn't have anything to do with your hardware configuration.

I take it then that I may not have the best/latest driver for my soundcard?  I have a Santa Cruz Turtle Beach which is seen as a Cirrus Logic chipset.

My sound problems are in [this thread ](http://www.ubuntuforums.org/showthread.php?t=291992)

I've skirted round the problems by installing an old generic Sound Blaster card but I want to run my chosen decent card, so I'll keep trying.
Hence my questions about updating drivers.

Thanks :)

---

### Post by 23meg on 2006-12-07
> I take it then that I may not have the best/latest driver for my soundcard?You have whatever driver is provided in the kernel. In Linux, device drivers exist as part of the kernel and to add a new device driver, you have to insert a kernel module. Stable versions of Ubuntu only get security updates, not feature updates with new versions of software, so even if a new driver is available, you won't see in in the official repositories unless it fixes a security flaw. And kernel security updates are quite uncommon.

---

### Post by Hendrixski on 2006-12-07
That is a really good question actually, I'd like to know.  Specifically how does update do what it does. I assume it's directly connected to apt, and that there's a file of what software I have at which version, and then it apt-get's the patches to upgrade.  If I install packages from apt-repositories other than Ubuntu (like Debian unstable for example) will Ubuntu know to look to them for updates as well?

---

### Post by 23meg on 2006-12-07
The update manager is just an apt frontend that checks for new versions periodically and notifies you of them. > If I install packages from apt-repositories other than Ubuntu (like Debian unstable for example) will Ubuntu know to look to them for updates as well?If any repository in your sources.list provides any newer version of a package that's installed, you'll be notified.

---

