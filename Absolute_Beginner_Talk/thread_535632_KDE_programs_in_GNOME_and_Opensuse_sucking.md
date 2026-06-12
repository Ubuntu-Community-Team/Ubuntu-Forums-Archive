---
title: "KDE programs in GNOME and Opensuse sucking"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Duffasaurus on 2007-08-26
Why do KDE programs work in GNOME? If they work in GNOME, why do they say "For KDE desktop" It's confusing, it should just abe a universal program. Also, how come opensuse completely sucked at using my videocard, and no video drivers were working, but it works magically in Ubuntu. Do you guys have secret driver you don't share with the rest of the linux community? (I have an Intel GMA X3000)

---

### Post by Hobo Joe on 2007-08-26
KDE and GNOME still both run on Ubuntu, they are just separate desktop variations. They differ in looks, default apps, and window manager, but other wise Kubuntu and Ubuntu are the same OS, hence programs working in both. So when you install a KDE program on GNOME, it just installs the dependencies that are normally install on KDE, so that the program can run like it's housed in KDE.

It all depends with the video drivers in Linux, all the distros have different ways of setting them up, and some have completely different drivers.

---

### Post by por100pre1 on 2007-08-26
When you install a program you'll get the dependencies you need. There are already some qt and kde modules installed for the KDE programs you use in GNOME.

---

### Post by Delkster on 2007-08-26
> **Duffasaurus said:**
> Why do KDE programs work in GNOME?
They use different software libraries (toolkits) for drawing the user interfaces and their components, as well as for things like common dialogs such as file opening and saving windows. You can have both libraries, and if you want to run a KDE application in Gnome, it'll just need to have the required KDE libraries available. The package manager (Synaptic, Add/Remove Applications, command-line tools, whatever you use) takes care of installing the required libraries when you install something.

> If they work in GNOME, why do they say "For KDE desktop" It's confusing, it should just abe a universal program.
They work, but they may not always integrate with the other applications on your desktop as well as they would with other KDE applications. Nowadays Gnome and KDE and their respective applications integrate quite nicely with each other -- the notification area icons work across desktop environments, as do most other things. Sometime in the past it wasn't so rosy.

Also, applications using the same libraries (e.g. Gnome libraries and user interface widgets) can share the library code in memory so they needn't be loaded in the memory multiple times. If, on the other hand, you have both Gnome and KDE applications running, you'll obviously have at least portions of both libraries loaded, so it takes more memory. That may or may not be a concern nowadays.

> Also, how come opensuse completely sucked at using my videocard, and no video drivers were working, but it works magically in Ubuntu.

I don't know and don't really have time to find out about your particular graphics card, but I'd suppose there are four possibilities:

1. The better operation requires a proprietary graphics driver, and while the Ubuntu project certainly doesn't write such drivers, they may include third-party proprietary drivers when needed. If you had a proprietary driver, you'd probably know about it. In any case, you can check for such drivers in System > Administration > Restricted Drivers Manager.
2. The driver in Ubuntu is principally the same driver, just a different (newer?) version. This sounds like the most probable cause.
3. The problem in OpenSuse wasn't with the driver but with detecting the device. Different distributions usually have the same drivers but different hardware detection mechanisms.
4. Both distributions have the same driver, but it has been somehow broken in OpenSuse. Distributions often patch parts of the system, notably the kernel which includes most of the low-level device drivers, and although the patches are meant to fix things the custom modification can sometimes also unintentionally break something. It's not unheard of, but doesn't really sounds very likely in this case either.

---

